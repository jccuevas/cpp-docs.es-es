---
title: Error del compilador C3455
ms.date: 11/04/2016
f1_keywords:
- C3455
helpviewer_keywords:
- C3455
ms.assetid: 218e5cfe-5391-4eeb-81c2-85c47e3a6cd2
ms.openlocfilehash: e016105a53b4020ca8ed83a95b0c9b96036b1884
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756674"
---
# <a name="compiler-error-c3455"></a>Error del compilador C3455

'attribute': ninguno de los constructores de atributo coincidía con los argumentos

Se usó un valor no válido para declarar un atributo.  Vea [attribute](../../windows/attributes/attribute.md) para obtener más información.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3455.

```cpp
// C3455.cpp
// compile with: /clr /c
using namespace System;

[attribute("MyAt")]   // C3455
// try the following line instead
// [attribute(All)]
ref struct MyAttr {
   MyAttr() {}
};
```
