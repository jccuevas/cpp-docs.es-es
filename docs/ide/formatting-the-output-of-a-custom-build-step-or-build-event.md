---
title: "Dar formato a la presentaci&#243;n de un paso de compilaci&#243;n personalizada o un evento de compilaci&#243;n | Microsoft Docs"
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
  - "eventos de compilación [C++], formato de resultados"
  - "pasos de compilación [C++], formato de resultados"
  - "compilaciones [C++], eventos de compilación"
  - "compilaciones [C++], pasos de compilación personalizada"
  - "pasos de compilación personalizada [C++], formato de resultados"
  - "eventos [C++], build"
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Dar formato a la presentaci&#243;n de un paso de compilaci&#243;n personalizada o un evento de compilaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si el resultado de un evento de compilación o de un paso de generación personalizada recibe el formato correcto, los usuarios obtienen los siguientes beneficios:  
  
-   El recuento de advertencias y errores aparece en la **Ventana de salida**.  
  
-   Los resultados aparecen en la ventana **Lista de tareas**.  
  
-   Al hacer clic en el resultado de la **Ventana de salida**, se muestra el tema apropiado.  
  
-   Las operaciones con F1 están habilitadas tanto en la ventana **Lista de tareas** como en la **Ventana de salida**.  
  
 El formato del resultado sería el siguiente:  
  
 {*filename* \(*line\#* \[, *column\#*\]\) &#124; *toolname*} **:**  
  
 \[*any text*\] {**error** &#124; **warning**} *code\#\#\#\#***:** *localizable string*  
  
 \[ *any text* \]  
  
 Donde:  
  
-   {*a* &#124; *b*} es una opción de *a* o de *b*.  
  
-   \[`ccc`\] es un parámetro o cadena opcional.  
  
 Por ejemplo:  
  
 C: \\*sourcefile.cpp*\(134\): error C2143: error de sintaxis: falta “; ” antes de “}”  
  
 VÍNCULO: error irrecuperable LNK1104: no se puede abrir el archivo abierto '*somelib.lib*'  
  
## Vea también  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)