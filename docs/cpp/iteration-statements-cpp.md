---
title: Instrucciones de iteración (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- iteration statements
- loop structures, iteration statements
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1973223d6aab44d4c5d8652111d3e6b8251676fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418918"
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