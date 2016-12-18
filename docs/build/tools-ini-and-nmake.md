---
title: "Tools.ini y NMAKE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "NMAKE (programa), leer archivos"
  - "Tools.ini y NMake"
ms.assetid: ebd5eab6-ddf4-430e-bf4a-1db5bb84e344
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tools.ini y NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE lee Tools.ini antes de leer archivos MAKE, a menos que se utilice \/R.  Primero busca Tools.ini en el directorio actual y, a continuación, en el directorio especificado por la variable de entorno INIT.  La sección de configuración de NMAKE en el archivo de inicialización empieza por `[NMAKE]` y puede contener información acerca de archivos MAKE.  Un comentario se especifica en una línea independiente que empiece por un signo de número \(\#\).  
  
## Vea también  
 [Ejecutar NMAKE](../build/running-nmake.md)