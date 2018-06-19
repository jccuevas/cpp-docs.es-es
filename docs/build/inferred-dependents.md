---
title: Dependientes inferidos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a86ed1a8fe6c97ae11af50f59cb639ef6fd7c1da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367903"
---
# <a name="inferred-dependents"></a>Dependientes inferidos
Un dependiente inferido se deriva de una regla de inferencia y se evalúa antes que dependientes explícitos. Si un dependiente inferido no está actualizado con respecto a su destino, NMAKE invoca el bloque de comandos para la dependencia. Si un dependiente inferido no existe o no está actualizado con respecto a sus propios dependientes, NMAKE actualiza primero el dependiente inferido. Para obtener más información sobre dependientes inferidos, vea [reglas de inferencia](../build/inference-rules.md).  
  
## <a name="see-also"></a>Vea también  
 [Dependientes](../build/dependents.md)