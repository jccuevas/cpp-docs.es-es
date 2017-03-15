---
title: "Error grave de NMAKE U1051 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "U1051"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1051"
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error grave de NMAKE U1051
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

memoria insuficiente  
  
 La memoria para NMAKE, incluida la memoria virtual, es insuficiente porque el archivo MAKE es demasiado grande o complejo.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Liberar algo de espacio en disco.  
  
2.  Aumentar el tamaño del archivo de paginación de Windows NT o del archivo de intercambio de Windows.  
  
3.  Si sólo se utiliza parte del archivo MAKE, divídalo en archivos distintos o utilice directivas de preprocesamiento **\!IF** para limitar la cantidad que debe procesar NMAKE.  Entre las directivas de preprocesamiento **\!IF** se encuentran las siguientes: **\!IF**, `!IFDEF`, **\!IFNDEF**, **\!ELSEIF**, **\!ELSE**`IFDEF` y **\!ELSE**`IFNDEF`.