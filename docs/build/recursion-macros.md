---
title: "Macros de recursividad | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "macros, recursividad"
  - "NMAKE (programa), macros de recursividad"
  - "macros de recursividad"
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Macros de recursividad
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las macros de recursividad se utilizan para llamar a NMAKE de forma recursiva.  Las sesiones recursivas heredan macros de línea de comandos y de variables de entorno e información de Tools.ini.  No heredan reglas de inferencia definidas por el archivo MAKE ni especificaciones **.SUFFIXES** y **.PRECIOUS**.  Para pasar macros a una sesión de NMAKE recursiva, se establece una variable de entorno con SET antes de la llamada recursiva, se define una macro en el comando para la llamada recursiva, o se define una macro en Tools.ini.  
  
|Macro|Definición|  
|-----------|----------------|  
|**MAKE**|Comando usado originalmente para llamar a NMAKE.<br /><br /> La macro $\(MAKE\) proporciona la ruta de acceso completa a nmake.exe.|  
|**MAKEDIR**|Directorio actual cuando se llamó a NMAKE.|  
|**MAKEFLAGS**|Opciones actualmente en vigor.  Utilice como `/$(MAKEFLAGS)`.  Tenga en cuenta que \/F no se incluye.|  
  
## Vea también  
 [Macros NMAKE especiales](../build/special-nmake-macros.md)