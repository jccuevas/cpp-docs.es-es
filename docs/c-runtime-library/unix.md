---
title: "UNIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "unix"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "compatibilidad con POSIX"
  - "nombres de archivo POSIX"
  - "UNIX"
  - "UNIX, compatibilidad"
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# UNIX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si piensa migrar los programas a UNIX, siga estas instrucciones:  
  
-   No quite los archivos de encabezado del subdirectorio de SYS.  Puede colocar los archivos de encabezado de SYS en otra parte sólo si no piensa llevar los programas a UNIX.  
  
-   Utilice el delimitador de la ruta de UNIX\- compatible de rutinas que toman cadenas que representan las rutas y los nombres de archivo como argumentos.  UNIX sólo admite la barra diagonal \(\/\) con este fin, mientras que los sistemas operativos de Win32 admiten la barra diagonal inversa \(\\\) y la barra diagonal \(\/\).  Así esta documentación se usa barras diagonales de UNIX\- compatible como delimitadores de ruta en las instrucciones de `#include` , por ejemplo. \(Sin embargo, el shell de comandos del sistema operativo Windows, CMD.EXE, no admite la barra diagonal en los comandos asociados en el símbolo del sistema\).  
  
-   Utilice las rutas y los nombres de archivo que funcionan correctamente en UNIX, que distingue entre mayúsculas y minúsculas.  El sistema de archivos de \(FAT\) de la tabla de asignación de archivos en sistemas operativos de Win32 no distingue entre mayúsculas y minúsculas; el sistema de archivos NTFS conserva el caso de las listas de directorios pero omite el caso en busca de archivos y otras operaciones del sistema.  
  
    > [!NOTE]
    >  En esta versión de Visual C\+\+, información sobre compatibilidad de UNIX se ha quitado de descripciones de la función.  
  
## Vea también  
 [Compatibilidad](../c-runtime-library/compatibility.md)