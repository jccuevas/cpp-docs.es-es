---
title: Advertencia del compilador C4936
ms.date: 11/04/2016
f1_keywords:
- C4936
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
ms.openlocfilehash: c6d54cf8b6704eec2a9e6af890c5c80c67106995
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165007"
---
# <a name="compiler-warning-c4936"></a>Advertencia del compilador C4936

> __declspec se admite solamente cuando se compila con /clr o /clr:pure

## <a name="remarks"></a>Observaciones

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Se utilizó un modificador `__declspec` , pero ese modificador `__declspec` solo es válido cuando se compila con una de las opciones [/clr](../../build/reference/clr-common-language-runtime-compilation.md) .

Para obtener más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).

La advertencia C4936 siempre se emite como error.  Puede deshabilitar la advertencia C4936 con la pragma [warning](../../preprocessor/warning.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4936:

```cpp
// C4936.cpp
// compile with: /c
// #pragma warning (disable : 4936)
__declspec(process) int i;   // C4936
__declspec(appdomain) int j;   // C4936
```
