---
title: Compilador (nivel 4) de la advertencia C4457 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4457
dev_langs: C++
helpviewer_keywords: C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 77965ba08b311768b54788692d3f5b7fa724f5b8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4457"></a>Compilador (nivel 4) de la advertencia C4457
  
> declaración de '*identificador*' oculta el parámetro de función
  
La declaración de *identificador* en el ámbito local oculta la declaración del parámetro de función con un nombre idéntico. Esta advertencia le permite saber que las referencias a *identificador* en el ámbito local resolver en la versión declarada localmente, no el parámetro, que puede ser o no su intención. Para corregir este problema, se recomienda que proporcionar nombres de variables locales que no entren en conflicto con nombres de parámetro.  
    
## <a name="example"></a>Ejemplo
  
El ejemplo siguiente genera C4457 porque el parámetro `x` y la variable local `x` en `member_fn` tienen los mismos nombres. Para corregir este problema, use nombres diferentes para los parámetros y variables locales.  
  
```cpp  
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        } 
        a += x; // uses parameter x
    }
} s;
```  
