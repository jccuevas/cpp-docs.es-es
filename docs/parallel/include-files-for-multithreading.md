---
title: "Archivos de inclusi&#243;n para el subprocesamiento m&#250;ltiple | Microsoft Docs"
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
  - "archivos de inclusión, multithreading"
  - "subprocesamiento múltiple [C++], archivos de inclusión"
  - "subprocesamiento [C++], archivos de inclusión"
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Archivos de inclusi&#243;n para el subprocesamiento m&#250;ltiple
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los archivos de inclusión estándar declaran las funciones de la biblioteca en tiempo de ejecución de C tal como se implementan en las bibliotecas.  Si utiliza las opciones de [Optimización completa](../build/reference/ox-full-optimization.md) \(\/Ox\) o de [convención de llamada fastcall](../build/reference/gd-gr-gv-gz-calling-convention.md) \(\/Gr\), el compilador supone que todas las llamadas a funciones se deben realizar mediante la convención de llamada de registro.  Las funciones de la biblioteca en tiempo de ejecución se compilaron con la convención de llamada de C; y son las declaraciones de los archivos de inclusión estándar las que indican al compilador que genere las referencias externas correctas para estas funciones.  
  
## Vea también  
 [Subprocesamiento múltiple con C y Win32](../parallel/multithreading-with-c-and-win32.md)