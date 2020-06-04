---
title: Error del compilador C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: 9b1fbc8f4ca2ce3434a30e833f4741bc17015bbb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749534"
---
# <a name="compiler-error-c3062"></a>Error del compilador C3062

' ENUM ': el enumerador requiere un valor porque el tipo subyacente es ' type '

Puede especificar un tipo subyacente para una enumeración. Sin embargo, algunos tipos requieren que se asignen valores a cada enumerador.

Para obtener más información sobre las enumeraciones, vea [enum (clase](../../extensions/enum-class-cpp-component-extensions.md)).

En el ejemplo siguiente se genera C3062:

```cpp
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```
