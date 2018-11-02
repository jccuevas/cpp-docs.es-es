---
title: Error del compilador C3062
ms.date: 11/04/2016
f1_keywords:
- C3062
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
ms.openlocfilehash: ac45847c94e7d2dc731eba71b0a38105eb915e53
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590416"
---
# <a name="compiler-error-c3062"></a>Error del compilador C3062

'enum': enumerador requiere un valor porque el tipo subyacente es 'type'

Puede especificar un tipo subyacente para una enumeración. Sin embargo, algunos tipos requieren asignar valores a cada enumerador.

Para obtener más información sobre las enumeraciones, vea [clase enum](../../windows/enum-class-cpp-component-extensions.md).

El ejemplo siguiente genera C3062:

```
// C3062.cpp
// compile with: /clr

enum class MyEnum : bool { a };   // C3062
enum class MyEnum2 : bool { a = true};   // OK
```