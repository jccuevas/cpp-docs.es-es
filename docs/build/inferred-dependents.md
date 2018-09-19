---
title: Dependientes inferidos | Microsoft Docs
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
ms.openlocfilehash: 631c5631b60f0e05dd1f1541facc767f35944d3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701485"
---
# <a name="inferred-dependents"></a>Dependientes inferidos

Un dependiente inferido se deriva de una regla de inferencia y se evalúa antes que dependientes explícitos. Si no está actualizado con respecto a su destino un dependiente inferido, NMAKE invoca el bloque de comandos para la dependencia. Si un dependiente inferido no existe o no está actualizado con respecto a sus propios dependientes, NMAKE actualiza primero el dependiente inferido. Para obtener más información sobre dependientes inferidos, vea [las reglas de inferencia](../build/inference-rules.md).

## <a name="see-also"></a>Vea también

[Dependientes](../build/dependents.md)