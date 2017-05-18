---
title: Compilador advertencia (nivel 4) C4458 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4458
dev_langs:
- C++
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
caps.latest.revision: 0
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 07b8db673b2db27f456f0e7228695c83497d1278
ms.contentlocale: es-es
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-warning-level-4-c4458"></a>Compilador advertencia (nivel 4) C4458
  
> declaración de '*identificador*' oculta el miembro de clase
  
La declaración de *identificador* en el ámbito local oculta la declaración de idéntico nombre *identificador* en el ámbito de clase. Esta advertencia le permite saber que las referencias a *identificador* en este ámbito resolver en la versión declarada localmente, no la clase miembro versión, que puede ser o no su intención. Para corregir este problema, se recomienda que proporcionar nombres de variables locales que no entren en conflicto con nombres de miembro de clase.  
    
## <a name="example"></a>Ejemplo
  
El ejemplo siguiente genera C4458 porque el parámetro `x` y la variable local `y` en `member_fn` tienen los mismos nombres que los miembros de datos en la clase. Para corregir este problema, use nombres diferentes para los parámetros y variables locales.  
  
```cpp  
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;  
        // To fix this issue, change the parameter name x
        // and local name y to something that does not 
        // conflict with the data member names.
    }
} s;
```  

