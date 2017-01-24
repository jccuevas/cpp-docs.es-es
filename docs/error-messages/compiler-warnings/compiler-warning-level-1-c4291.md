---
title: "Advertencia del compilador (nivel 1) C4291 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4291"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4291"
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4291
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'declaración' : no se ha encontrado un operador delete que coincida; no se liberará memoria si la inicialización produce una excepción  
  
 Se utiliza un operador [new](../../cpp/new-operator-cpp.md) de colocación para el cual no hay otro operador de colocación [delete](../../cpp/delete-operator-cpp.md).  
  
 Cuando se asigna memoria para un objeto con el operador **new**, se llama al constructor del objeto.  Si el constructor produce una excepción, debe desasignarse toda la memoria asignada al objeto.  Esto no es posible a menos que exista una función **delete** de operador que se corresponda con el operador **new**.  
  
 Si se utiliza el operador **new** sin argumentos adicionales y se compila con la opción [\/GX](../../build/reference/gx-enable-exception-handling.md), [\/EHs](../../build/reference/eh-exception-handling-model.md), o las opciones \/EHa para habilitar el control de excepciones, el compilador generará código para llamar al operador **delete** si el constructor produce una excepción.  
  
 Si se utiliza la forma de colocación del operador **new** \(aquella que, además del tamaño de asignación, utiliza otros argumentos\) y el constructor del objeto produce una excepción, el compilador continuará generando código para llamar al operador **delete**; pero sólo lo hará si existe una versión de colocación del operador **delete** que se corresponda con la versión de colocación del operador **new** que asignó la memoria.  Por ejemplo:  
  
```  
// C4291.cpp  
// compile with: /EHsc /W1  
#include <malloc.h>  
  
class CList  
{  
public:  
   CList(int)  
   {  
      throw "Fail!";  
   }  
};  
  
void* operator new(size_t size, char* pszFilename, int nLine)  
{  
   return malloc(size);  
}  
  
int main(void)  
{  
   try  
   {  
      // This will call ::operator new(unsigned int) to allocate heap  
      // memory. Heap memory pointed to by pList1 will automatically be  
      // deallocated by a call to ::operator delete(void*) when  
      // CList::CList(int) throws an exception.  
      CList* pList1 = new CList(10);  
   }  
   catch (...)  
   {  
   }  
  
   try  
   {  
      // This will call the overloaded ::operator new(size_t, char*, int)  
      // to allocate heap memory. When CList::CList(int) throws an  
      // exception, ::operator delete(void*, char*, int) should be called  
      // to deallocate the memory pointed to by pList2. Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291  
   }  
   catch (...)  
   {  
   }  
}  
```  
  
 El ejemplo anterior genera la advertencia C4291, al no haberse definido ninguna versión de colocación del operador **delete** que se corresponda con la versión de colocación del operador **new**.  Para resolver el problema, inserte el código siguiente antes de **main**.  Observe que todos los parámetros de función del operador sobrecargado **delete** coinciden con los del operador sobrecargado **new**, excepto el primero.  
  
```  
void operator delete(void* pMem, char* pszFilename, int nLine)  
{  
   free(pMem);  
}  
```