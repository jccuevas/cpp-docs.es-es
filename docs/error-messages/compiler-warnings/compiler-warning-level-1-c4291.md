---
title: Advertencia del compilador (nivel 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c1972236e30be4e6ca738b606b00398f5c7860e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754854"
---
# <a name="compiler-warning-level-1-c4291"></a>Advertencia del compilador (nivel 1) C4291

'declaración': no se ha encontrado ninguna eliminación de operador coincidente; memoria no se liberará si la inicialización produce una excepción

Se utiliza una ubicación [nueva](../../cpp/new-operator-cpp.md) para la que no hay [ninguna eliminación de](../../cpp/delete-operator-cpp.md)ubicación.

Cuando se asigna memoria para un objeto con el operador **new**, se llama al constructor del objeto. Si el constructor produce una excepción, se debe desasignar cualquier memoria asignada para el objeto. Esto no puede tener lugar a menos que exista una función **de eliminación** de operador que coincida con el operador **new**.

Si usa el operador **new** sin ningún argumento adicional y compila con las opciones [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md)o /EHa para habilitar el control de excepciones, el compilador generará código para llamar a **operator delete** si el constructor produce una excepción.

Si usa el formulario de ubicación del operador **new** (el formulario con argumentos además del tamaño de la asignación) y el constructor del objeto produce una excepción, el compilador seguirá generando código para llamar al operador **delete**; pero solo lo hará si existe una forma de colocación de **eliminación** de operador que coincida con la forma de ubicación del operador **nuevo** que asignó la memoria. Por ejemplo:

```cpp
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

El ejemplo anterior genera la advertencia C4291 porque no se ha definido ninguna forma de ubicación de **eliminación** de operador que coincida con la forma de ubicación del operador **new**. Para resolver el problema, inserte el siguiente código encima de **main**. Observe que todos los parámetros de función **delete** del operador sobrecargado coinciden con los del operador sobrecargado **new**, excepto el primer parámetro.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
