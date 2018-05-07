---
title: Advertencia de BSCMAKE BK4502 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs:
- C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ed7145c28b10885dc6edf0c399478aea4503ca0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="bscmake-warning-bk4502"></a>Advertencia de BSCMAKE BK4502
trunca. SBR truncado 'filename' no está en nombre de archivo  
  
 Se especificó un archivo .sbr de longitud cero que no formaba parte de un archivo .bsc durante una actualización.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Especificadas el nombre de archivo incorrecto.  
  
2.  Archivo eliminado. (Error [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) resultados.)  
  
3.  Archivo dañado que requiere que BSCMAKE realice una compilación completa.