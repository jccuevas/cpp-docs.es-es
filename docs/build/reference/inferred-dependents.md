---
title: Dependientes inferidos
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 2382dec960ef93fc2f73987ad27b4670768a68cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291540"
---
# <a name="inferred-dependents"></a>Dependientes inferidos

Un dependiente inferido se deriva de una regla de inferencia y se evalúa antes que dependientes explícitos. Si no está actualizado con respecto a su destino un dependiente inferido, NMAKE invoca el bloque de comandos para la dependencia. Si un dependiente inferido no existe o no está actualizado con respecto a sus propios dependientes, NMAKE actualiza primero el dependiente inferido. Para obtener más información sobre dependientes inferidos, vea [las reglas de inferencia](inference-rules.md).

## <a name="see-also"></a>Vea también

[Dependientes](dependents.md)
