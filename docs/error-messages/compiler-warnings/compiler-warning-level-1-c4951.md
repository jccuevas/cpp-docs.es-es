---
title: Compilador advertencia (nivel 1) C4951 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c3ebf012338bdf6b90cc943e754056335c6751a4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4951"></a>Advertencia del compilador (nivel 1) C4951
'function' se ha editado desde que se recopilaron los datos de perfil; los datos de perfil de la función no se han utilizado  
  
 Una función se ha editado en un módulo de entrada a [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de forma que los datos del perfil ahora no son válidos. El módulo de entrada se ha vuelto a compilar después de **/LTCG:PGINSTRUMENT** y tiene una función (***function***) con un flujo de control diferente que el del módulo en el momento de la operación **/LTCG:PGINSTRUMENT** .  
  
 La advertencia es informativa. Para solucionar esta advertencia, ejecute **/LTCG:PGINSTRUMENT**, rehaga todas las ejecuciones de prueba y ejecute **/LTCG:PGOPTIMIZE**.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado **/LTCG:PGOPTIMIZE** .