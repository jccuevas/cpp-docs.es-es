---
title: Error del compilador C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: 633ffa86bce3579adb808dbba34127bb6f0665c9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749417"
---
# <a name="compiler-error-c3895"></a>Error del compilador C3895

' var ': los miembros de datos de tipo no pueden ser ' volatile '

Ciertos tipos de miembros de datos, por ejemplo, [literal](../../extensions/literal-cpp-component-extensions.md) o [InitOnly](../../dotnet/initonly-cpp-cli.md), no pueden ser [volátiles](../../cpp/volatile-cpp.md).

En el ejemplo siguiente se genera C3895:

```cpp
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```
