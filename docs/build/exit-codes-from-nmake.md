---
title: "C&#243;digos de salida de NMAKE | Microsoft Docs"
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
  - "códigos de salida"
  - "NMAKE (programa), códigos de salida"
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C&#243;digos de salida de NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

NMAKE devuelve los siguientes códigos de salida:  
  
|Código|Significado|  
|------------|-----------------|  
|0|Ningún error \(posiblemente una advertencia\).|  
|1|Compilación incompleta \(sólo se emite cuando se utiliza \/K\).|  
|2|Error del programa, debido posiblemente a una de las siguientes causas:|  
||-   Error de sintaxis en el archivo MAKE.|  
||-   Código de error o de salida de un comando.|  
||-   Interrupción por parte del usuario.|  
|4|Error del sistema: memoria insuficiente.|  
|255|El destino no está actualizado \(sólo se emite cuando se utiliza \/Q\).|  
  
## Vea también  
 [Ejecutar NMAKE](../build/running-nmake.md)