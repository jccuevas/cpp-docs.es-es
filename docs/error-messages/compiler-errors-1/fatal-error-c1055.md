---
title: Error irrecuperable C1055 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1055
dev_langs:
- C++
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 07f0dc0e8dca08e8b0de47b73516d3fdfa21435b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1055"></a>Error irrecuperable C1055
límite del compilador: no hay claves  
  
 El archivo de origen contiene demasiados símbolos. El compilador se quedó sin claves hash para la tabla de símbolos.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Divida el archivo de origen en archivos más pequeños.  
  
2.  Eliminar archivos de encabezado innecesarios.  
  
3.  Volver a usar las variables temporales y globales en lugar de crear otros nuevos.