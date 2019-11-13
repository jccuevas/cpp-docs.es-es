---
title: ADVERTENCIA del compilador (nivel 3) C4290
ms.date: 11/04/2016
f1_keywords:
- C4290
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
ms.openlocfilehash: 5ccacd7d5f4dfd2e9ad8de3958d7aa43571091fe
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051662"
---
# <a name="compiler-warning-level-3-c4290"></a>ADVERTENCIA del compilador (nivel 3) C4290

C++se omitió la especificación de excepción excepto para indicar que una función no es __declspec (nothrow)

Una función se declara mediante la especificación de la excepción C++ , que Visual acepta pero no implementa. Es posible que sea necesario volver a compilar y vincular el código con especificaciones de excepción que se omiten durante la compilación y que se pueden volver a usar en versiones futuras que admitan especificaciones de excepción.

Para obtener más información, vea [Especificaciones de excepciones (Throw)](../../cpp/exception-specifications-throw-cpp.md) .

Puede evitar esta advertencia mediante el pragma [Warning](../../preprocessor/warning.md) :

```cpp
#pragma warning( disable : 4290 )
```

En el ejemplo de código siguiente se genera C4290:

```cpp
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```