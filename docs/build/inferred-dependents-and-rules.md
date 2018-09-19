---
title: Inferir dependientes y reglas | Microsoft Docs
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
ms.openlocfilehash: c13ae7784ff40b39642ce26fd062a1aab80f2d4c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707556"
---
# <a name="inferred-dependents-and-rules"></a>Dependientes inferidos y reglas

NMAKE supone un dependiente inferido para un destino, si existe una regla de inferencia aplicable. Una regla se aplica si:

- *toext* coincide con la extensión del destino.

- *fromext* coincide con la extensión de un archivo que tiene el nombre base del destino y que existe en el directorio actual o especificado.

- *fromext* en [. SUFIJOS](../build/dot-directives.md); ninguna otra *fromext* en una regla de coincidencia tiene un valor superior **. SUFIJOS** prioridad.

- Ningún dependiente explícito tiene un valor superior **. SUFIJOS** prioridad.

Dependientes inferidos pueden provocar efectos secundarios inesperados. Si el bloque de descripción del destino contiene comandos, NMAKE ejecuta esos comandos en lugar de los comandos en la regla.

## <a name="see-also"></a>Vea también

[Reglas de inferencia](../build/inference-rules.md)