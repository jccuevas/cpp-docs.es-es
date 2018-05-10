---
title: bad_alloc (Clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- new/std::bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab496a5de8062f6888b92b318788ff72345bc7c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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

El valor que devuelve **what** es una cadena de C definida por la implementación. Ninguna de las funciones miembro produce excepciones.

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

[Clase Exception](../standard-library/exception-class.md) [seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
