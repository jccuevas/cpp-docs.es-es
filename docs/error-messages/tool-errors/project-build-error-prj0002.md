---
title: "Error PRJ0002 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0002"
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error PRJ0002 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

resultado del error devuelto desde 'línea de comandos'.  
  
 Un comando, ***línea de comandos***, formado a partir de los datos proporcionados por el usuario en el cuadro de diálogo **Páginas de propiedades**, devolvió un código de error, pero no se mostrará información en la Ventana de salida.  
  
 La solución de este error dependerá de la herramienta que lo generó.  Para MIDL, podrá averiguar qué pasó si define el modificador \/o \(Redirigir resultados\).  
  
 Un archivo de proceso por lotes \(como un paso de generación personalizada o un evento de compilación\) que no informe de las condiciones de error también podría ser la causa de este error.