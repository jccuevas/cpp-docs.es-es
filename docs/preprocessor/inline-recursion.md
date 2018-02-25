---
title: inline_recursion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f3e4ef784d2fcb9ec076d9f8a7c87ffee1d5800
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="inlinerecursion"></a>inline_recursion
Controla la expansión en línea de llamadas de función directas o mutuamente recursivas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>Comentarios  
 Use esta pragma para controlar funciones marcadas como [en línea](../cpp/inline-functions-cpp.md) y [__inline](../cpp/inline-functions-cpp.md) o funciones que el compilador expanda automáticamente bajo la opción/Ob2. El uso de esta directiva pragma requiere un [/Ob](../build/reference/ob-inline-function-expansion.md) valor de la opción de compilador de 1 ó 2. El estado predeterminado de `inline_recursion` es desactivado. Esta pragma tiene efecto en la primera llamada de función después de que se considere la directiva pragma y no afecta a la definición de la función.  
  
 La directiva pragma `inline_recursion` controla cómo se expanden las funciones recursivas. Si `inline_recursion` está desactivada y una función insertada se llama a sí misma (directa o indirectamente), la función solo se expande una vez. Si `inline_recursion` está activada, la función se expande varias veces hasta que alcanza el valor establecido con la [inline_depth](../preprocessor/inline-depth.md) pragma, el valor predeterminado para funciones recursivas definido por el `inline_depth` pragma o una límite de capacidad .  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_depth](../preprocessor/inline-depth.md)   
 [/Ob (Expansión de funciones insertadas)](../build/reference/ob-inline-function-expansion.md)