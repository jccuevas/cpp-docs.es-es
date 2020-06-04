---
title: ADVERTENCIA del compilador (nivel 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: 20d6010cb83107946c00f2f7b00cda771b2e70b9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199022"
---
# <a name="compiler-warning-level-3-c4159"></a>ADVERTENCIA del compilador (nivel 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>pragma pragma (pop,...): ha sacado el identificador '*Identifier*' insertado anteriormente

## <a name="remarks"></a>Observaciones

El código fuente contiene una instrucción de **envío** con un identificador para una directiva pragma seguida de una instrucción **pop** sin un identificador. Como resultado, se extrae el *identificador* y los usos posteriores del *identificador* pueden producir un comportamiento inesperado.

## <a name="example"></a>Ejemplo

Para evitar esta advertencia, proporcione un identificador en la instrucción **pop** . Por ejemplo:

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```
