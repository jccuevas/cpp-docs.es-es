---
title: "Instrucciones de iteración (C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c06ae1c043551bbb4ed6469ab3f87d1ed86fd92
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iteration-statements-c"></a>Instrucciones de iteración (C++)
Las instrucciones de iteración producen instrucciones (o instrucciones compuestas) que se ejecutarán cero o más veces, según determinados criterios de la finalización de bucle. Cuando estas instrucciones son instrucciones compuestas, se ejecutan en orden, excepto cuando ya sea el [salto](../cpp/break-statement-cpp.md) instrucción o [continuar](../cpp/continue-statement-cpp.md) se encuentra la instrucción.  
  
 C++ proporciona cuatro instrucciones de iteración: [mientras](../cpp/while-statement-cpp.md), [hacer](../cpp/do-while-statement-cpp.md), [para](../cpp/for-statement-cpp.md), y [basado en intervalo para](../cpp/range-based-for-statement-cpp.md). Cada una de ellas se repite hasta que la expresión de finalización se evalúa como cero (false), o hasta que se fuerza la finalización de bucle con un **salto** instrucción. En la tabla siguiente se resumen estas instrucciones y sus acciones; cada una se explica detalladamente en las secciones siguientes.  
  
### <a name="iteration-statements"></a>Instrucciones de iteración  
  
|Instrucción|Se evalúa en|Inicialización|Incremento|  
|---------------|------------------|--------------------|---------------|  
|`while`|Principio del bucle|No|No|  
|**do**|Final del bucle|No|No|  
|**for**|Principio del bucle|Sí|Sí|  
|**basado en intervalo para**|Principio del bucle|Sí|Sí|  
  
 La parte de instrucción de una instrucción de iteración no puede ser una declaración. Sin embargo, puede ser una instrucción compuesta que contenga una declaración.  
  
## <a name="see-also"></a>Vea también  
 [Información general sobre las instrucciones de C++](../cpp/overview-of-cpp-statements.md)