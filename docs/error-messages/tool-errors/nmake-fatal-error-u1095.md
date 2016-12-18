---
title: "Error grave de NMAKE U1095 | Microsoft Docs"
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
  - "U1095"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1095"
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error grave de NMAKE U1095
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la línea de comandos expandida 'líneadecomandos' es demasiado larga  
  
 Después de la expansión de macros, la línea de comandos dada supera el límite de longitud de las líneas de comandos para el sistema operativo.  
  
 MS\-DOS permite hasta 128 caracteres en una línea de comandos.  
  
 Si el comando es para un programa que puede aceptar entradas de línea de comandos desde un archivo, cambie el comando y proporcione la entrada desde un archivo de disco o un archivo en línea.  Por ejemplo, LINK y LIB aceptan la entrada desde un archivo de respuesta.