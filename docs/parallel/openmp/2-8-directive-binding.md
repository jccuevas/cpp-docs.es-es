---
title: 2.8 enlace de directivas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dc5b702b17e01bb8d4625a837abdb71086113e68
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415907"
---
# <a name="28-directive-binding"></a>2.8 Enlace de directivas

Enlace dinámico de directivas debe cumplir las reglas siguientes:

- El **para**, **secciones**, **único**, **maestro**, y **barrera** directivas enlazar a la dinámicamente envolvente **paralelo**, si existe alguno, independientemente del valor de cualquier **si** cláusula que puede estar presente en esa directiva. Si no hay ninguna región paralela se está ejecutando actualmente, las directivas se ejecutan por un equipo que se compone del subproceso principal.

- El **ordenados** directiva se enlaza a la inclusión dinámicamente **para**.

- El **atómica** Directiva exige acceso exclusivo con respecto a **atómica** directivas en todos los subprocesos, no solo el equipo actual.

- El **críticos** Directiva exige acceso exclusivo con respecto a **críticos** directivas en todos los subprocesos, no solo el equipo actual.

- Una directiva nunca puede enlazar dinámicamente a cualquier directiva fuera lo más parecido posible inclusión **paralelo**.