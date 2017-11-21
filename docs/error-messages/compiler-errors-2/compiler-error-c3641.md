---
title: Error del compilador C3641 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3641
dev_langs: C++
helpviewer_keywords: C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 992e2a5d34b380146a99f6f78145b022eacd21d6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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