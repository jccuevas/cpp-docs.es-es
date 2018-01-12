---
title: Advertencia de BSCMAKE BK4502 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- BK4502
- BK1513
dev_langs: C++
helpviewer_keywords:
- BK1513
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 042aaf4c416bf88c87b3177c40cf3f1611385922
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-warning-bk4502"></a>Advertencia de BSCMAKE BK4502
trunca. SBR truncado 'filename' no está en nombre de archivo  
  
 Se especificó un archivo .sbr de longitud cero que no formaba parte de un archivo .bsc durante una actualización.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Especificadas el nombre de archivo incorrecto.  
  
2.  Archivo eliminado. (Error [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) resultados.)  
  
3.  Archivo dañado que requiere que BSCMAKE realice una compilación completa.