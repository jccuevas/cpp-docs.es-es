---
title: "Error de BSCMAKE BK1513 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1513"
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de BSCMAKE BK1513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la actualización no incremental requiere todos los archivos .SBR  
  
 BSCMAKE no puede compilar un archivo nuevo de información de examen \(.bsc\) debido a que uno o más archivos .sbr están truncados.  Para buscar los nombres de los archivos .sbr truncados, lea las advertencias [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) que acompañan a este error.  
  
 BSCMAKE puede actualizar un archivo .bsc con un archivo .sbr truncado, pero no puede compilar uno nuevo.  BSCMAKE podría compilar un archivo .bsc nuevo por las siguientes razones:  
  
-   Falta el archivo. bsc.  
  
-   Se ha especificado un nombre de archivo incorrecto para el archivo .bsc.  
  
-   El archivo .bsc está dañado.  
  
 Para resolver este problema, elimine los archivos .sbr truncados y recompílelos, o limpie la solución y recompílela.  \(En el IDE, elija **Compilar**, **Limpiar solución** y, a continuación, seleccione **Compilar**, **Recompilar solución**.\)