---
title: Reglas de inferencia
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: 0c1db9150c3b2c36c35e6802bfcd639af45bdc82
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035707"
---
# <a name="inference-rules"></a>Reglas de inferencia

Las reglas de inferencia proporcionan comandos para actualizar los destinos e inferir dependientes para destinos. Extensiones en una regla de inferencia coinciden con un único destino y dependientes que tienen el mismo nombre base. Las reglas de inferencia son definidas por el usuario o predefinidos. reglas predefinidas se pueden redefinir.

Si una dependencia no actualizada no tiene comandos y [. SUFIJOS](dot-directives.md) contiene la extensión del dependiente, usos NMAKE una regla cuyas extensiones coinciden con el destino y una existente de archivos en el directorio actual o especificado. Si más de una regla coincide con los archivos existentes, la **. SUFIJOS** lista determina que se va a usar; prioridad de la lista desciende de izquierda a derecha. Si un archivo dependiente no existe y no aparece como un destino en otro bloque de descripción, una regla de inferencia puede crear la falta dependiente de otro archivo con el mismo nombre base. Si el destino de un bloque de descripción no tiene elementos dependientes o comandos, una regla de inferencia puede actualizar el destino. Las reglas de inferencia pueden crear un destino de línea de comandos, aunque no exista ningún bloque de descripción. NMAKE puede invocar una regla para un dependiente inferido incluso si se especifica un dependiente explícito.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué más desea saber?

[Definir una regla](defining-a-rule.md)

[Reglas de modo por lotes](batch-mode-rules.md)

[Reglas predefinidas](predefined-rules.md)

[Dependientes inferidos y reglas](inferred-dependents-and-rules.md)

[Prioridad en las reglas de inferencia](precedence-in-inference-rules.md)

## <a name="see-also"></a>Vea también

[Referencia de NMAKE](nmake-reference.md)