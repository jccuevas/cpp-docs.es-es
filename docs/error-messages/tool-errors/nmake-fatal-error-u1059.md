---
title: "Error grave de NMAKE U1059 | Microsoft Docs"
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
  - "U1059"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1059"
ms.assetid: b21d9198-9c63-40d0-b589-80e17294ce24
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error grave de NMAKE U1059
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : falta '}' en dependiente  
  
 Se ha especificado incorrectamente una ruta de acceso de búsqueda para un dependiente.  Existe un espacio en la ruta de acceso o se ha omitido la llave de cierre \(**}**\).  
  
 La sintaxis de la especificación de un directorio para un dependiente es  
  
 **{**   
 ***directories* }dependiente**  
  
 donde `directories` especifica una o más rutas de acceso, separadas entre sí por un punto y coma \(**;**\).  No se permiten espacios.  
  
 Si una parte o la totalidad de la ruta de acceso de una búsqueda se sustituye por una macro, asegúrese de que no existan espacios en la expansión de la macro.