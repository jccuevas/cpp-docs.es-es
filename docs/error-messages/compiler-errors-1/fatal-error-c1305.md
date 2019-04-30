---
title: Error irrecuperable C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 988842a0d5e8002ffd1478a2e10a8c88ee971911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397502"
---
# <a name="fatal-error-c1305"></a>Error irrecuperable C1305

la base de datos del perfil 'archivo_pgd' es para una arquitectura diferente

Un archivo .pgd generado a partir de la operación/LTCG: PGINSTRUMENT de otra plataforma que se pasó a [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . [Las optimizaciones guiadas por perfil](../../build/profile-guided-optimizations.md) están disponibles para las plataformas x86 y x64. Sin embargo, un archivo .pgd generado con una operación /LTCG:PGINSTRUMENT de una plataforma no es válido como entrada para una operación /LTCG:PGOPTIMIZE de otra plataforma.

Para resolver este error, pase únicamente un archivo .pgd creado mediante las operaciones /LTCG:PGINSTRUMENT a /LTCG:PGOPTIMIZE de la misma plataforma.