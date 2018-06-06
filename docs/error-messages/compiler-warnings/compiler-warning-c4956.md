---
title: Advertencia del compilador C4956 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4956
dev_langs:
- C++
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be92eb948e31a0a5367f92f5c2ed59baac2bd39b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703709"
---
# <a name="compiler-warning-c4956"></a>Advertencia del compilador C4956

> '*tipo*': este tipo no es comprobable

## <a name="remarks"></a>Comentarios

Esta advertencia se genera cuando se especifica [/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) y el código contiene un tipo que no es comprobable. El **/CLR: safe** opción del compilador está en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

Para obtener más información, consulte [código puro y comprobable (C++ / CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

Esta advertencia se emite como un error y puede deshabilitarse con pragma [warning](../../preprocessor/warning.md) o la opción del compilador [/wd](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```