---
title: 2.8 Enlace de directivas
ms.date: 11/04/2016
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
ms.openlocfilehash: fb22d1b503303842ff73550c1c6544cae7e5f2f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528627"
---
# <a name="28-directive-binding"></a>2.8 Enlace de directivas

Enlace dinámico de directivas debe cumplir las reglas siguientes:

- El **para**, **secciones**, **único**, **maestro**, y **barrera** directivas enlazar a la dinámicamente envolvente **paralelo**, si existe alguno, independientemente del valor de cualquier **si** cláusula que puede estar presente en esa directiva. Si no hay ninguna región paralela se está ejecutando actualmente, las directivas se ejecutan por un equipo que se compone del subproceso principal.

- El **ordenados** directiva se enlaza a la inclusión dinámicamente **para**.

- El **atómica** Directiva exige acceso exclusivo con respecto a **atómica** directivas en todos los subprocesos, no solo el equipo actual.

- El **críticos** Directiva exige acceso exclusivo con respecto a **críticos** directivas en todos los subprocesos, no solo el equipo actual.

- Una directiva nunca puede enlazar dinámicamente a cualquier directiva fuera lo más parecido posible inclusión **paralelo**.