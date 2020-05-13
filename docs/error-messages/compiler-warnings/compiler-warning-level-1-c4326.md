---
title: Advertencia del compilador (nivel 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: 32bcd85b1cd1bb6c89678daae02f4f31a9318b6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162977"
---
# <a name="compiler-warning-level-1-c4326"></a>Advertencia del compilador (nivel 1) C4326

> el tipo de valor devuelto de '*function*' debe ser '*tipo1*' en lugar de '*tipo2*'

## <a name="remarks"></a>Observaciones

Una función devolvió un tipo distinto de *tipo1*. Por ejemplo, con [/za](../../build/reference/za-ze-disable-language-extensions.md), **Main** no devolvió un valor **int**.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4326 y se muestra cómo corregirlo:

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```
