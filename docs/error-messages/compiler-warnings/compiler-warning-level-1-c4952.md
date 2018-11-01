---
title: Advertencia del compilador (nivel 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: c2e9b88125655d9ea0abe3e65500b149289ba83b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537584"
---
# <a name="compiler-warning-level-1-c4952"></a>Advertencia del compilador (nivel 1) C4952

> '*función*': se encontró ningún perfil de datos en la base de datos de programa '*archivo_pgd*'

Al usar [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después `/LTCG:PGINSTRUMENT` y que tiene presente una nueva función (*function*).

La advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.

Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .