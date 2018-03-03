---
title: Definir una regla | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c0d6ca616e3685db36d6d24b339a860eab4c6150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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