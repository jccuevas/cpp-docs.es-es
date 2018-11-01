---
title: 2.4.2 sections (Construcción)
ms.date: 11/04/2016
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
ms.openlocfilehash: 2d9fca08eecd382c9d3df60159c13ac188a1ab85
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50486819"
---
# <a name="242-sections-construct"></a>2.4.2 sections (Construcción)

El **secciones** directiva identifica una construcción noniterative uso compartido que especifica un conjunto de construcciones que se va a dividir entre los subprocesos en un equipo. Cada sección se ejecuta una vez por un subproceso en el equipo. La sintaxis de la **secciones** directiva es como sigue:

```
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

La cláusula es uno de los siguientes:

**private(** *variable-list* **)**

**firstprivate(** *variable-list* **)**

**lastprivate(** *variable-list* **)**

**reducción (** *operador* **:***lista de variables* **)**

**nowait**

Cada sección está precedido por un **sección** directiva, aunque el **sección** directiva es opcional para la primera sección. El **sección** las directivas deben aparecer dentro de la extensión de léxico el **secciones** directiva. Hay una barrera implícita al final de un **secciones** construir, a menos que un **nowait** se especifica.

Restricciones para el **secciones** directiva son los siguientes:

- Un **sección** directiva no debe aparecer fuera de la extensión de léxico el **secciones** directiva.

- Una sola **nowait** cláusula puede aparecer en un **secciones** directiva.

## <a name="cross-references"></a>Referencias cruzadas:

- **privada**, **firstprivate**, **lastprivate**, y **reducción** cláusulas, vea [sección 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) en la página 25.