---
title: Reglas de inferencia
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: d3d7ca41d96d3845237b445edefff05044dacdc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170519"
---
# <a name="inference-rules"></a>Reglas de inferencia

Las reglas de inferencia proporcionan comandos para actualizar los destinos y para deducir los dependientes de los destinos. Las extensiones en una regla de inferencia coinciden con un único destino y dependiente que tienen el mismo nombre base. Las reglas de inferencia están definidas por el usuario o están predefinidas; se pueden redefinir las reglas predefinidas.

Si una dependencia no actualizada no tiene comandos, y si [. Sufijos](dot-directives.md) que contiene la extensión del dependiente, NMAKE usa una regla cuyas extensiones coinciden con el destino y con un archivo existente en el directorio actual o especificado. Si hay más de una regla que coincida con los archivos existentes, el **. La lista de sufijos** determina cuál usar; la prioridad de la lista desciende de izquierda a derecha. Si un archivo dependiente no existe y no aparece como destino en otro bloque de descripción, una regla de inferencia puede crear el dependiente que falta de otro archivo con el mismo nombre base. Si el destino de un bloque de descripción no tiene ningún comando o dependientes, una regla de inferencia puede actualizar el destino. Las reglas de inferencia pueden compilar un destino de línea de comandos aunque no exista ningún bloque de descripción. NMAKE puede invocar una regla para un dependiente deducido incluso si se especifica un dependiente explícito.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Definir una regla](defining-a-rule.md)

[Reglas de modo por lotes](batch-mode-rules.md)

[Reglas predefinidas](predefined-rules.md)

[Dependientes y reglas inferidos](inferred-dependents-and-rules.md)

[Prioridad en las reglas de inferencia](precedence-in-inference-rules.md)

## <a name="see-also"></a>Consulte también

[Referencia de NMAKE](nmake-reference.md)
