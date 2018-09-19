---
title: Error irrecuperable C1307 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 65f398dd9885c571ea0d66171889f20d3321a3b9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085867"
---
# <a name="fatal-error-c1307"></a>Error irrecuperable C1307

el programa se ha editado desde que se recogieron los datos de perfil

Cuando se usa [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el vinculador detectó un módulo de entrada que se volvió a compilar después/LTCG: PGINSTRUMENT y que el módulo se cambió en el punto donde los datos de perfil existentes ya no están relevantes. Por ejemplo, si cambia el gráfico de llamadas en el módulo que se ha vuelto a compilar, el compilador generará C1307.

Para resolver este error, ejecute/LTCG: PGINSTRUMENT, rehacer todas las ejecuciones de prueba y ejecute/LTCG: PGOPTIMIZE. Si no se puede ejecutar/LTCG: PGINSTRUMENT y rehaga que todas las pruebas se ejecuta, utilice/LTCG: PGUPDATE en lugar de/LTCG: PGOPTIMIZE para crear la imagen optimizada.