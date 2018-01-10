---
title: Compilador advertencia (nivel 1) C4951 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4951
dev_langs: C++
helpviewer_keywords: C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 199df135d5d2c00255037e5a1b31db80e2683d4f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4951"></a>Advertencia del compilador (nivel 1) C4951
'function' se ha editado desde que se recopilaron los datos de perfil; los datos de perfil de la función no se han utilizado  
  
 Una función se ha editado en un módulo de entrada a [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md), de forma que los datos del perfil ahora no son válidos. El módulo de entrada se ha vuelto a compilar después de **/LTCG:PGINSTRUMENT** y tiene una función (***function***) con un flujo de control diferente que el del módulo en el momento de la operación **/LTCG:PGINSTRUMENT** .  
  
 La advertencia es informativa. Para solucionar esta advertencia, ejecute **/LTCG:PGINSTRUMENT**, rehaga todas las ejecuciones de prueba y ejecute **/LTCG:PGOPTIMIZE**.  
  
 Esta advertencia se reemplazaría por un error si se hubiera usado **/LTCG:PGOPTIMIZE** .