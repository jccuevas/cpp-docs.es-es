---
title: 2.4.3 single (Construcción)
ms.date: 11/04/2016
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
ms.openlocfilehash: 7dda98ee83ee08adc29830a9c4ada71a208705fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466370"
---
# <a name="243-single-construct"></a>2.4.3 single (Construcción)

El **único** directiva identifica una construcción que especifica que se ejecuta el bloque estructurado asociado sólo un subproceso en el equipo (no necesariamente el subproceso principal). La sintaxis de la **único** directiva es como sigue:

```
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

La cláusula es uno de los siguientes:

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**copyprivate (** *lista de variables* **)**

**nowait**

Hay una barrera implícita después de la **único** construir a menos que un **nowait** se especifica la cláusula.

Restricciones para el **único** directiva son los siguientes:

- Una sola **nowait** cláusula puede aparecer en un **único** directiva.

- El **copyprivate** cláusula no debe usarse con la **nowait** cláusula.

## <a name="cross-references"></a>Referencias cruzadas:

- **privada**, **firstprivate**, y **copyprivate** cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.