---
title: "Advertencia de las herramientas del vinculador LNK4197 | Microsoft Docs"
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
  - "LNK4197"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4197"
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4197
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se especificó la exportación 'nombredeexportación' varias veces; se usará la primera especificación  
  
 Se especificó una exportación de varias formas diferentes.  El vinculador usa la primera especificación y omite el resto.  
  
 Si se recompila la biblioteca en tiempo de ejecución de C, se puede omitir el mensaje.  
  
 Si se especifica una exportación exactamente de la misma forma varias veces, el vinculador no emite ninguna advertencia.  
  
 Por ejemplo, el contenido siguiente de un archivo .def provocaría esta advertencia:  
  
```  
EXPORTS  
   functioname      NONAME  
   functioname      @10  
```  
  
### Posibles causas del error:  
  
1.  Se especificó la misma exportación en la línea de comandos \(con export:\) y en el archivo .def  
  
2.  La misma exportación aparece dos veces en el archivo .def con diferentes atributos.