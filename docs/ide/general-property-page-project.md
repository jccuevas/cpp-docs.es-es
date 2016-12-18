---
title: "P&#225;gina de propiedades General (Proyecto) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCConfiguration.IntermediateDirectory"
  - "VC.Project.VCConfiguration.ConfigurationType"
  - "VC.Project.VCConfiguration.ManagedExtensions"
  - "VC.Project.VCConfiguration.BuildBrowserInformation"
  - "VC.Project.VCConfiguration.BuildLogFile"
  - "VC.Project.VCConfiguration.PlatformToolset"
  - "VC.Project.VCConfiguration.TargetName"
  - "VC.Project.VCConfiguration."
  - "VC.Project.VCConfiguration.TargetExt"
  - "VC.Project.VCConfiguration.ATLMinimizesCRunTimeLibraryUsage"
  - "VC.Project.VCConfiguration.ReferencesPath"
  - "VC.Project.VCConfiguration.DeleteExtensionsOnClean"
  - "VC.Project.VCConfiguration.useOfMfc"
  - "VC.Project.VCConfiguration.CharacterSet"
  - "VC.Project.VCGeneralMakefileSettings.ConfigurationType"
  - "VC.Project.VCConfiguration.OutputDirectory"
  - "VC.Project.VCConfiguration.AppSupport"
  - "VC.Project.VCConfiguration.ToolFiles"
  - "VC.Project.VCConfiguration.useOfATL"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Limpiar (opción de Compilar)"
  - "archivos de salida, establecer directorio"
  - "Unicode, crear una configuración de compilación en C++"
ms.assetid: 593b383c-cd0f-4dcd-ad65-9ec9b4b19c45
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# P&#225;gina de propiedades General (Proyecto)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al hacer clic con el botón secundario en un nodo de proyecto en el Explorador de soluciones y seleccionar **Propiedades**, la página de propiedades **General** bajo el nodo **Propiedades de configuración** en el panel izquierdo muestra dos secciones de propiedades:  
  
-   General  
  
-   Valores predeterminados del proyecto  
  
## General  
 Las propiedades de la sección General afectan a la ubicación de los archivos que se crean en el proceso de compilación y a los archivos que se eliminarán cuando se seleccione la opción **Limpiar** \(menú **Compilar**\).  
  
 **Plataforma de destino**  
 Especifica la plataforma en la que se ejecutará el proyecto. Por ejemplo, Windows, Android o iOS. El valor **Windows 10** significa que el proyecto tiene como destino la Plataforma universal de Windows. Si quiere que el destino sean versiones anteriores de Windows, no se muestra la versión y el valor de este campo aparece simplemente como **Windows**. Este es un campo de solo lectura que se establece al crear un proyecto.  
  
 **Versión de la plataforma de destino**  
 Para la plataforma Windows, especifica la versión del Windows SDK con la que se compila el proyecto. En Windows, esta es la versión del Windows SDK.[!INCLUDE[vs_dev14](../ide/includes/vs_dev14_md.md)] se distribuye con el Windows SDK 8.1. Si instaló las [Herramientas para Windows 10](http://go.microsoft.com/fwlink/p/?LinkId=617631), todas las versiones de las herramientas que haya instalado se mostrarán en la lista desplegable.  
  
 Para establecer Windows 7 o Windows Vista como destino, use el valor **8.1**, ya que Windows SDK 8.1 es compatible con estas plataformas. Además, debe definir el valor adecuado para \_WIN32\_WINNT en targetver.h. Para Windows 7, es 0x0601. Vea [Modificar WINVER y \_WIN32\_WINNT](../porting/modifying-winver-and-win32-winnt.md).  
  
 Puede instalar el conjunto de herramientas de la plataforma v110\_xp incluido en [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] para usar la versión actual de [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] para compilar proyectos de Windows XP y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Para obtener información sobre cómo obtener y usar este conjunto de herramientas de la plataforma, consulte [Configurar 11 programas de C\+\+ para Windows XP](../build/configuring-programs-for-windows-xp.md). Para obtener información adicional sobre cómo cambiar el conjunto de herramientas de la plataforma, consulte [Cómo: Modificar versión de .NET Framework de destino y el conjunto de herramientas de la plataforma](../build/how-to-modify-the-target-framework-and-platform-toolset.md).  
  
 **Versión mínima de la plataforma Versión**  
 Especifica la versión más antigua de la plataforma en la que se puede ejecutar el proyecto. Esta propiedad solo aparece si el tipo de proyecto lo admite, como en el caso de proyectos universales de Windows. Si la aplicación puede aprovechar las características de una versión más reciente del SDK de Windows, pero todavía se puede ejecutar en versiones anteriores sin esas características, quizás el valor de estas dos propiedades podría ser diferente con alguna pérdida de funcionalidad. De ser así, el código debe comprobar la versión de la plataforma en la que se está ejecutando en tiempo de ejecución y no intentar usar características que no están disponibles en una versión anterior de la plataforma.  
  
 Tenga en cuenta que Visual C\+\+ no aplica esta opción. Se incluye para proporcionar consistencia con otros lenguajes, como C\# y JavaScript, y como una guía para cualquier persona que use su proyecto. Visual C\+\+ no generarán un error si usa una característica que no esté disponible en la versión mínima.  
  
 **Directorio de salida**  
 Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos de salida que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el vinculador, el bibliotecario o BSCMake.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>.  
  
 **Directorio intermedio**  
 Especifica el directorio en el que herramientas como el vinculador colocarán todos los archivos intermedios que se creen durante el proceso de compilación. Normalmente, esto incluye los resultados de herramientas como el compilador de C\/C\+\+, MIDL y el compilador de recursos.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>.  
  
 **Nombre de destino**  
 Especifica el nombre de archivo que este proyecto genera.  
  
 **Extensión de destino**  
 Especifica la extensión de nombre de archivo que este proyecto genera; por ejemplo, .exe o .dll.  
  
 **Extensiones para eliminar al limpiar**  
 La opción **Limpiar** \(menú **Compilar**\) elimina archivos del directorio intermedio en el que se compila la configuración de un proyecto. Se eliminarán los archivos que tengan las extensiones especificadas con esta propiedad cuando se ejecute **Limpiar** o cuando se recompile. Además de los archivos del directorio intermedio que tienen estas extensiones, el sistema de compilación también eliminará todos los resultados conocidos de la compilación independientemente de dónde se encuentren \(incluidos los resultados intermedios, como los archivos .obj\). Tenga en cuenta que puede especificar caracteres comodín.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>.  
  
 **Archivo de registro de compilación**  
 Permite especificar una ubicación no predeterminada para el archivo de registro que se crea cada vez que se compila un proyecto.  
  
 Puede utilizar macros de proyecto para cambiar la ubicación del directorio. Vea [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md).  
  
 **Conjunto de herramientas de la plataforma**  
 Permite al proyecto elegir como destino una versión diferente de las bibliotecas y el compilador de Visual C\+\+. Los proyectos de [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] pueden tener como destino el conjunto de herramientas predeterminado de [!INCLUDE[vs_dev11_long](../build/includes/vs_dev11_long_md.md)] \(**v100**\) o el conjunto de herramientas que crea archivos ejecutables que se pueden ejecutar en Windows XP.  
  
## Valores predeterminados del proyecto  
 Las propiedades de la sección Valores predeterminados del proyecto representan propiedades predeterminadas que puede modificar. La definición de estas propiedades se puede encontrar en los archivos .props que se encuentran en el *Directorio de instalación*\\VC\\VCProjectDefaults.  
  
 **Tipo de configuración**  
 Se puede elegir entre varios tipos de configuración diferentes:  
  
-   **Aplicación \(.exe\)**: muestra el conjunto de herramientas del vinculador \(Compilador de C\/C\+\+, MIDL, Compilador de recursos, Vinculador, BSCMake, Generador del proxy de Servicios Web XML; eventos personalizados de compilación, previos a la compilación, previos a la vinculación y posteriores a la compilación\).  
  
-   **Biblioteca dinámica \(.dll\)**: muestra el conjunto de herramientas del vinculador, especifica la opción \/DLL del vinculador y agrega la definición \_WINDLL a CL.  
  
-   **Archivo MAKE**: muestra el conjunto de herramientas para archivos MAKE \(NMake\).  
  
-   **Biblioteca estática \(.lib\)**: muestra el conjunto de herramientas de bibliotecario \(igual que el conjunto de herramientas del vinculador, con la diferencia de que incluye un bibliotecario en lugar de un vinculador y se omite el Generador del proxy de Servicios Web XML\).  
  
-   **Utilidad**: muestra el conjunto de herramientas de utilidades \(MIDL; eventos personalizados de compilación, previos a la compilación, previos a la vinculación y posteriores a la compilación\).  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.ConfigurationType%2A>.  
  
 **Uso de MFC**  
 Especifica si el proyecto MFC se vinculará de forma estática o dinámica al archivo DLL de MFC. En los proyectos que no están basados en MFC se puede seleccionar **Utilizar bibliotecas estándar de Windows** para vincularse a distintas bibliotecas Win32 que se incluyen cuando se utiliza MFC.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>.  
  
 **Uso de ATL**  
 Especifica si el proyecto ATL se vinculará de forma estática o dinámica al archivo .DLL de ATL. Si se especifica otra opción que no sea **No utilizar ATL**, se agregará una definición a la página de propiedades **Línea de comandos** del compilador.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfATL%2A>.  
  
 **Juego de caracteres**  
 Define si se debe establecer \_UNICODE o \_MBCS. También afecta al punto de entrada del vinculador cuando sea necesario.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>.  
  
 **Compatible con Common Language Runtime**  
 Hace que se utilice la opción [\/clr](../build/reference/clr-common-language-runtime-compilation.md) del compilador.  
  
 Para obtener acceso a esta propiedad mediante programación, vea <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>.  
  
 **Optimización de todo el programa**  
 Especifica la opción [\/GL](../build/reference/gl-whole-program-optimization.md) del compilador y la opción [\/LTCG](../build/reference/ltcg-link-time-code-generation.md) del vinculador.  
  
 **Compatibilidad con aplicaciones de la Tienda Windows**  
 Especifica si este proyecto admite aplicaciones de la [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]. Para obtener más información, consulte [\/ZW \(Compilación de Windows en tiempo de ejecución\)](../build/reference/zw-windows-runtime-compilation.md) y el Centro para desarrolladores de Windows.  
  
## Vea también  
 [Páginas de propiedades](../ide/property-pages-visual-cpp.md)