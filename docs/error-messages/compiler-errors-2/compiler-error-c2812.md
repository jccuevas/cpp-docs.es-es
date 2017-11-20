---
title: Error del compilador C2812 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2812
dev_langs: C++
helpviewer_keywords: C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 859d371d5886ece416ea6d60c405b114a527864f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2812"></a>Error del compilador C2812
\#no se admite la importación con/CLR: pure y/CLR: safe  
  
 Las opciones del compilador **/clr:pure** y **/clr:safe** están en desuso en Visual Studio 2015.  
  
 [#import (directiva)](../../preprocessor/hash-import-directive-cpp.md) no es compatible con **/CLR: pure** y **/CLR: safe** porque `#import` requiere el uso de bibliotecas de compatibilidad de compilador nativo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2812.  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```