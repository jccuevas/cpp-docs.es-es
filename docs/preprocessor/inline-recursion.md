---
title: inline_recursion | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f81347c8286dfa1f0651af43bd3134565a22aade
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849501"
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