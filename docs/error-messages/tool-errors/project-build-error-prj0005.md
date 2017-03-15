---
title: "Error PRJ0005 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0005"
ms.assetid: 00c1821b-16aa-4bd9-9cf6-a778e5ed4ad9
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error PRJ0005 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede crear un archivo temporal en el directorio 'nombre\_directorio'.  
  
 La llamada para crear un archivo temporal produjo un error.  Las razones posibles del error son:  
  
-   Se agotaron los nombres de archivo temporal disponibles.  
  
-   El directorio temp es de sólo lectura.  
  
-   No hay un directorio temp ni una variable de entorno TMP.  
  
-   El equipo no tiene espacio disponible en disco.