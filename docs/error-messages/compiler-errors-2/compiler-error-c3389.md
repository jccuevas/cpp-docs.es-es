---
title: Error del compilador C3389 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f0f60a1096c070d28be3b7af161bbb924fb20dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3389"></a>Error del compilador C3389
__declspec(Keyword) no se puede usar con/CLR: pure o/CLR: safe  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 A [__declspec](../../cpp/declspec.md) modificador utilizado implica una por cada estado de proceso.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) implica un por [appdomain](../../cpp/appdomain.md) estado.  Por lo tanto, declarar una variable con el `keyword` **__declspec** modificador y compilar con **/CLR: pure** no está permitido.  
  
 El ejemplo siguiente genera C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```