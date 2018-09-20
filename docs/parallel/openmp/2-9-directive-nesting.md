---
title: 2.9 anidamiento de directivas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9558180a2f063171be563219f89ec3858e37a5d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396994"
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