---
title: Error del compilador C3641 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3641
dev_langs:
- C++
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 496ff73822dcc1c886fbd2020f8ec6b8a5a9a2f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3641"></a>Error del compilador C3641
'función': no válido de convención de llamada 'convención de llamada' para la función compilada con/CLR: pure o/CLR: safe  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 Solo [__clrcall](../../cpp/clrcall.md) se permite la convención de llamada con [/CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 El ejemplo siguiente genera C3641:  
  
```  
// C3641.cpp  
// compile with: /clr:pure /c  
void __cdecl f() {}   // C3641  
```