---
title: Reglas de inferencia
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: cb67fc8fe8e65814c9b169f7936c7d225d26e1e3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471050"
---
# <a name="inference-rules"></a>Reglas de inferencia

Las reglas de inferencia proporcionan comandos para actualizar los destinos e inferir dependientes para destinos. Extensiones en una regla de inferencia coinciden con un único destino y dependientes que tienen el mismo nombre base. Las reglas de inferencia son definidas por el usuario o predefinidos. reglas predefinidas se pueden redefinir.

Si una dependencia no actualizada no tiene comandos y [. SUFIJOS](../build/dot-directives.md) contiene la extensión del dependiente, usos NMAKE una regla cuyas extensiones coinciden con el destino y una existente de archivos en el directorio actual o especificado. Si más de una regla coincide con los archivos existentes, la **. SUFIJOS** lista determina que se va a usar; prioridad de la lista desciende de izquierda a derecha. Si un archivo dependiente no existe y no aparece como un destino en otro bloque de descripción, una regla de inferencia puede crear la falta dependiente de otro archivo con el mismo nombre base. Si el destino de un bloque de descripción no tiene elementos dependientes o comandos, una regla de inferencia puede actualizar el destino. Las reglas de inferencia pueden crear un destino de línea de comandos, aunque no exista ningún bloque de descripción. NMAKE puede invocar una regla para un dependiente inferido incluso si se especifica un dependiente explícito.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Definir una regla](../build/defining-a-rule.md)

[Reglas de modo por lotes](../build/batch-mode-rules.md)

[Reglas predefinidas](../build/predefined-rules.md)

[Dependientes inferidos y reglas](../build/inferred-dependents-and-rules.md)

[Prioridad en las reglas de inferencia](../build/precedence-in-inference-rules.md)

## <a name="see-also"></a>Vea también

[Referencia de NMAKE](../build/nmake-reference.md)