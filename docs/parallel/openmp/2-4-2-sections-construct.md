---
title: 2.4.2 sections (construcción) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 35ae940e37b40cbb9c883c4d7d6bca7b0fa65520
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410553"
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