---
title: Error irrecuperable C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 6ad00eb3d95e9f09d4f84daefb7e2a87fd1a3abf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203364"
---
# <a name="fatal-error-c1305"></a>Error irrecuperable C1305

la base de datos del perfil 'archivo_pgd' es para una arquitectura diferente

Un archivo. pgd generado a partir de la operación/LTCG: PGINSTRUMENT de otra plataforma se pasó a [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) . Las [optimizaciones guiadas por perfiles](../../build/profile-guided-optimizations.md) están disponibles para las plataformas x86 y x64. Sin embargo, un archivo .pgd generado con una operación /LTCG:PGINSTRUMENT de una plataforma no es válido como entrada para una operación /LTCG:PGOPTIMIZE de otra plataforma.

Para resolver este error, pase únicamente un archivo .pgd creado mediante las operaciones /LTCG:PGINSTRUMENT a /LTCG:PGOPTIMIZE de la misma plataforma.
