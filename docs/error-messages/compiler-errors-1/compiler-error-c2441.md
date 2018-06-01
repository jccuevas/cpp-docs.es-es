---
title: Error del compilador C2441 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2441
dev_langs:
- C++
helpviewer_keywords:
- C2441
ms.assetid: ffbd6573-777a-48dd-892f-5cf4a758dcab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d4224d9090f3ace43f61a10c599fafa78d21600
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705285"
---
# <a name="compiler-error-c2441"></a>Error del compilador C2441

> '*variable*': un símbolo declarado con __declspec (proceso) debe ser constante en/CLR: pure modo

## <a name="remarks"></a>Comentarios

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admiten en Visual Studio de 2017.

De forma predeterminada, las variables son por dominio de aplicación bajo **/CLR: pure**. Una variable marcada `__declspec(process)` en **/CLR: pure** es propenso a errores si se modifica en un dominio de aplicación y leer en otro.

Por lo tanto, el compilador exige por proceso de ser variables `const` en **/CLR: puro**, hacer que ellos leen solo en todos los dominios de aplicación.

Para obtener más información, consulte [proceso](../../cpp/process.md) y [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C2441.

```cpp
// C2441.cpp
// compile with: /clr:pure /c
__declspec(process) int i;   // C2441
__declspec(process) const int j = 0;   // OK
```