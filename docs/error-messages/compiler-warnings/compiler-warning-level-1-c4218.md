---
title: Compilador advertencia (nivel 1) C4218 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4218
dev_langs:
- C++
helpviewer_keywords:
- C4218
ms.assetid: d6c3cd90-4518-49e9-ae86-4ba9e2761d98
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 6f657da21a7756973b9f9febe823003ebfd68fd1
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4218"></a>Advertencia del compilador (nivel 1) C4218
se ha utilizado una extensión no estándar : se debe especificar al menos una clase de almacenamiento o un tipo  
  
 Con las extensiones de Microsoft predeterminadas (/Ze), puede declarar una variable sin especificar una clase de almacenamiento o tipo. El tipo predeterminado es `int`.  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4218.c  
// compile with: /W4  
i;  // C4218  
  
int main()  
{  
}  
```  
  
 Estas declaraciones no son válidas en la compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).
