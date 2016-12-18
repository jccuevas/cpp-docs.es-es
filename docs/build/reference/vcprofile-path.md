---
title: "VCPROFILE_PATH | Microsoft Docs"
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
  - "VCPROFILE_PATH"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VCPROFILE_PATH (variable de entorno)"
ms.assetid: 25217aa4-7e86-4eba-854d-10b3c457e4df
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# VCPROFILE_PATH
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el directorio para crear archivos .pgc.  
  
## Sintaxis  
  
```  
VCPROFILE_PATH=path  
```  
  
#### Parámetros  
 `path`  
 Ruta de acceso al directorio donde se agregarán los archivos .pgc.  
  
## Comentarios  
 De forma predeterminada, los archivos .pgc se crean en el mismo directorio que el binario a partir del que se generan perfiles.  Sin embargo, si la ruta de acceso absoluta al binario no existe, como ocurre cuando se ejecutan escenarios de perfiles en equipos distintos al equipo donde se creó el binario, `VCPROFILE_PATH` puede establecerse en una ruta de acceso existente.  
  
## Ejemplo  
  
```  
set VCPROFILE_PATH=c:\  
```  
  
## Vea también  
 [Variables de entrono para las optimizaciones guiadas por perfiles](../../build/reference/environment-variables-for-profile-guided-optimizations.md)