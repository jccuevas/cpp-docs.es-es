---
title: Compilador advertencia (nivel 1) C4951 | Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4951
dev_langs:
- C++
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e26c4bc176a54f063a3f9bce2faf451a9c0406f0
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43204240"
---
# <a name="compiler-warning-level-1-c4951"></a>Advertencia del compilador (nivel 1) C4951

> '*función*' se ha editado desde que se recopilaron los datos, los datos de perfil de función no usa de perfil

Una función se ha editado en un módulo de entrada a [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de forma que los datos del perfil ahora no son válidos. El módulo de entrada se ha vuelto a compilar después **/LTCG: PGINSTRUMENT** y tiene una función (*función*) con un flujo de control diferente que el módulo en el momento de la  **/LTCG: PGINSTRUMENT** operación.

La advertencia es informativa. Para solucionar esta advertencia, ejecute **/LTCG:PGINSTRUMENT**, rehaga todas las ejecuciones de prueba y ejecute **/LTCG:PGOPTIMIZE**.

Esta advertencia se reemplazaría por un error si se hubiera usado **/LTCG:PGOPTIMIZE** .