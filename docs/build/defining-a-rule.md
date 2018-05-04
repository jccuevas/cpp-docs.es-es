---
title: Definir una regla | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8ff7c58033ac5f7e42764d185c45c206bf406f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="defining-a-rule"></a>Definir una regla
El *fromext* representa la extensión de un archivo dependiente, y *toext* representa la extensión de un archivo de destino.  
  
```  
.fromext.toext:  
   commands  
```  
  
## <a name="remarks"></a>Comentarios  
 Las extensiones no distinguen mayúsculas de minúsculas. Pueden llamar a las macros para representar *fromext* y *toext*; se expanden las macros durante el preprocesamiento. El punto (.) anterior *fromext* debe aparecer al principio de la línea. Los dos puntos (:) está precedido por cero o más espacios o tabulaciones. Solo puede ir seguido sólo por espacios o tabulaciones, un punto y coma (;) para especificar un comando, un signo de número (#) para especificar un comentario ni un carácter de nueva línea. Otros espacios de no se permiten. Hay comandos en bloques de descripción.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Rutas de búsqueda en reglas](../build/search-paths-in-rules.md)  
  
## <a name="see-also"></a>Vea también  
 [Reglas de inferencia](../build/inference-rules.md)