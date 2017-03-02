---
title: C2812 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2812
dev_langs:
- C++
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 358d0d3a5c7f0129d74be70c3309337542807d1d
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2812"></a>Error del compilador C2812
\#no se admite la importación con/CLR: pure y/CLR: safe  
  
 El **/CLR: pure** y **/CLR: safe** opciones del compilador están desusadas en Visual Studio 2015.  
  
 [#import (directiva)](../../preprocessor/hash-import-directive-cpp.md) no es compatible con **/CLR: pure** y **/CLR: safe** porque `#import` requiere el uso de bibliotecas de compatibilidad de compilador nativo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2812.  
  
```  
// C2812.cpp  
// compile with: /clr:pure /c  
#import "importlib.tlb"   // C2812  
```
