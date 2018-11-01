---
title: 2.9 Anidamiento de directivas
ms.date: 11/04/2016
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
ms.openlocfilehash: 804cafd65fde19e501b89c47925f471143d74938
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438733"
---
# <a name="29-directive-nesting"></a>2.9 Anidamiento de directivas

Anidamiento dinámico de directivas debe cumplir las reglas siguientes:

- Un **paralelo** directiva dinámicamente dentro de otra **paralelo** lógicamente establece un nuevo equipo, que se compone del subproceso actual, a menos que anidada paralelismo está habilitado.

- **para**, **secciones**, y **único** directivas que se enlazan a la misma **paralelo** no pueden anidarse dentro de otros.

- **crítica** no pueden anidarse dentro de otras directivas con el mismo nombre. Tenga en cuenta que esta restricción no es suficiente para evitar el interbloqueo.

- **para**, **secciones**, y **único** directivas no están permitidas en la extensión dinámica de **críticos**, **ordenados**, y **maestro** regiones si las directivas se enlazan a la misma **paralelo** como las regiones.

- **barrera** directivas no están permitidas en la extensión dinámica de **para**, **ordenados**, **secciones**, **único**, **maestro**, y **críticos** regiones si las directivas se enlazan a la misma **paralelo** como las regiones.

- **maestro** directivas no están permitidas en la extensión dinámica de **para**, **secciones**, y **único** directivas si el **master** directivas enlazar al mismo **paralelo** como las directivas de uso compartido.

- **ordenada** directivas no se permiten en la extensión dinámica de **críticos** regiones si las directivas se enlazan a la misma **paralelo** como las regiones.

- También se permite cualquier directiva que se permite cuando se ejecuta de forma dinámica dentro de una región paralela cuando se ejecuta fuera de una región paralela. Cuando se ejecuta dinámicamente fuera de una región paralela especificada por el usuario, la directiva se ejecuta por un equipo que se compone del subproceso principal.