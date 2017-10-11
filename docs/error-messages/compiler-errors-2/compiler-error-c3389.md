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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 561359afcd9cf694369bd1addb4f641a33a3f989
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

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
