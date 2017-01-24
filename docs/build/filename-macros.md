---
title: "Macros de nombre de archivo | Microsoft Docs"
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
  - "macros de nombre de archivo de NMAKE"
  - "macros, NMAKE"
  - "NMAKE (programa), macros de nombre de archivo"
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Macros de nombre de archivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las macros de nombre de archivo están predefinidas como nombres de archivos especificados en la dependencia \(no los nombres de archivos completos especificados en el disco\).  No es necesario encerrar estas macros entre paréntesis cuando se les llama; basta con especificar el signo $, como se muestra.  
  
|Macro|Significado|  
|-----------|-----------------|  
|**$@**|Nombre completo del destino actual \(ruta de acceso, nombre base, extensión\), como se especifica actualmente.|  
|**$$@**|Nombre completo del destino actual \(ruta de acceso, nombre base, extensión\), como se especifica actualmente.  Sólo tiene validez como un dependiente en una dependencia.|  
|**$\***|Ruta de acceso y nombre base sin extensión de archivo del destino actual.|  
|**$\*\***|Todos los dependientes del destino actual.|  
|**$?**|Todos los dependientes con una marca de tiempo posterior al destino actual.|  
|**$\<**|Archivo dependiente con una marca de tiempo posterior al destino actual.  Sólo tiene validez en comandos en reglas de inferencia.|  
  
 Para especificar parte de una macro de nombre de archivo predefinida, se anexa un modificador de macro y se encierra entre paréntesis la macro modificada.  
  
|Modificador|Parte de nombre de archivo resultante|  
|-----------------|-------------------------------------------|  
|**L**|Unidad más directorio|  
|**B**|Nombre base|  
|**F**|Nombre base más extensión|  
|**R**|Unidad más directorio más nombre base|  
  
## Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)