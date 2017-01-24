---
title: "Compilar proyectos externos | Microsoft Docs"
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
  - "compilaciones [C++], proyectos externos"
  - "proyectos externos"
  - "proyectos de archivos Make, proyectos externos"
  - "proyectos [C++], proyectos externos"
  - "proyectos de Visual C++, proyectos externos"
ms.assetid: 650b7803-ea91-489d-bee3-8f3e990e223c
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compilar proyectos externos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un proyecto externo es un proyecto de Visual C\+\+ que usa un archivo MAKE u otro medio externo o ajeno al entorno de desarrollo de Visual C\+\+.  
  
 Si desea generar un proyecto externo \(por ejemplo, un proyecto de archivos MAKE\) en el entorno de desarrollo de Visual C\+\+, cree un proyecto de archivos MAKE y, en el Asistente para aplicaciones de archivos MAKE, especifique el comando y el resultado de generación del proyecto.  Para obtener más información, vea [Crear un proyecto de archivos MAKE](../ide/creating-a-makefile-project.md).  
  
 Tenga en cuenta que Visual C\+\+ ya no admite la posibilidad de exportar desde el entorno de desarrollo un archivo MAKE para el proyecto activo.  Utilice [Modificadores de línea de comandos para Devenv](../Topic/Devenv%20Command%20Line%20Switches.md) para compilar proyectos de Visual Studio desde la línea de comandos.  
  
## Vea también  
 [Compilar proyectos de C\+\+ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)