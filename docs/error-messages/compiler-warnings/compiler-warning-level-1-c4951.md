---
title: Advertencia del compilador (nivel 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: d94347df17bac01334cfd85c2bd9f6c8a98b5fc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174601"
---
# <a name="compiler-warning-level-1-c4951"></a>Advertencia del compilador (nivel 1) C4951

> '*function*' se ha editado desde que se recopilaron los datos de perfil; los datos de Perfil de función no se usan

Una función se ha editado en un módulo de entrada a [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de forma que los datos del perfil ahora no son válidos. El módulo de entrada se ha vuelto a compilar después de **/LTCG:PGINSTRUMENT** y tiene una función (*function*) con un flujo de control diferente que el del módulo en el momento de la operación **/LTCG:PGINSTRUMENT** .

Esta advertencia es informativa. Para solucionar esta advertencia, ejecute **/LTCG:PGINSTRUMENT**, rehaga todas las ejecuciones de prueba y ejecute **/LTCG:PGOPTIMIZE**.

Esta advertencia se reemplazaría por un error si se hubiera usado **/LTCG:PGOPTIMIZE** .
