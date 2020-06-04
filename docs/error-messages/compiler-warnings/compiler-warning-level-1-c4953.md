---
title: Advertencia del compilador (nivel 1) C4953
ms.date: 08/27/2018
f1_keywords:
- C4953
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
ms.openlocfilehash: 46f07227b5df62938cc51a7be4cf4f3595a0d947
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174524"
---
# <a name="compiler-warning-level-1-c4953"></a>Advertencia del compilador (nivel 1) C4953

> La '*función*' insertada se ha editado desde que se recopilaron los datos de perfil; los datos de perfil no se usan

Al usar [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después de `/LTCG:PGINSTRUMENT` y tiene una función (*function*) que se editó y donde las ejecuciones de pruebas existentes identifican la función como candidata para la inclusión en líneas. Sin embargo, como resultado de volver a compilar el módulo, la función ya no será candidata para la inclusión en líneas.

Esta advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.

Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .
