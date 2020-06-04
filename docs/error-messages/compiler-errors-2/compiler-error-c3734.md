---
title: Error del compilador C3734
ms.date: 11/04/2016
f1_keywords:
- C3734
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
ms.openlocfilehash: 381bb59dae523c05cdc67e33ba9d326e247abc7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752865"
---
# <a name="compiler-error-c3734"></a>Error del compilador C3734

'class': una clase administrada o de WinRT no puede ser una coclase

El atributo [CoClass](../../windows/coclass.md) no se puede usar con clases administradas o WinRT.

En el siguiente ejemplo se genera el error C3734 y se muestra cómo corregirlo:

```cpp
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```
