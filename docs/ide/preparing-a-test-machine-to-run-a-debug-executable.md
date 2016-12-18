---
title: "Preparar un equipo de pruebas para ejecutar un archivo ejecutable de depuraci&#243;n | Microsoft Docs"
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
  - "archivo ejecutable de depuración, preparar un equipo de pruebas para ejecutar"
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Preparar un equipo de pruebas para ejecutar un archivo ejecutable de depuraci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para preparar un equipo con el fin de probar la versión de depuración de una aplicación compilada con Visual C\+\+, tiene que implementar versiones de depuración de los archivos DLL de biblioteca de Visual C\+\+ de los que depende la aplicación.  Para identificar qué archivos DLL deben implementarse, siga los pasos descritos en [Descripción de las dependencias de una aplicación de Visual C\+\+](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).  Normalmente, las versiones de depuración de los archivos DLL de biblioteca de Visual C\+\+ tienen nombres que terminan en "d"; por ejemplo, la versión de depuración del archivo msvcr100.dll se denomina msvcr100d.dll.  
  
> [!NOTE]
>  Las versiones de depuración de una aplicación no son redistribuibles, como tampoco lo son las correspondientes a los archivos DLL de biblioteca de Visual C\+\+.  Puede implementar versiones de depuración de las aplicaciones y los archivos DLL de Visual C\+\+ solo en otros equipos de su propiedad, con el único propósito de depurar y probar las aplicaciones en un equipo que no tiene Visual Studio instalado.  Para obtener más información, vea [Redistribuir archivos de Visual C\+\+](../ide/redistributing-visual-cpp-files.md).  
  
 Hay tres maneras de implementar versiones de depuración de archivos DLL de biblioteca de Visual C\+\+ junto con la versión de depuración de una aplicación.  
  
-   Utilice la implementación central para instalar una versión de depuración de un archivo DLL de Visual C\+\+ determinado en el directorio %windir%\\system32\\ mediante un proyecto de instalación que incluya módulos de combinación para la versión de biblioteca y la arquitectura de la aplicación correctas.  Los módulos de combinación se encuentran en el directorio Archivos de programa o Archivos de programa \(x86\), en \\Common Files\\Merge Modules\\.  La versión de depuración de un módulo de combinación contiene Debug en el nombre; por ejemplo, Microsoft\_VC110 \_DebugCRT\_x86.msm.  Puede encontrar un ejemplo de esta implementación en [Tutorial: Implementar una aplicación de Visual C\+\+ mediante un proyecto de instalación](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).  
  
-   Utilice la implementación local para instalar una versión de depuración de un archivo DLL de Visual C\+\+ determinado en el directorio de instalación de la aplicación usando los archivos que se proporcionan en el directorio Archivos de programa o Archivos de programa \(x86\), en \\Microsoft Visual Studio \<versión\>\\VC\\redist\\Debug\_NonRedist\\.  
  
    > [!NOTE]
    >  Para realizar la depuración remota de una aplicación compilada mediante Visual C\+\+ 2005 o Visual C\+\+ 2008 en otro equipo, tiene que implementar versiones de depuración de los archivos DLL de biblioteca de Visual C\+\+ como ensamblados en paralelo compartidos.  Puede utilizar un proyecto de instalación o Windows Installer para instalar los módulos de combinación correspondientes.  
  
-   Utilice la opción **Implementar** del cuadro de diálogo **Administrador de configuración** de Visual Studio para copiar el resultado del proyecto y otros archivos al equipo remoto.  Puede encontrar un ejemplo de esta implementación en [Configurar la depuración remota en un proyecto de Visual Studio](../Topic/Set%20Up%20Remote%20Debugging%20for%20a%20Visual%20Studio%20Project.md).  
  
 Una vez instalados los archivos DLL de Visual C\+\+, puede ejecutar un depurador remoto en un recurso compartido de red.  Para obtener más información acerca de la depuración remota, vea [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
## Vea también  
 [Configurar las herramientas remotas en el dispositivo](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)   
 [Implementación en Visual C\+\+](../ide/deployment-in-visual-cpp.md)   
 [Opciones de la línea de comandos de Windows Installer](http://msdn.microsoft.com/library/windows/desktop/aa367988.aspx)   
 [Ejemplos de implementación](../ide/deployment-examples.md)