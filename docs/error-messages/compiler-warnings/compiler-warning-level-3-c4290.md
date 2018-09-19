---
title: Compilador advertencia (nivel 3) C4290 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4290
dev_langs:
- C++
helpviewer_keywords:
- C4290
ms.assetid: d1c6d85b-28e0-4a1f-9d48-23593337a6fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a6f09d8f3396381f34a0fbe3c7150b5948cee01
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46015981"
---
# <a name="compiler-warning-level-3-c4290"></a>Advertencia del compilador (nivel 3) C4290

Especificación de excepciones de C++ ignoran, excepto to indicar que una función no es __declspec (nothrow)

Una función se declara mediante la especificación de excepción, que Visual C++ admite pero no implementa. Con la excepción que deba volver a compilar las especificaciones que se omiten durante la compilación de código y vinculada para ser reutilizado en futuras versiones que admiten las especificaciones de excepción.

Para obtener más información, consulte [especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md) .

Puede evitar esta advertencia mediante la [advertencia](../../preprocessor/warning.md) pragma:

```
#pragma warning( disable : 4290 )
```

Ejemplo de código siguiente genera C4290:

```
// C4290.cpp
// compile with: /EHs /W3 /c
void f1(void) throw(int) {}   // C4290

// OK
void f2(void) throw() {}
void f3(void) throw(...) {}
```