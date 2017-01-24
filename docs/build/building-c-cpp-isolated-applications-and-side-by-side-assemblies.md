---
title: "Compilar aplicaciones aisladas y ensamblados simult&#225;neos de C/C++ | Microsoft Docs"
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
  - "WinSxS [C++]"
  - "caché de ensamblados nativo [C++]"
  - "compilaciones [C++], aplicaciones aisladas"
  - "aplicaciones simultáneas [C++]"
  - "compilaciones [C++], ensamblados en paralelo"
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compilar aplicaciones aisladas y ensamblados simult&#225;neos de C/C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ admite un modelo de implementación para aplicaciones cliente de Windows que se basa en la idea de las [aplicaciones aisladas](http://msdn.microsoft.com/library/aa375190) y los [ensamblados en paralelo](_win32_side_by_side_assemblies). De forma predeterminada, Visual C\+\+ compila todas las aplicaciones nativas de C\/C\+\+ como aplicaciones aisladas que usan [manifiestos](http://msdn.microsoft.com/library/aa375365) para describir sus dependencias en las bibliotecas de Visual C\+\+.  
  
 Compilar programas de C\/C\+\+ como aplicaciones aisladas presenta varias ventajas. Por ejemplo, a las aplicaciones aisladas no les afecta que otras aplicaciones de C\/C\+\+ instalen o desinstalen bibliotecas de Visual C\+\+. Las bibliotecas de Visual C\+\+ usadas por las aplicaciones aisladas, aun así, se pueden redistribuir en la carpeta local de la aplicación o instalándolas en la caché de ensamblados nativa \(WinSxS\). Sin embargo, el mantenimiento de las bibliotecas de Visual C\+\+ para las aplicaciones ya implementadas se puede simplificar con un [archivo de configuración del publicador](http://msdn.microsoft.com/library/aa375680). Con el modelo de implementación de aplicaciones aisladas, es más fácil que las aplicaciones de C\/C\+\+ que se ejecutan en un equipo determinado usen la última versión de las bibliotecas de Visual C\+\+ y, al mismo tiempo, se deja abierta la posibilidad de que los administradores del sistema y los autores de aplicaciones controlen el enlace explícito de versiones de las aplicaciones a las DLL dependientes.  
  
 En esta sección, se explica cómo compilar una aplicación de C\/C\+\+ como aplicación aislada y enlazarla a bibliotecas de Visual C\+\+ con un manifiesto. La información de esta sección se aplica, principalmente, a las aplicaciones de Visual C\+\+ nativas o no administradas. Para obtener información sobre la implementación de aplicaciones nativas compiladas con Visual C\+\+, vea [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md).  
  
## En esta sección  
 [Conceptos de aplicaciones aisladas y ensamblados simultáneos](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)  
  
 [Compilar aplicaciones aisladas de C\/C\+\+](../build/building-c-cpp-isolated-applications.md)  
  
 [Compilar ensamblados simultáneos de C\/C\+\+](../build/building-c-cpp-side-by-side-assemblies.md)  
  
 [Cómo: Crear componentes COM de registro gratuito](../build/how-to-build-registration-free-com-components.md)  
  
 [Cómo: Compilar aplicaciones aisladas que utilicen componentes COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
 [Introducción a la generación de manifiestos para los programas de C\/C\+\+](../build/understanding-manifest-generation-for-c-cpp-programs.md)  
  
 [Solución de problemas](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
## Secciones relacionadas  
 [Aplicaciones aisladas y ensamblados en paralelo](http://msdn.microsoft.com/library/dd408052)  
  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)