---
title: Error irrecuperable C1307 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1307
dev_langs:
- C++
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d06ce51ada7cd9159b8e02ff627bf12ebb7293d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33227140"
---
# <a name="fatal-error-c1307"></a>Error irrecuperable C1307
el programa se ha editado desde que se recogieron los datos de perfil  
  
 Cuando se usa [/LTCG: PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), el vinculador detectó un módulo de entrada que se ha vuelto a compilar después de/LTCG: PGINSTRUMENT y que el módulo se modificó hasta el punto donde los datos de perfil existentes ya no están relevantes. Por ejemplo, si cambia el gráfico de llamadas en el módulo ha vuelto a compilar, el compilador generará C1307.  
  
 Para resolver este error, ejecute/LTCG: PGINSTRUMENT, vuelva a realizar todas las ejecuciones de prueba y ejecute/LTCG: PGOPTIMIZE. Si no se puede ejecutar/LTCG: PGINSTRUMENT y rehaga que todas las pruebas se ejecuta, utilice/LTCG: PGUPDATE en lugar de/LTCG: PGOPTIMIZE para crear la imagen optimizada.