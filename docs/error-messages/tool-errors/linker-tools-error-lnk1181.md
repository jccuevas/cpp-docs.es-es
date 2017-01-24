---
title: "Error de las herramientas del vinculador LNK1181 | Microsoft Docs"
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
  - "LNK1181"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1181"
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1181
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede abrir el archivo de entrada 'nombredearchivo'  
  
 El vinculador no encontró `filename` porque no existe, o no se halló la ruta de acceso.  
  
 Entre algunas de las causas comunes del error LNK1181 se incluyen las siguientes:  
  
-   Se ha hecho referencia a `filename` como una dependencia adicional en la línea del vinculador, pero el archivo no existe.  
  
-   Falta una instrucción **\/LIBPATH** que especifica el directorio que contiene `filename`.  
  
 Para resolver los problemas anteriores, asegúrese de que todos los archivos a los que se haya hecho referencia en la línea del vinculador están presentes en el sistema.  Asegúrese también de que haya una instrucción **\/LIBPATH** para cada directorio que contenga un archivo dependiente del vinculador.  
  
 Otra de las causas posibles del error LNK1181 es no haber colocado entre comillas un nombre largo de archivo con espacios incrustados.  En ese caso, el vinculador sólo reconoce un nombre de archivo hasta el primer espacio y luego supone una extensión de archivo de .obj.  La solución a esta situación es colocar el nombre largo de archivo \(ruta de acceso más nombre de archivo\) entre comillas.  
  
 Para obtener más información, vea [Archivos .lib como entrada del vinculador](../../build/reference/dot-lib-files-as-linker-input.md).  
  
## Vea también  
 [\/LIBPATH \(Directorios de bibliotecas adicionales\)](../../build/reference/libpath-additional-libpath.md)