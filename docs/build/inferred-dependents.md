---
title: Dependientes inferidos
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 958a33c29be0d68fee1044fff1d81235ea9370c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641381"
---
# <a name="inferred-dependents"></a>Dependientes inferidos

Un dependiente inferido se deriva de una regla de inferencia y se evalúa antes que dependientes explícitos. Si no está actualizado con respecto a su destino un dependiente inferido, NMAKE invoca el bloque de comandos para la dependencia. Si un dependiente inferido no existe o no está actualizado con respecto a sus propios dependientes, NMAKE actualiza primero el dependiente inferido. Para obtener más información sobre dependientes inferidos, vea [las reglas de inferencia](../build/inference-rules.md).

## <a name="see-also"></a>Vea también

[Dependientes](../build/dependents.md)