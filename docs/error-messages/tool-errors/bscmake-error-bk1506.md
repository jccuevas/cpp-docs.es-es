---
title: Error de BSCMAKE BK1506 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1506
dev_langs:
- C++
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e19ec77818c8017387519b03e400c09d47021bc5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300428"
---
# <a name="bscmake-error-bk1506"></a>Error de BSCMAKE BK1506
no se puede abrir el archivo 'nombredearchivo' [: motivo]  
  
 BSCMAKE no puede abrir el archivo.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Archivo bloqueado por otro proceso. Si `reason` dice **permiso denegado**, el explorador puede estar usando el archivo. Cierre la ventana del explorador y vuelva a intentar la compilación.  
  
2.  Un disco lleno.  
  
3.  Un error de hardware.  
  
4.  El archivo de salida especificado tiene el mismo nombre que un subdirectorio existente.