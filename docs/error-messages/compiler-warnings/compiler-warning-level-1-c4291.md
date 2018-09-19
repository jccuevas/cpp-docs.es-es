---
title: Compilador advertencia (nivel 1) C4291 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4291
dev_langs:
- C++
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8c5f2fe57d26de4b4b2f88a85f20b99344ac201
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038053"
---
# <a name="compiler-warning-level-1-c4291"></a>Advertencia del compilador (nivel 1) C4291

'declaration': no coincidente se encuentra; de operador delete no se liberará memoria si la inicialización produce una excepción

Una selección de ubicación [nueva](../../cpp/new-operator-cpp.md) se usa para las que no hay ninguna selección de ubicación [eliminar](../../cpp/delete-operator-cpp.md).

Cuando se asigna memoria para un objeto con el operador **nueva**, se llama al constructor del objeto. Si el constructor produce una excepción, debe desasignarse toda la memoria que se asignó para el objeto. Esto no puede tener lugar a menos que un operador **eliminar** función existe que coincida con el operador **nuevo**.

Si usa el operador **nueva** sin argumentos adicionales y compilar con [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md), o/EHa opciones para habilitar el control de excepciones, el compilador generará código para llamar al operador **eliminar** si el constructor produce una excepción.

Si usa el formato de ubicación de la **nuevo** operador (el formulario con argumentos además del tamaño de la asignación) y el constructor del objeto produce una excepción, el compilador seguirá generando código para llamar al operador **eliminar**; pero solo lo hará por tanto, si un formulario de selección de ubicación del operador **eliminar** existe el formato de la ubicación del operador de coincidencia **nuevo** que asignó la memoria. Por ejemplo:

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

El ejemplo anterior genera la advertencia C4291 porque no hay ningún formulario de selección de ubicación del operador **eliminar** se ha definido que coincida con el formato de la ubicación del operador **nuevo**. Para resolver el problema, inserte el código siguiente encima **principal**. Tenga en cuenta que todo el operador sobrecargado **eliminar** parámetros de función coinciden con los del operador sobrecargado **nuevo**, salvo el primer parámetro.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```