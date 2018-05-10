---
title: inline_depth | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e40b9382abc8ee0fa0c003964eebe75bc075e473
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="inlinedepth"></a>inline_depth
Especifica la profundidad de búsqueda heurística alineada de tal forma que ninguna función se inserte si está en una profundidad (en el gráfico de llamadas) mayor que `n`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma inline_depth( [n] )  
```  
  
## <a name="remarks"></a>Comentarios  
 Esta directiva pragma controla la inclusión de las funciones marcadas como [en línea](../cpp/inline-functions-cpp.md) y [__inline](../cpp/inline-functions-cpp.md) o insertadas automáticamente bajo la opción/Ob2.  
  
 `n` puede ser un valor entre 0 y 255, donde 255 significa una profundidad ilimitada en el gráfico de llamadas y cero deshabilita la expansión alineada.  Cuando no se especifica `n`, se usa el valor predeterminado (254).  
  
 El **inline_depth** pragma controla el número de veces que se puede expandir una serie de llamadas de función. Por ejemplo, si la profundidad alineada es cuatro y A llama a B y B después llama a C, las tres llamadas se expandirán alineadas. Sin embargo, si la expansión alineada más próxima es de dos, solo se expanden A y B, y C permanece como una llamada a función.  
  
 Para utilizar esta directiva pragma, debe establecer la opción del compilador /Ob en 1 o 2. La profundidad establecida mediante esta directiva pragma surte efecto en la primera llamada a función después de pragma.  
  
 La profundidad alineada puede reducirse durante la expansión, pero no se puede aumentar. Si la profundidad alineada es seis y durante la expansión, el preprocesador encuentra una **inline_depth** pragma con un valor de ocho, la profundidad permanece en seis.  
  
 El **inline_depth** pragma no surte ningún efecto en las funciones marcadas con `__forceinline`.  
  
> [!NOTE]
>  Las funciones recursivas pueden sustituirse alineadas con una profundidad máxima de 16 llamadas.  
  
## <a name="see-also"></a>Vea también  
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_recursion](../preprocessor/inline-recursion.md)