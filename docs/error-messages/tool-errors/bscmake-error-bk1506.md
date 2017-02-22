---
title: "Error de BSCMAKE BK1506 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1506"
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error de BSCMAKE BK1506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede abrir el archivo 'nombredearchivo' \[: reason\]  
  
 BSCMAKE no puede abrir el archivo.  
  
### Posibles causas del error:  
  
1.  Archivo bloqueado por otro proceso.  Si `reason` indica **Permiso denegado**, puede que el explorador esté usando el archivo.  Cierre la ventana del explorador y vuelva a intentar la compilación.  
  
2.  Disco lleno.  
  
3.  Error de hardware.  
  
4.  El archivo de salida especificado tiene el mismo nombre que un subdirectorio.