---
title: "Compilar aplicaciones aisladas de C/C++ | Microsoft Docs"
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
  - "aplicaciones aisladas [C++]"
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compilar aplicaciones aisladas de C/C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una aplicación aislada sólo depende de los ensamblados en paralelo y enlaza a sus dependencias mediante un manifiesto.  No es necesario que su aplicación esté aislada por completo para que se ejecute correctamente en Windows; sin embargo, si invierte en el aislamiento completo de la aplicación, podrá ahorrar tiempo en su mantenimiento en el futuro.  Para obtener más información sobre las ventajas de aislar totalmente la aplicación, vea [Isolated Applications \[Side\-by\-side Assemblies\]](http://msdn.microsoft.com/library/aa375190).  
  
 Al compilar la aplicación de C\/C\+\+ nativa mediante Visual C\+\+, el sistema de proyectos de Visual Studio genera de forma predeterminada un archivo de manifiesto en el que se describen las dependencias de la aplicación en las bibliotecas de Visual C\+\+.  Si estas son las únicas dependencias que tiene la aplicación, se convertirá en una aplicación aislada en cuanto se recompile con Visual Studio.  Si la aplicación utiliza otras bibliotecas en tiempo de ejecución, puede que tenga que recompilarlas como ensamblados en paralelo siguiendo los pasos descritos en [Compilar ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## Vea también  
 [Conceptos de aplicaciones aisladas y ensamblados simultáneos](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Compilar aplicaciones aisladas y ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)