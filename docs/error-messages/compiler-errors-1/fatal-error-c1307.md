---
title: Error irrecuperable C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 1acdda77ac9cbf8d99752de3b78ab9c32bbb4cbc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338537"
---
# <a name="fatal-error-c1307"></a>Error irrecuperable C1307

el programa se ha editado desde que se recogieron los datos de perfil

Cuando se usa [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el vinculador detectó un módulo de entrada que se volvió a compilar después/LTCG: PGINSTRUMENT y que el módulo se cambió en el punto donde los datos de perfil existentes ya no están relevantes. Por ejemplo, si cambia el gráfico de llamadas en el módulo que se ha vuelto a compilar, el compilador generará C1307.

Para resolver este error, ejecute/LTCG: PGINSTRUMENT, rehacer todas las ejecuciones de prueba y ejecute/LTCG: PGOPTIMIZE. Si no se puede ejecutar/LTCG: PGINSTRUMENT y rehaga que todas las pruebas se ejecuta, utilice/LTCG: PGUPDATE en lugar de/LTCG: PGOPTIMIZE para crear la imagen optimizada.