---
title: Error de BSCMAKE BK1506 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: BK1506
dev_langs: C++
helpviewer_keywords: BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f553646689fd1e703e10f100bca6d989c8f767d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-error-bk1506"></a>Error de BSCMAKE BK1506
no se puede abrir el archivo 'nombredearchivo' [: motivo]  
  
 BSCMAKE no puede abrir el archivo.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Archivo bloqueado por otro proceso. Si `reason` dice **permiso denegado**, el explorador puede estar usando el archivo. Cierre la ventana del explorador y vuelva a intentar la compilación.  
  
2.  Un disco lleno.  
  
3.  Un error de hardware.  
  
4.  El archivo de salida especificado tiene el mismo nombre que un subdirectorio existente.