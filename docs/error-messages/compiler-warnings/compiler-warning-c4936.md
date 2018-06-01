---
title: Advertencia del compilador C4936 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0be4a565dd251da77174c401c23b8ed8bfc531b0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703944"
---
# <a name="compiler-warning-c4936"></a>Advertencia del compilador C4936

> __declspec se admite solamente cuando se compila con /clr o /clr:pure

## <a name="remarks"></a>Comentarios

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

Se utilizó un modificador `__declspec` , pero ese modificador `__declspec` solo es válido cuando se compila con una de las opciones [/clr](../../build/reference/clr-common-language-runtime-compilation.md) .

Para más información, consulte [appdomain](../../cpp/appdomain.md) y [process](../../cpp/process.md).

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