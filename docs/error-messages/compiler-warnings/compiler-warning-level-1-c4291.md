---
title: Advertencia del compilador (nivel 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: cd161a37683703fd67b4c682558a51121c130816
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175719"
---
# <a name="compiler-warning-level-1-c4291"></a>Advertencia del compilador (nivel 1) C4291

' DECLARATION ': no se encontró ninguna eliminación de operador coincidente; no se liberará memoria si la inicialización produce una excepción.

Se utiliza una ubicación [nueva](../../cpp/new-operator-cpp.md) para la que no hay ninguna [eliminación](../../cpp/delete-operator-cpp.md)de ubicación.

Cuando se asigna memoria para un objeto con el operador **New**, se llama al constructor del objeto. Si el constructor produce una excepción, se debe desasignar cualquier memoria asignada para el objeto. Esto no puede tener lugar a menos que exista una función Operator **Delete** que coincida con el operador **New**.

Si usa el operador **New** sin ningún argumento adicional y compila con las opciones [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md)o/EHA para habilitar el control de excepciones, el compilador generará código para llamar al operador **Delete** si el constructor produce una excepción.

Si utiliza el formulario de colocación del operador **New** (el formulario con argumentos además del tamaño de la asignación) y el constructor del objeto produce una excepción, el compilador seguirá generando código para llamar al operador **Delete**; pero solo lo hará si existe un formulario de colocación de operador **Delete** que coincida con el formato de ubicación del operador **nuevo** que asignó la memoria. Por ejemplo:

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

En el ejemplo anterior se genera la advertencia C4291 porque no se ha definido ninguna forma de colocación de operador **Delete** que coincida con el formato de ubicación del operador **New**. Para solucionar el problema, inserte el siguiente código encima de **Main**. Observe que todos los parámetros de la función de **eliminación** de operadores sobrecargados coinciden con los del operador sobrecargado **New**, excepto para el primer parámetro.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
