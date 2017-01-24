---
title: "Gu&#237;a de migraci&#243;n y actualizaci&#243;n de Visual C++ | Microsoft Docs"
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
ms.assetid: f5fbcc3d-aa72-41a6-ad9a-a706af2166fb
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gu&#237;a de migraci&#243;n y actualizaci&#243;n de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema proporciona a una guía para actualizar código de Visual C\+\+.  Esto incluye lograr que el código se compile y ejecute correctamente en una versión más reciente de las herramientas, así como sacar partido de las nuevas funciones de Visual Studio y del lenguaje.  En este tema también se incluye información acerca de la migración de aplicaciones heredadas a plataformas más modernas.  
  
## Motivos para actualizar código de Visual C\+\+  
 Debería considerar la posibilidad de actualizar el código por los siguientes motivos:  
  
-   El código es más rápido debido a unas mejores optimizaciones del compilador.  
  
-   El proceso de compilación es más rápido debido a las mejoras de rendimiento del propio compilador.  
  
-   Características del lenguaje.  Ahora Visual C\+\+ implementa muchas características de los estándares más recientes de C\+\+.  
  
-   Mejor seguridad.  Características de seguridad, como la comprobación de protección.  
  
### Migrar el código  
 Al actualizar, considere los proyectos y el código de la aplicación.  ¿La aplicación se compila con Visual Studio?  De ser así, identifique los proyectos implicados.  ¿Dispone de scripts de compilación personalizada?  Si en lugar de utilizar el sistema de compilación de Visual Studio, usa scripts de compilación personalizada, le costará más trabajo realizar la actualización porque no podrá disfrutar del ahorro de tiempo que supone que Visual Studio actualice sus archivos de proyecto y configuración de compilación.  
  
 El formato de archivos de proyecto y el sistema de compilación cambió en Visual Studio de vcbuild \(hasta Visual Studio 2008\) a MSBuild \(a partir de Visual Studio 2010\) .  Si su actualización es de una versión anterior a 2010 y tiene un sistema de compilación altamente personalizado, puede que tenga que realizar más trabajo para llevar a cabo la actualización.  Si está actualizando desde Visual Studio 2010 o posterior, sus proyectos ya utilizan MSBuild, por lo que debería será más fácil actualizar el proyecto y la compilación de la aplicación.  
  
 Si no utiliza el sistema de compilación de Visual Studio, debería considerar la posibilidad de llevar a cabo la actualización para que utilice MSBuild.  Si lo hace, puede que le resulte más sencillo actualizar en el futuro y utilizar servicios como Visual Studio Online.  MSBuild es compatible con todas las plataformas de destino que admite Visual Studio.  
  
### Migrar proyectos de Visual Studio  
 En el caso de proyectos grandes, puede que sea mejor actualizar las versiones de Visual Studio de una en una, porque, de lo contrario, puede ser difícil determinar qué versión introdujo un cambio problemático que haya afectado al código.  
  
 Para empezar a actualizar un proyecto o una solución, solo tiene que abrir la solución en la nueva versión de Visual Studio y seguir las indicaciones para iniciar la actualización.  Al actualizar un proyecto, obtendrá un informe de actualización, que también se guarda en la carpeta del proyecto como UpgradeLog.htm.  El informe de actualización muestra un resumen de los problemas encontrados durante el proceso de actualización y cierta información sobre los cambios realizados o los problemas que no se pudieron resolver automáticamente.  
  
1.  Propiedades del proyecto  
  
2.  Archivos de inclusión  
  
3.  Código que ya no se compila correctamente debido a cambios de conformidad del compilador.  
  
4.  Código que se basa en características de Windows o Visual Studio que ya no están disponibles o archivos de encabezado que no se incluyen en una instalación predeterminada de Visual Studio o que se han quitado del producto.  
  
5.  Código que ya no se compila debido a cambios en las API, como las API cuyo nombre se ha cambiado, firmas de función cambiadas o funciones en desuso.  
  
6.  Código que ya no se compila debido a cambios en los diagnósticos, como una advertencia que se convierte en un error.  
  
7.  Errores del vinculador debidos a bibliotecas que se cambiaron, especialmente cuando se utiliza \/NODEFAULTLIB.  
  
8.  Errores en tiempo de ejecución o resultados inesperados debidos a cambios de comportamiento.  
  
9. Errores debidos a errores que se introdujeron en las herramientas.  Si encuentra un problema, informe al equipo de Visual C\+\+ a través de los canales de soporte normales o mediante el [Centro de comentarios de Visual Studio](http://connect.microsoft.com/VisualStudio/Feedback).  
  
 Además de los cambios que no puede evitar debido a errores del compilador, algunos cambios son opcionales en un proceso de actualización, como:  
  
1.  Nuevas advertencias podrían significar que debería limpiar el código.  Dependiendo de los diagnósticos específicos, esto puede mejorar la portabilidad, el cumplimiento de estándares y la seguridad del código.  
  
2.  Puede que le convenga aprovechar las nuevas características del compilador, como la opción del compilador [\/guard:cf \(Habilitar protección de flujo de control\)](../build/reference/guard-enable-control-flow-guard.md), que agrega comprobaciones de ejecución de código no autorizado.  
  
3.  Puede que le interese actualizar una parte del código para que use las nuevas características del lenguaje que permiten simplifican el código, mejorar el rendimiento de sus programas o actualizar el código para que utilice bibliotecas modernas y cumpla con los estándares modernos y los procedimientos recomendados.  
  
 Una vez que haya actualizado su proyecto \(y lo haya probado\), puede que le interese considerar la posibilidad de mejorar más el código o planear el rumbo que debe tomar el código, o incluso reconsiderar la arquitectura de su proyecto.  ¿Será importante que su código se pueda ejecutar en otras plataformas?  De ser así, ¿en qué plataformas?  C\+\+ es un lenguaje estandarizado diseñado en torno a los conceptos de portabilidad y desarrollo multiplataforma, y aun así, el código de muchas aplicaciones de Windows está estrechamente ligado a la plataforma Windows.  ¿Desea refactorizar el código para separar las partes más ligadas a la plataforma de Windows?  
  
 ¿Y qué sucede con la interfaz de usuario?  Si está utilizando MFC, puede que le interese actualizar la interfaz de usuario.  ¿Está utilizando alguna de las nuevas características de MFC introducidas en 2008 como un Feature Pack?  Si lo único que quiere es que su aplicación tenga un nuevo aspecto, sin tener que volver a escribir toda la aplicación, debería considerar las API de cinta de opciones en MFC o usar algunas de las nuevas características de MFC.  
  
 Para agregar una nueva interfaz de usuario de escritorio de Windows, podría utilizar C\+\+\/CX \(extensiones de componentes\) o agregar código administrado en C\# y una capa de interoperabilidad en C\+\+\/CLI para conectar C\# con su código nativo.  
  
 Por otro lado, quizás ahora tiene nuevos requisitos o puede prever la necesidad de enfocarse a otras plataformas que no sean el escritorio de Windows, como Windows Phone o los dispositivos Android.  Podía migrar el código de la interfaz de usuario a una biblioteca de interfaz de usuario multiplataforma.  Con estos marcos de interfaz de usuario puede desarrollar aplicaciones para varios dispositivos y seguir utilizando Visual Studio y el depurador de Visual Studio como entorno de desarrollo.  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Actualizar proyectos desde versiones anteriores de Visual C\+\+](../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md)|Explica cómo utilizar los proyectos creados en versiones anteriores de Visual C\+\+.|  
|[Cambios importantes en Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md)|Una lista de los cambios en las herramientas de compilación y las bibliotecas de Visual C\+\+ que podrían precisar de modificaciones en su código.|  
|[Migración y actualización: ejemplos y casos prácticos](../porting/porting-and-upgrading-examples-and-case-studies.md)|En esta sección migramos y actualizamos varios ejemplos y aplicaciones y analizamos las experiencias y los resultados.  Puede que leer estos ejemplos le dé una idea de lo que conlleva el proceso de migración y actualización.  Durante el proceso ofreceremos sugerencias y trucos para llevar a cabo la actualización y mostraremos cómo se corrigieron errores concretos.|  
|[Migración a la Plataforma universal de Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)|Contiene información sobre el traslado de código a Windows 10.|  
|[Introducción a Visual C\+\+ para los usuarios de UNIX](../porting/introduction-to-visual-cpp-for-unix-users.md)|Proporciona información a los usuarios de UNIX que no estén familiarizados con [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] y deseen ser más productivos con él.|  
|[Trasladar de UNIX a Win32](../porting/porting-from-unix-to-win32.md)|Describe las opciones para migrar aplicaciones de UNIX a Windows.|  
|[Manual de migraciones C\+\+\/CLI](../dotnet/cpp-cli-migration-primer.md)|Muestra en detalle cómo actualizar la sintaxis de Extensiones administradas de C\+\+ para que utilice la nueva sintaxis.  Para obtener más información, vea [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md).|  
  
## Vea también  
 [Cambios importantes en Visual C\+\+ 2015](../porting/visual-cpp-change-history-2003-20151.md)