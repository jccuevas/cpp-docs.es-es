---
title: "Compilar proyectos de C++ en Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "compilaciones [C++], acerca de las compilaciones en Visual Studio"
  - "proyectos [C++], compilar"
  - "proyectos de Visual C++, compilar"
ms.assetid: 9e8bc1a2-bb17-4951-937a-c757ed88d2d1
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compilar proyectos de C++ en Visual Studio
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el entorno de desarrollo integrado \(IDE\) de Visual Studio, hay varias formas de compilar una solución completa o solo uno de sus proyectos.  También puede modificar la configuración de compilación y especificar pasos de compilación personalizada para que el proceso de desarrollo sea más eficiente.  
  
 Para compilar una solución que esté abierta en [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] y seleccionada en el **Explorador de soluciones**, puede hacer lo siguiente:  
  
-   En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
-   O bien, en el **Explorador de soluciones**, abra el menú contextual de la solución y, luego, elija **Compilar solución**.  
  
-   O bien, presione F7  \(es el método abreviado de teclado predeterminado de la configuración del desarrollo en C\/C\+\+\).  
  
-   O bien, en la [ventana Comandos](../Topic/Command%20Window.md) \(en la barra de menús, elija **Ver**, **Otras ventanas**, **Ventana Comandos**\), escriba `Build.BuildSolution`.  
  
-   O bien, en el cuadro [Inicio rápido](../Topic/Quick%20Launch,%20Environment,%20Options%20Dialog%20Box.md), escriba `build build solution`.  
  
 Para compilar un proyecto que esté seleccionado en el **Explorador de soluciones**, puede hacer lo siguiente:  
  
-   En la barra de menús, elija **Compilar**, **Compilar \<Nombre del proyecto\>**.  
  
-   O bien, en el **Explorador de soluciones**, abra el menú contextual del proyecto y, luego, elija **Compilar**.  
  
-   O bien, en la ventana Comandos \(en la barra de menús, elija **Ver**, **Otras ventanas**, **Ventana Comandos**\), escriba `Build.BuildOnlyProject`.  
  
-   O bien, en el cuadro Inicio rápido, escriba `build project only build only <nombre del proyecto>`.  
  
 Al compilar una aplicación de Visual C\+\+ en Visual Studio, puede modificar gran parte de la configuración de la compilación en el cuadro de diálogo Páginas de propiedades del proyecto.  Para obtener información sobre cómo establecer las propiedades del proyecto, consulte [Trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).  
  
 Para ver un ejemplo de cómo usar el IDE con el fin de crear, compilar y depurar un proyecto de C\+\+, consulte el [tutorial de exploración del IDE de Visual Studio con C\+\+](../Topic/Getting%20Started%20with%20C++%20in%20Visual%20Studio.md).  Para ver un ejemplo de cómo usar el IDE con el fin de compilar un proyecto de C\+\+\/CLR, consulte [Tutorial: Compilar un programa de C\+\+ orientado a CLR en Visual Studio](../ide/walkthrough-compiling-a-cpp-program-that-targets-the-clr-in-visual-studio.md).  Para ver un ejemplo de cómo usar el IDE para crear una aplicación de Windows en tiempo de ejecución, consulte el tema sobre [cómo crear su primera aplicación de Windows en tiempo de ejecución con C\+\+](http://msdn.microsoft.com/library/windows/apps/hh974580.aspx).  
  
 Para más información sobre cómo compilar, modificar la configuración de compilación y especificar pasos de compilación personalizada, consulte los siguientes artículos.  
  
## En esta sección  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)  
 Describe cómo personalizar el proceso de compilación en el entorno de desarrollo integrado.  
  
 [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)  
 Presenta una lista de macros que puede usar donde se aceptan cadenas.  
  
 [Compilar proyectos externos](../ide/building-external-projects.md)  
 Examina la compilación de proyectos que utilizan instalaciones de fuera del entorno de desarrollo integrado.  
  
 [Archivos de proyecto](../ide/project-files.md)  
 Presenta la estructura XML de un archivo .vcxproj.  
  
## Secciones relacionadas  
 [VC\+\+ Directories, Projects, Options Dialog Box](http://msdn.microsoft.com/es-es/e027448b-c811-4c3d-8531-4325ad3f6e02)  
 Explica cómo modificar la ruta de búsqueda de los archivos ejecutables e incluir archivos, archivos de biblioteca y archivos de código fuente durante una compilación.  
  
 [Compilar aplicaciones en Visual Studio](../Topic/Compiling%20and%20Building%20in%20Visual%20Studio.md)  
 Proporciona información sobre la compilación en Visual Studio.  
  
 [Compilar programas de C\/C\+\+](../build/building-c-cpp-programs.md)  
 Ofrece vínculos a temas en los que se describe la compilación de programas desde la línea de comandos o desde el entorno de desarrollo integrado de Visual Studio.  
  
 [Referencia de compilación de C\/C\+\+](../build/reference/c-cpp-building-reference.md)  
 Incluye vínculos a una introducción a la compilación de programas en C\+\+, opciones del compilador y el enlazador y herramientas de compilación adicionales.  
  
 [Actualizar proyectos desde versiones anteriores de Visual C\+\+](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
 Proporciona vínculos a temas en los que se abarcan los problemas de actualización de proyectos de Visual C\+\+ 6.0 y posteriores a Visual C\+\+ .NET.  
  
 [Porting and Upgrading Programs](http://msdn.microsoft.com/es-es/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)  
 Ofrece detalles sobre la migración de aplicaciones y examina los archivos Make.  
  
## Vea también  
 [Roadmap for Windows Store apps using C\+\+](http://msdn.microsoft.com/es-es/0b71e4a4-5d8a-4a20-b2ec-e40062675ec1)