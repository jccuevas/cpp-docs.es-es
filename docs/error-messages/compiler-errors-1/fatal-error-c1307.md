---
title: Error irrecuperable C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: c7eb90c8e17408f6898ef7ff1a9d9e5efcafb4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203351"
---
# <a name="fatal-error-c1307"></a>Error irrecuperable C1307

el programa se ha editado desde que se recogieron los datos de perfil

Al usar [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el vinculador detectó un módulo de entrada que se volvió a compilar después de/LTCG: PGINSTRUMENT y que el módulo se cambió al punto en el que los datos de perfil existentes ya no son relevantes. Por ejemplo, si el gráfico de llamadas ha cambiado en el módulo recompilado, el compilador generará C1307.

Para resolver este error, ejecute/LTCG: PGINSTRUMENT, rehaga todas las ejecuciones de pruebas y ejecute/LTCG: PGOPTIMIZE. Si no puede ejecutar/LTCG: PGINSTRUMENT y rehacer todas las ejecuciones de pruebas, use/LTCG: PGUPDATE en lugar de/LTCG: PGOPTIMIZE para crear la imagen optimizada.
