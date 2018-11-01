---
title: bad_alloc (Clase)
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 1ebb427277c985fdab711d5bd84dcea54898a83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515614"
---
# <a name="badalloc-class"></a>bad_alloc (Clase)

Clase que describe una excepción que se produce para indicar que una solicitud de asignación no se realizó correctamente.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_alloc : public exception {
    bad_alloc();
virtual ~bad_alloc();

};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por `what` es una cadena de C definido por la implementación. Ninguna de las funciones miembro produce excepciones.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<new>

**Espacio de nombres:** std

## <a name="example"></a>Ejemplo

```cpp
// bad_alloc.cpp
// compile with: /EHsc
#include<new>
#include<iostream>
using namespace std;

int main() {
   char* ptr;
   try {
      ptr = new char[(~unsigned int((int)0)/2) - 1];
      delete[] ptr;
   }
   catch( bad_alloc &ba) {
      cout << ba.what( ) << endl;
   }
}
```

## <a name="sample-output"></a>Resultados del ejemplo

```Output
bad allocation
```

## <a name="requirements"></a>Requisitos

**Encabezado:** \<new>

## <a name="see-also"></a>Vea también

[exception (Clase)](../standard-library/exception-class.md)<br/>
[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
