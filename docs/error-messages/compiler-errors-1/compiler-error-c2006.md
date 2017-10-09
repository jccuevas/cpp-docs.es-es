---
title: C2006 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8d182e7a98d01dee4047defa5adb5ccc2dc7cde5
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2006"></a>C2006 de Error del compilador
'directiva' esperaba un nombre de archivo, que se encontró 'token'  
  
 Directivas como [#include](../../preprocessor/hash-include-directive-c-cpp.md) o [#import](../../preprocessor/hash-import-directive-cpp.md) requieren un nombre de archivo. Para resolver el error, asegúrese de que *token* es un nombre de archivo válido. Además, puede colocar el nombre de archivo dobles comillas o corchetes angulares.  
  
 El ejemplo siguiente genera C2006:  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 Posible solución:  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```
