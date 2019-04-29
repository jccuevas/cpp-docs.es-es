---
title: Dependientes inferidos y reglas
ms.date: 11/04/2016
helpviewer_keywords:
- rules, inferred
- inferred dependents in NMAKE
- inferred rules in NMAKE
- dependents, inferred
ms.assetid: 9381e74a-53d9-445c-836d-0ff7ef6112d9
ms.openlocfilehash: b9c3055db0cc173999e1737986166eb334dcf96c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269913"
---
# <a name="inferred-dependents-and-rules"></a>Dependientes inferidos y reglas

NMAKE supone un dependiente inferido para un destino, si existe una regla de inferencia aplicable. Una regla se aplica si:

- *toext* coincide con la extensión del destino.

- *fromext* coincide con la extensión de un archivo que tiene el nombre base del destino y que existe en el directorio actual o especificado.

- *fromext* en [. SUFIJOS](dot-directives.md); ninguna otra *fromext* en una regla de coincidencia tiene un valor superior **. SUFIJOS** prioridad.

- Ningún dependiente explícito tiene un valor superior **. SUFIJOS** prioridad.

Dependientes inferidos pueden provocar efectos secundarios inesperados. Si el bloque de descripción del destino contiene comandos, NMAKE ejecuta esos comandos en lugar de los comandos en la regla.

## <a name="see-also"></a>Vea también

[Reglas de inferencia](inference-rules.md)
