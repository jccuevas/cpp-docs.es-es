---
title: "Advertencia del compilador C4801 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4801"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4801"
ms.assetid: 05b29dff-15ef-42ca-9712-dc993afc4fd6
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4801
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede comprobar la devolución por referencia: razón  
  
 No se puede almacenar una referencia de seguimiento en una variable local y después, devolverla de modo que se pueda comprobar.  
  
 Una referencia sólo se puede devolver de modo que sea comprobable cuando el comprobador puede realizar su seguimiento desde la creación al punto de devolución y cuando se trata de una referencia a un elemento de una matriz, o a un miembro de una clase.  
  
 Para obtener más información, vea [Peverify.exe \(PEVerify Tool\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md).  
  
 Para que pueda ser comprobable, una referencia debe permanecer en la pila desde la creación hasta la devolución.  
  
 La advertencia C4801 siempre se emite como error.  Puede desactivar esta advertencia con `#pragma warning` o **\/wd**; vea [warning](../../preprocessor/warning.md) o [\/w, \/Wn, \/WX, \/Wall, \/wln, \/wdn, \/wen, \/won \(Nivel de advertencia\)](../../build/reference/compiler-option-warning-level.md) para obtener más información.  
  
## Ejemplo  
 La advertencia C4801 se generará si el comprobador no puede ver la dirección tomada, por lo que debe suponer que podría ser una referencia no comprobable.  El ejemplo siguiente genera el error C4801.  
  
```  
// C4801.cpp  
// compile with: /clr:safe /c  
int% f(int% p) {  
   return p;   // C4801  
}  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4801.  
  
```  
// C4801_b.cpp  
// compile with: /clr:safe /c  
  
int% f(int i, array<int>^ ar) {  
   int x;  
   int% bri = x;   // cannot return a byref to a local.  
   if (i < ar->Length) {  
      bri = ar[i];   // this byref is ok.  
   }  
  
   return bri;   // C4801 not returned within the basic block  
}  
```  
  
## Ejemplo  
 La advertencia C4801 también puede aparecer si se intenta desreferenciar y devolver un valor de referencia en un bloque try.  El resultado será que se generará un código que no se podrá comprobar porque la pila se habrá borrado al final de un bloque try, destruyendo todo valor devuelto en la pila.  En su lugar, desreferencie el tipo de referencia y asígnelo a una variable, para garantizar que no se produzca ninguna excepción.  A continuación, al final de la función, desreferencie el tipo de referencia y devuélvalo.  
  
 El ejemplo siguiente genera el error C4801.  
  
```  
// C4801_c.cpp  
// compile with: /clr:safe  
using namespace System;  
  
ref class StackEmptyException : public System::Exception {};  
ref class StackFullException : public System::Exception {};  
  
template <typename T>  
ref struct Stack {  
  
   Stack() {  
      topElem = -1;   // initialize stack  
      stackPtr = gcnew array<T>(10);  
   }  
  
   void push(const T%);  
   T% top();  
  
private:  
   int topElem;    
   array<T>^ stackPtr;    
};  
  
template <typename T>   
T% Stack<T>::top() {  
   try {  
      return stackPtr[topElem];   // C4801  
      // Try the following line instead.  
      // T% deadstore = stackPtr[topElem] ;  
   }  
  
   catch (System::IndexOutOfRangeException ^ e) {  
      throw gcnew StackEmptyException();  
   }  
  
   catch (System::Exception ^ e) {  
      throw;  
   }  
  
   return stackPtr[topElem] ;  
}  
  
int main() {  
   typedef Stack<Int32> IntStack;  
   IntStack ^ is = gcnew IntStack();  
  
   int i = 1;  
   while (1) {  
      try {  
         is->push(i++);  
      }  
      catch (System::Exception ^ e) {  
         break;  
      }  
      Console::Write("{0} ", is->top());  
   }  
}  
```