---
title: Compilador (nivel 4) de la advertencia C4456 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4456
dev_langs: C++
helpviewer_keywords: C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 937475e32ce3c57633f0d0c504ce0ca4b7c627c8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4456"></a>Compilador (nivel 4) de la advertencia C4456
  
> declaración de '*identificador*' oculta la declaración local
  
La declaración de *identificador* en el ámbito local oculta la declaración de la declaración anterior local del mismo nombre. Esta advertencia le permite saber que las referencias a *identificador* en el ámbito local resolver en la versión declarada localmente, no el local anterior, que puede ser o no su intención. Para corregir este problema, se recomienda que proporcionar nombres de variables locales que no entren en conflicto con otros nombres locales.  
    
## <a name="example"></a>Ejemplo
  
El ejemplo siguiente genera C4456 porque la variable de control de bucle `int x` y la variable local `double x` en `member_fn` tienen los mismos nombres. Para corregir este problema, use nombres diferentes para las variables locales.  
  
```cpp  
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        } 
        x += u; // uses local double x
    }
} s;
```  
