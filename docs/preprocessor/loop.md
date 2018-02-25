---
title: bucle | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- loop_CPP
- vc-pragma.loop
dev_langs:
- C++
ms.assetid: 6d5bb428-cead-47e7-941d-7513bbb162c7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f3e076c48b512c6059a2f574a07f6e77acfaca22
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="loop"></a>bucle
Controla cómo el paralelizador automático debe considerar el código del bucle y/o excluye un bucle de la consideración del vectorizador automático.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#pragma loop( hint_parallel(n) )  
```  
  
```  
  
#pragma loop( no_vector )  
```  
  
```  
  
#pragma loop( ivdep )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `hint_parallel(` `n` `)`  
 Sugiere al compilador que este bucle se ejecute en paralelo en `n` subprocesos, donde `n` es un literal entero positivo o cero. Si `n` es cero, se usa el número máximo de subprocesos en tiempo de ejecución. Esta es una sugerencia que se hace al compilador, no una orden y, por tanto, no existen garantías de que el bucle se ejecute en paralelo. Si el bucle tiene dependencias de datos o problemas estructurales (por ejemplo, el bucle se almacena en un valor escalar que se usa más allá del cuerpo del bucle), el bucle no se ejecuta en paralelo.  
  
 El compilador omite esta opción a menos que la [/Qpar](../build/reference/qpar-auto-parallelizer.md) ha especificado el modificador de compilador.  
  
 `no_vector`  
 De forma predeterminada, el vectorizador automático está activado e intentará vectorizar todos los bucles que evalúe de modo que se beneficien de él. Especifique esta directiva pragma para deshabilitar el vectorizador automático para el bucle que aparece detrás.  
  
 `ivdep`  
 Sugiere al compilador que omita las dependencias de vector de este bucle. Se utiliza junto con `hint_parallel`.  
  
## <a name="remarks"></a>Comentarios  
 Para utilizar la directiva pragma `loop`, colóquela inmediatamente antes de una definición de bucle, no dentro de ella. La directiva pragma surte efecto para el ámbito del bucle que aparece detrás. Puede aplicar varias directivas pragma a un bucle, en cualquier orden, pero debe establecer cada una de ellas en una instrucción pragma diferente.  
  
## <a name="see-also"></a>Vea también  
 [Paralelización y vectorización automática](../parallel/auto-parallelization-and-auto-vectorization.md)   
 [Directivas pragma y la palabra clave __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)