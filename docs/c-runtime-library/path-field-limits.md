---
title: "L&#237;mites del campo de ruta de acceso | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_MAX_EXT"
  - "_MAX_DIR"
  - "_MAX_PATH"
  - "_MAX_FNAME"
  - "_MAX_DRIVE"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_MAX_DIR (constante)"
  - "_MAX_DRIVE (constante)"
  - "_MAX_EXT (constante)"
  - "_MAX_FNAME (constante)"
  - "_MAX_PATH (constante)"
  - "MAX_DIR (constante)"
  - "MAX_DRIVE (constante)"
  - "MAX_EXT (constante)"
  - "MAX_FNAME (constante)"
  - "constantes de campo de ruta de acceso"
  - "rutas de acceso, límite máximo"
ms.assetid: 2b5d0e43-1347-45b4-8397-24a8a45c444e
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# L&#237;mites del campo de ruta de acceso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
#include <stdlib.h>  
```  
  
## Comentarios  
 Estas constantes definen la longitud máxima de la ruta de acceso y de campos individuales dentro de la ruta.  
  
|Constante|Significado|  
|---------------|-----------------|  
|`_MAX_DIR`|Longitud máxima del componente de directorio|  
|`_MAX_DRIVE`|Longitud máxima del componente impulsor|  
|`_MAX_EXT`|Longitud máxima del componente de extensión|  
|`_MAX_FNAME`|Longitud máxima del componente de nombre de archivo|  
|`_MAX_PATH`|Longitud máxima de la ruta de acceso completa|  
  
> [!NOTE]
>  El tiempo de ejecución de C admite longitudes de rutas de acceso hasta 32768 caracteres de longitud, pero es el sistema operativo, específicamente el sistema de archivos, admitir estas rutas de acceso más larga.  La suma de los campos no debe superar `_MAX_PATH` para la compatibilidad total con sistemas de archivos del FAT32.  [!INCLUDE[win2kfamily](../c-runtime-library/includes/win2kfamily_md.md)], [!INCLUDE[WinXpFamily](../Token/winxpfamily_md.md)], [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)], y el sistema de archivos NTFS de Windows Vista admite las rutas de hasta 32768 caracteres, pero al utilizar Unicode API.  ¿Cuándo utilizar nombres de ruta largos, prefijo la ruta con el \\\\ de caracteres? el \\ y utiliza las versiones de Unicode de funciones en tiempo de ejecución de C.  
  
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)