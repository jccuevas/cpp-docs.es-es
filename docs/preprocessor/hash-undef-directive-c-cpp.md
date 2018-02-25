---
title: '#undef (directiva) (C/C ++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#undef'
dev_langs:
- C++
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 428831b2718009fc0b471d238cff965f74528a2f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="undef-directive-cc"></a>#undef (Directiva) (C/C++)
Quita (anula la definición de) un nombre creado previamente con `#define`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
#undef   
identifier  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El `#undef` directiva quita la definición actual de *identificador*. Por lo tanto, las siguientes apariciones del *identificador* se omiten el preprocesador. Para quitar una definición de macro utilizando `#undef`, asigne a solo la macro *identificador* ; no proporcionan una lista de parámetros.  
  
 También puede aplicar la directiva `#undef` a un identificador que no tenga ninguna definición anterior. De este modo se garantiza que el identificador no esté definido. El reemplazo de macros no se realiza dentro de instrucciones `#undef`.  
  
 La directiva `#undef` se empareja normalmente con una directiva `#define` para crear una región en un programa de origen en el que un identificador tiene un significado especial. Por ejemplo, una función específica del programa de origen puede utilizar constantes de manifiesto para definir valores específicos del entorno que no afecten al resto del programa. La directiva `#undef` también funciona con la directiva `#if` para controlar la compilación condicional del programa de origen. Vea [#if, #elif, #else y #endif directivas](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) para obtener más información.  
  
 En el ejemplo siguiente, la directiva `#undef` quita las definiciones de una constante simbólica y una macro. Observe que solo se proporciona el identificador de la macro.  
  
```  
#define WIDTH 80  
#define ADD( X, Y ) ((X) + (Y))  
.  
.  
.  
#undef WIDTH  
#undef ADD  
```  
  
 **Específicos de Microsoft**  
  
 Las macros pueden no definirse desde la línea de comandos mediante la opción /U seguida de los nombres de las macros que no se definen. El efecto de emitir este comando es equivalente a una secuencia de `#undef` *nombre de la macro* instrucciones al principio del archivo.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)