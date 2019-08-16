---
title: bad_alloc (Clase)
ms.date: 11/04/2016
f1_keywords:
- new/std::bad_alloc
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
ms.openlocfilehash: 9d1d81e393b4a3eb27ea08bc53634bfcbc119240
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243977"
---
# <a name="badalloc-class"></a>bad_alloc (Clase)

Clase que describe una excepción que se produce para indicar que una solicitud de asignación no se realizó correctamente.

## <a name="syntax"></a>Sintaxis

```cpp
class bad_alloc : public exception {
    bad_alloc();
    virtual ~bad_alloc();
    bad_alloc(const bad_alloc&);
    bad_alloc& operator=(const bad_alloc&);
    const char* what() const override;
};
```

## <a name="remarks"></a>Comentarios

El valor devuelto por `what` es una cadena de C definido por la implementación. Ninguna de las funciones miembro produce excepciones.

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

```Output
bad allocation
```
