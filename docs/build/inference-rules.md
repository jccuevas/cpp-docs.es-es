---
title: Las reglas de inferencia | Documentos de Microsoft
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
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 932aad860cd2b78208857ca7b028e35cd96d481e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="inference-rules"></a>Reglas de inferencia
Las reglas de inferencia proporcionan comandos para actualizar destinos e inferir dependientes para destinos. Extensiones en una regla de inferencia coinciden con un único destino y dependientes que tienen el mismo nombre base. Las reglas de inferencia son definidas por el usuario o predefinidos. pueden volver a definir las reglas predefinidas.  
  
 Si una dependencia no actualizada no tiene comandos y si [. SUFIJOS](../build/dot-directives.md) contiene la extensión del dependiente, usos NMAKE una regla cuyas extensiones coinciden con el destino y una existente de archivos en el directorio actual o especificado. Si más de una regla coincide con archivos existentes, la **. SUFIJOS** lista determina que se va a usar; la prioridad de la lista desciende de izquierda a derecha. Si un archivo dependiente no existe y no se incluye como un destino en otro bloque de descripción, una regla de inferencia puede crear la falta dependiente de otro archivo con el mismo nombre base. Si el destino de un bloque de descripción no tiene dependientes ni comandos, una regla de inferencia puede actualizar el destino. Las reglas de inferencia pueden crear un destino de línea de comandos aunque no exista ningún bloque de descripción. NMAKE puede invocar una regla para un dependiente inferido aunque se especifique un dependiente explícito.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?  
 [Definir una regla](../build/defining-a-rule.md)  
  
 [Reglas de modo por lotes](../build/batch-mode-rules.md)  
  
 [Reglas predefinidas](../build/predefined-rules.md)  
  
 [Dependientes inferidos y reglas](../build/inferred-dependents-and-rules.md)  
  
 [Prioridad en las reglas de inferencia](../build/precedence-in-inference-rules.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)