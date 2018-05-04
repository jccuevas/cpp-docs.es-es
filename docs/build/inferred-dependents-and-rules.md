---
title: Inferir dependientes y reglas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aae09fd756e0eb4eab3031beb5b4cba8c4d35a40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="inferred-dependents-and-rules"></a>Dependientes inferidos y reglas
NMAKE supone un dependiente inferido para un destino si existe una regla de inferencia aplicable. Una regla se aplica si:  
  
-   *toext* coincide con la extensión del destino.  
  
-   *fromext* coincide con la extensión de un archivo que tiene el nombre base del destino y que existe en el directorio actual o especificado.  
  
-   *fromext* en [. SUFIJOS](../build/dot-directives.md); ninguna otra *fromext* en una regla de coincidencia tiene un valor superior **. SUFIJOS** prioridad.  
  
-   Ningún dependiente explícito tiene una prioridad **. SUFIJOS** prioridad.  
  
 Dependientes inferidos pueden provocar efectos secundarios inesperados. Si el bloque de descripción del destino contiene comandos, NMAKE ejecuta esos comandos en lugar de los comandos de la regla.  
  
## <a name="see-also"></a>Vea también  
 [Reglas de inferencia](../build/inference-rules.md)