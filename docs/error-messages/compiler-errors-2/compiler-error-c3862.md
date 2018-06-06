---
title: Error del compilador C3862 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b21e457feb6d090e4abaf531293987eb3504457
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704976"
---
# <a name="compiler-error-c3862"></a>Error del compilador C3862

> '*función*': no se puede compilar una función no administrada con/CLR: pure o/CLR: safe

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

Una compilación con **/CLR: pure** o **/CLR: safe** producirá una imagen sólo MSIL, una imagen con ningún código nativo (no administrado).  Por lo tanto, no puede usar el `unmanaged` pragma en una **/CLR: pure** o **/CLR: safe** compilación.

Para obtener más información, consulte [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) y [managed, unmanaged](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```