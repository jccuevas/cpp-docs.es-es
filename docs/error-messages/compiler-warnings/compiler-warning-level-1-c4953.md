---
title: Advertencia del compilador (nivel 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 1948342e1ff97c38ca3a44694dc7e7d399d96825
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384158"
---
# <a name="compiler-warning-level-1-c4953"></a>Advertencia del compilador (nivel 1) C4953

> Inlinee '*función*' se ha editado desde que se recopilaron los datos, datos de perfil no utilizados de perfil

Al usar [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después de `/LTCG:PGINSTRUMENT` y tiene una función (*function*) que se editó y donde las ejecuciones de pruebas existentes identifican la función como candidata para la inclusión en líneas. Sin embargo, como resultado de volver a compilar el módulo, la función ya no será candidata para la inclusión en líneas.

Esta advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.

Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .