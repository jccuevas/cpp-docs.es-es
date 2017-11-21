---
title: Error del compilador C2533 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2533
dev_langs: C++
helpviewer_keywords: C2533
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c21849c7318ac4f169bf7104a478fa57ba7dd040
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2533"></a>Error del compilador C2533
'identificador': los constructores no permiten un tipo de valor devuelto  
  
 Un constructor no puede tener un tipo de valor devuelto (ni siquiera un tipo de valor devuelto `void`).  
  
 Una causa común de este error es la ausencia de un punto y coma entre el final de una definición de clase y la primera implementación de constructor. El compilador ve la clase como una definición del tipo de valor devuelto para la función de constructor y genera C2533.  
  
 El ejemplo siguiente genera el error C2533 y muestra cómo corregirlo:  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```