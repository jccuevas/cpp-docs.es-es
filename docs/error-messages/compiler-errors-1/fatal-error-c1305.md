---
title: Error irrecuperable C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: d67f0eabfd0718d8a3e3dd75e96c3e6c0d2266b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623215"
---
# <a name="fatal-error-c1305"></a>Error irrecuperable C1305

la base de datos del perfil 'archivo_pgd' es para una arquitectura diferente

Un archivo .pgd generado a partir de la operación/LTCG: PGINSTRUMENT de otra plataforma que se pasó a [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Las optimizaciones guiadas por perfil](../../build/reference/profile-guided-optimizations.md) están disponibles para las plataformas x86 y x64. Sin embargo, un archivo .pgd generado con una operación /LTCG:PGINSTRUMENT de una plataforma no es válido como entrada para una operación /LTCG:PGOPTIMIZE de otra plataforma.

Para resolver este error, pase únicamente un archivo .pgd creado mediante las operaciones /LTCG:PGINSTRUMENT a /LTCG:PGOPTIMIZE de la misma plataforma.