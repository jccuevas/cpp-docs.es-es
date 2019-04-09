---
title: Error del compilador C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 7a627ce28e60f42dabcf0a257464a8bfbd58b9a4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028632"
---
# <a name="compiler-error-c2483"></a>Error del compilador C2483

>'*identificador*': no se puede declarar el objeto con constructor o destructor 'thread'

Este mensaje de error es obsoleta en Visual Studio 2015 y versiones posteriores. En versiones anteriores, las variables declaradas con el `thread` atributo no se puede inicializar con un constructor u otra expresión que requiere la evaluación del tiempo de ejecución. Se requiere una expresión estática para inicializar `thread` datos.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2483 en Visual Studio 2013 y versiones anteriores.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Vea también

[thread](../../cpp/thread.md)