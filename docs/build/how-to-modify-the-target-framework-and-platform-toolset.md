---
title: "C&#243;mo: Modificar versi&#243;n de .NET Framework de destino y el conjunto de herramientas de la plataforma | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
f1_keywords: 
  - "msbuild.cpp.howto.modifytargetframeworkandplatformtoolset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (C++), cómo: modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma"
ms.assetid: 031b1d54-e6e1-4da7-9868-3e75a87d9ffe
caps.latest.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 32
---
# C&#243;mo: Modificar versi&#243;n de .NET Framework de destino y el conjunto de herramientas de la plataforma
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede cambiar la configuración del proyecto de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] a distintas versiones de destino de .NET Framework y utilizar diferentes conjuntos de herramientas de la plataforma. De forma predeterminada, el sistema de proyectos utiliza la versión de .NET Framework y la versión del conjunto de herramientas que corresponden a la versión de Visual Studio que se utiliza para crear el proyecto. Puede cambiar el conjunto de herramientas de la plataforma de destino modificando las propiedades del proyecto. Puede cambiar la versión de .Net Framework de destino modificando el archivo de proyecto \(.vcxproj\). No tiene que mantener una base de código independiente para cada destino de compilación.  
  
> [!IMPORTANT]
>  Es posible que algunas ediciones no admitan versiones de .NET Framework de destino o conjuntos de herramientas de plataformas modificados. Para obtener información de compatibilidad, vea [Portar, migrar y actualizar proyectos de Visual Studio](../Topic/Porting,%20Migrating,%20and%20Upgrading%20Visual%20Studio%20Projects.md).  
  
 Cuando se cambia la versión de .Net Framework de destino, también cambia el conjunto de herramientas de la plataforma a una versión que admite la versión de .Net Framework de destino. Por ejemplo, para definir como destino .NET Framework 4.5, debe utilizar un conjunto de herramientas de plataforma compatible, tal como Visual Studio 2015 \(v140\), Visual Studio 2013 \(v120\) o Visual Studio 2012 \(v110\). Puede utilizar el conjunto de herramientas de la plataforma **Windows7.1SDK** para las plataformas .NET Framework 2.0, 3.0, 3.5 y 4, así como x86, Itanium y x64.  
  
> [!NOTE]
>  Para cambiar el conjunto de herramientas de la plataforma de destino, debe tener la versión asociada de Visual Studio o Windows Platform SDK instalado. Por ejemplo, para definir como destino la plataforma Itanium con el conjunto de herramientas de la plataforma de **Windows7.1SDK**, debe tener instalado [Microsoft Windows SDK para Windows 7 y .NET Framework 4 SP1](http://www.microsoft.com/download/details.aspx?id=8279); sin embargo, podría utilizar otra versión compatible de Visual Studio para realizar el trabajo de desarrollo, siempre que el destino sea el conjunto de herramientas correcto de versión y plataforma de .NET Framework.  
  
 Puede extender la plataforma de destino aún más creando un conjunto de herramientas personalizado de la plataforma. Para obtener más información, vea [C\+\+ Native Multi\-Targeting](http://go.microsoft.com/fwlink/?LinkId=196619) en el blog de Visual C\+\+.  
  
### Para cambiar la versión de .NET Framework de destino  
  
1.  En Visual Studio, en el **Explorador de soluciones**, seleccione el proyecto. En la barra de menús, abra el menú **Proyecto** y elija **Descargar el proyecto**. Esto descarga el archivo de proyecto \(.vcxproj\) para el proyecto.  
  
    > [!NOTE]
    >  Un proyecto de C\+\+ no se puede cargar mientras el archivo de proyecto se está modificando en Visual Studio. Sin embargo, puede utilizar otro editor como Bloc de notas para modificar el archivo de proyecto mientras se carga el proyecto en Visual Studio. Visual Studio detecta que el archivo de proyecto ha cambiado y pide que se recargue el proyecto.  
  
2.  En la barra de menús, seleccione **Archivo**, **Abrir**, **Archivo**. En el cuadro de diálogo **Abrir archivo**, navegue a la carpeta de proyecto y vuelva a abrir el archivo de proyecto \(.vcxproj\).  
  
3.  En el archivo de proyecto, busque la entrada para la versión de .Net Framework de destino. Por ejemplo, si se ha diseñado el proyecto para usar .NET Framework 4.5, busque `<TargetFrameworkVersion>v4.5</TargetFrameworkVersion>` en el elemento `<PropertyGroup Label="Globals">` del elemento `<Project>`. Si el elemento `<TargetFrameworkVersion>` no está presente, el proyecto no usa .NET Framework y no se requiere ningún cambio.  
  
4.  Cambie el valor a la versión de Framework que desee, como v3.5 o v4.6.  
  
5.  Guarde los cambios y cierre el editor.  
  
6.  En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Volver a cargar el proyecto**.  
  
7.  Para comprobar el cambio, en el **Explorador de soluciones**, haga clic con el botón derecho para abrir el menú contextual del proyecto \(no de la solución\) y, luego, elija **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades** del proyecto. En el panel de la izquierda del cuadro de diálogo, expanda **Propiedades de configuración** y, a continuación, seleccione **General**. Compruebe que **Versión de .NET Target Framework** muestre la nueva versión de Framework.  
  
### Para cambiar el conjunto de herramientas del proyecto  
  
1.  En Visual Studio, en el **Explorador de soluciones**, abra el menú contextual del proyecto \(no de la solución\) y, luego, elija **Propiedades** para abrir el cuadro de diálogo **Páginas de propiedades** del proyecto.  
  
2.  En el cuadro de diálogo **Páginas de propiedades**, abra la lista desplegable **Configuración** y seleccione **Todas las configuraciones**.  
  
3.  En el panel de la izquierda del cuadro de diálogo, expanda **Propiedades de configuración** y, a continuación, seleccione **General**.  
  
4.  En el panel de la derecha, seleccione **Conjunto de herramientas de la plataforma** y, a continuación, seleccione el conjunto de herramientas que desee en la lista desplegable. Por ejemplo, si instaló el conjunto de herramientas [!INCLUDE[vs_dev10_long](../build/includes/vs_dev10_long_md.md)], seleccione **Visual Studio 2010 \(v100\)** para usarlo para el proyecto.  
  
5.  Elija el botón **Aceptar**.  
  
## Vea también  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)