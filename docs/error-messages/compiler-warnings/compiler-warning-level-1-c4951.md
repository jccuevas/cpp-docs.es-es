---
title: Advertencia del compilador (nivel 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: 73e048aeaa044c35e09539b07d51398829a0fdfd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408063"
---
# <a name="compiler-warning-level-1-c4951"></a>Advertencia del compilador (nivel 1) C4951

> '*función*' se ha editado desde que se recopilaron los datos, los datos de perfil de función no usa de perfil

Una función se ha editado en un módulo de entrada a [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de forma que los datos del perfil ahora no son válidos. El módulo de entrada se ha vuelto a compilar después de **/LTCG:PGINSTRUMENT** y tiene una función (*function*) con un flujo de control diferente que el del módulo en el momento de la operación **/LTCG:PGINSTRUMENT** .

La advertencia es informativa. Para solucionar esta advertencia, ejecute **/LTCG:PGINSTRUMENT**, rehaga todas las ejecuciones de prueba y ejecute **/LTCG:PGOPTIMIZE**.

Esta advertencia se reemplazaría por un error si se hubiera usado **/LTCG:PGOPTIMIZE** .