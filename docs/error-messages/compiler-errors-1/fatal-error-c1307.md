---
title: Error irrecuperable C1307 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fe97f1658a74b0db5985ed755bf387811f2c6d1b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1307"></a>Error irrecuperable C1307
el programa se ha editado desde que se recogieron los datos de perfil  
  
 Cuando se usa [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el vinculador detectó un módulo de entrada que se ha vuelto a compilar después de/LTCG: PGINSTRUMENT y que el módulo se modificó hasta el punto donde los datos de perfil existentes ya no están relevantes. Por ejemplo, si cambia el gráfico de llamadas en el módulo ha vuelto a compilar, el compilador generará C1307.  
  
 Para resolver este error, ejecute/LTCG: PGINSTRUMENT, vuelva a realizar todas las ejecuciones de prueba y ejecute/LTCG: PGOPTIMIZE. Si no se puede ejecutar/LTCG: PGINSTRUMENT y rehaga que todas las pruebas se ejecuta, utilice/LTCG: PGUPDATE en lugar de/LTCG: PGOPTIMIZE para crear la imagen optimizada.