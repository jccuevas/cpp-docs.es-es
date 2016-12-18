---
title: "_amsg_exit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_amsg_exit"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_amsg_exit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_amsg_exit"
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
caps.latest.revision: 2
caps.handback.revision: 2
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _amsg_exit
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Emite un mensaje de error especificado en tiempo de ejecución y después cierra la aplicación con el código de error 255.  
  
## Sintaxis  
  
```cpp  
void _amsg_exit (  
   int rterrnum  
   )  
  
```  
  
#### Parámetros  
 `rterrnum`  
 El número de identificación de un mensaje de error sistema\- definido en tiempo de ejecución.  
  
## Comentarios  
 Esta función emite el mensaje de error de tiempo de ejecución a **stderr** para aplicaciones de consola, o bien el mensaje en un cuadro de mensaje para aplicaciones Windows.  En modo de depuración, puede elegir para invocar el depurador antes de salir.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|\_amsg\_exit|internal.h|