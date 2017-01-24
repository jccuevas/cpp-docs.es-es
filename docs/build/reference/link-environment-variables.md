---
title: "Variables de entorno de LINK | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "link"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "variables de entorno [C++], LINK"
  - "LIB (variable de entorno)"
  - "LINK (herramienta) [C++], variables de entorno"
  - "variables, entorno"
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Variables de entorno de LINK
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La herramienta LINK usa las variables de entorno siguientes:  
  
-   LINK y \_LINK\_, si se definen.  La herramienta LINK antepone las opciones y los argumentos definidos en la variable de entorno LINK, y anexa las opciones y los argumentos definidos en la variable de entorno \_LINK\_ a los argumentos de la línea de comandos antes del procesamiento.  
  
-   LIB, si se define.  La herramienta LINK usa la ruta de acceso de LIB para buscar un objeto, una biblioteca u otro archivo especificado en la línea de comandos o mediante la opción [\/BASE](../../build/reference/base-base-address.md).  También usa esta ruta para buscar un archivo .pdb denominado en un objeto.  La variable LIB puede contener una o varias especificaciones de ruta de acceso, separadas por punto y coma.  Una ruta de acceso debe apuntar al subdirectorio \\lib de la instalación de Visual C\+\+.  
  
-   PATH, si la herramienta debe ejecutar CVTRES y no encuentra el archivo en el mismo directorio de la propia LINK.  \(LINK requiere CVTRES para vincular un archivo. res\). PATH debe apuntar al subdirectorio \\bin de la instalación de Visual C\+\+.  
  
-   TMP, para especificar un directorio al vincular archivos .res u OMF.  
  
## Vea también  
 [Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)   
 [Establecer la ruta de acceso y las variables de entorno para compilar desde la línea de comandos](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)