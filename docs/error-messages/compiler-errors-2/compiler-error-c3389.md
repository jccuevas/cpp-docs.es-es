---
title: Error del compilador C3389 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd88753553d2bad1cb9253cfe709e7627c4b01ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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