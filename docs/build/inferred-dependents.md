---
title: Dependientes inferidos
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: d4d12d0ab686c604ce0d4495df89ec62c6160ebe
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414154"
---
# <a name="inferred-dependents"></a>Dependientes inferidos

Un dependiente inferido se deriva de una regla de inferencia y se evalúa antes que dependientes explícitos. Si no está actualizado con respecto a su destino un dependiente inferido, NMAKE invoca el bloque de comandos para la dependencia. Si un dependiente inferido no existe o no está actualizado con respecto a sus propios dependientes, NMAKE actualiza primero el dependiente inferido. Para obtener más información sobre dependientes inferidos, vea [las reglas de inferencia](../build/inference-rules.md).

## <a name="see-also"></a>Vea también

[Dependientes](../build/dependents.md)
