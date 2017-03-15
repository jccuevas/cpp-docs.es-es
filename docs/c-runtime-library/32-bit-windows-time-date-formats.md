---
title: "Formatos de fecha y hora de Windows de 32 bits | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.time"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Windows de 32 bits"
ms.assetid: ef1589db-84d7-4b24-8799-7c7a22cfe2bf
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Formatos de fecha y hora de Windows de 32 bits
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La hora de archivo y la fecha se almacenan individualmente, mediante enteros sin signo como campos de bits.  Se empaquetan la hora y la fecha del archivo como sigue:  
  
### Time  
  
|Posición de bit:|0   1   2   3   4|5 6 7 8 9 A|F OF TABLE D E IZQUIERDA C OF TABLE B|  
|----------------------|-----------------------|-----------------|-------------------------------------------|  
|Longitud:|5|6|5|  
|Contenido:|hours|minutes|incrementos 2 second|  
|Intervalo de valores:|0–23|0–59|0\-29 en 2 segundos intervalos|  
  
### Date  
  
|Posición de bit:|0   1   2   3   4   5   6|7 8 9 A|F OF TABLE D E IZQUIERDA C OF TABLE B|  
|----------------------|-------------------------------|-------------|-------------------------------------------|  
|Longitud:|7|4|5|  
|Contenido:|año|mes|día|  
|Intervalo de valores:|0–119|1–12|1–31|  
||\(en relación con el an o 80\)|||  
  
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)