---
title: Compilador advertencia (nivel 1) C4953 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4953
dev_langs:
- C++
helpviewer_keywords:
- C4953
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e53808d4ad97bad4eccdf81b0a863277f8f7796
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194637"
---
# <a name="compiler-warning-level-1-c4953"></a>Advertencia del compilador (nivel 1) C4953

> Inlinee '*función*' se ha editado desde que se recopilaron los datos, datos de perfil no utilizados de perfil

Cuando se usa [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), el compilador detectó un módulo de entrada que se ha vuelto a compilar después `/LTCG:PGINSTRUMENT` y tiene una función (*función*) que se editó y donde ejecuciones de pruebas existentes identificado el función como candidata para inserción. Sin embargo, como resultado de volver a compilar el módulo, la función ya no será candidata para la inclusión en líneas.

Esta advertencia es informativa. Para resolver esta advertencia, ejecute `/LTCG:PGINSTRUMENT`, rehaga todas las pruebas y ejecute `/LTCG:PGOPTIMIZE`.

Esta advertencia se reemplazaría por un error si se hubiera usado `/LTCG:PGOPTIMIZE` .