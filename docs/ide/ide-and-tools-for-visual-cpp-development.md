---
title: IDE y herramientas de desarrollo de Visual C++ | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: Visual C++, development tools
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1fc416d6856b2b84005e4e1d66e17a3b10e93eb6
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="ide-and-tools-for-visual-c-development"></a>IDE y herramientas para desarrollo de Visual C++
Como parte del Entorno de desarrollo integrado (IDE) de Visual Studio, Visual C++ tiene muchas ventanas y herramientas en común con otros lenguajes. Muchas de ellas, como **el Explorador de soluciones**, el Editor de código y el depurador, se documentan en [IDE de Visual Studio](/visualstudio/ide/visual-studio-ide). A menudo, una herramienta o una ventana compartida tiene un conjunto de características ligeramente diferentes para C++ que para los lenguajes .NET o Javascript. Algunas ventanas o herramientas solo están disponibles en Visual Studio Pro o Visual Studio Enterprise.   
  
 Además de las herramientas compartidas en el IDE de Visual Studio, Visual C++ dispone de varias herramientas específicas para desarrollar código nativo. Esas herramientas también se indican en este artículo. Para obtener una lista de los cuales herramientas están disponibles en cada edición de Visual Studio, vea [características en ediciones de Visual Studio y herramientas de Visual C++](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md).  
## <a name="creating-a-solution-and-projects"></a>Crear una solución y uno o varios proyectos  

Un "proyecto" es básicamente un conjunto de archivos de código fuente y recursos como imágenes o archivos de datos que están integrados en un archivo ejecutable. 2017 de Visual Studio puede admitir cualquier sistema de compilación o herramientas de compilación personalizadas que se va a usar, con compatibilidad total con Intellisense, exploración y la depuración:
 - MSBuild es el sistema de compilación "nativas" de Visual Studio y suele ser la mejor opción para aplicaciones UWP o heredadas aplicaciones de escritorio de Windows que utilizan MFC o ATL. Para obtener más información acerca de los proyectos de C++ basado en MSBuild, vea [crear y administrar proyectos basados en MSBuild](creating-and-managing-visual-cpp-projects.md).
 - CMake es el sistema que se integra en el IDE de Visual Studio cuando se instala la carga de trabajo de C++ de escritorio de compilación de soluciones multiplataforma. Para más información, consulte el artículo sobre [proyectos CMake en Visual C++](cmake-tools-for-visual-cpp.md).
 - Cualquier otro C++ sistema de compilación, incluida una colección flexible de archivos, se admite a través de la característica de la carpeta abierta. Crear archivos JSON sencillos para invocar el programa de compilación y configurar las sesiones de depuración. Para obtener más información, consulte [volver a poner el código de C++ en Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2017/04/14/bring-your-cpp-code-to-visual-studio/).
 
 
 **Plantillas de proyecto (MSBuild)**  
  
 Visual C++ incluye varias plantillas para proyectos basados en MSBuild; Estas plantillas contienen código de inicio y la configuración necesaria para diversos tipos de programas básicos. Normalmente empieza por elegir **archivo &#124; Nuevo proyecto** para crear un proyecto desde una plantilla de proyecto, a continuación, agregar nuevos archivos de código fuente a ese proyecto o comienza a escribir código en los archivos proporcionados. Para obtener información específica a los proyectos de C++ y asistentes para proyectos, consulte [crear y administrar proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md).  
  
 **Asistentes para aplicaciones (MSBuild)**  
  
 Visual C++ proporciona asistentes para algunos tipos de proyecto de MSBuild cuando se elige **archivo &#124; Nuevo proyecto**. Un asistente le guía paso a paso durante el proceso de creación de un nuevo proyecto. Esto es útil para los tipos de proyectos que tienen muchas opciones y configuración. Para obtener más información, consulte [crear escritorio proyectos por con asistentes para aplicaciones](../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
## <a name="creating-user-interfaces-with-designers-msbuild"></a>Crear interfaces de usuario con diseñadores (MSBuild) 
 Si el programa tiene interfaz de usuario, una de las primeras tareas que se deben realizar consiste en rellenar la interfaz de controles, como botones, cuadros de lista, etc. Visual Studio incluye una superficie de diseño visual y un cuadro de herramientas para cada tipo de aplicación de C++. Independientemente del tipo de aplicación que quiera crear, la idea básica es siempre la misma: arrastrar un control desde la ventana del cuadro de herramientas y colocarlo en el lugar que se desee de la superficie de diseño. Visual Studio genera en segundo plano los recursos y el código necesario para que todo funcione. A continuación, escribir el código para rellenar los controles con datos o personalizar su apariencia y comportamiento.
  
 Para obtener más información acerca de cómo diseñar una interfaz de usuario para una aplicación de plataforma Universal de Windows, vea [diseño y la interfaz de usuario](https://developer.microsoft.com/en-us/windows/design).  
  
 Para obtener más información acerca de cómo crear una interfaz de usuario para una aplicación MFC, vea [aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md). Para obtener información acerca de los programas de Windows de Win32, vea [las aplicaciones de escritorio de Windows](../windows/windows-desktop-applications-cpp.md).  
  
 Para obtener información acerca de las aplicaciones de Windows Forms con C++ / CLI, consulte [crear un Windows Forms aplicación mediante .NET Framework (C++)](http://msdn.microsoft.com/en-us/8e007885-6c8b-4fb2-a41d-91febd114a9b).  
  
## <a name="writing-and-editing-code"></a>Escribir y editar código  
 **Coloración semántica**  
  
 Después de crear un proyecto, se muestran todos los archivos de proyecto en el **el Explorador de soluciones** ventana. Al hacer clic en un archivo .h o .cpp en **el Explorador de soluciones**, el archivo se abre en el editor de código. El editor de código es un procesador de textos especializado para código fuente en C++. Este editor codifica mediante colores las palabras clave, los nombres de los métodos y las variables del lenguaje, así como otros elementos del código para que el código sea más fácil de leer y entender.  
  
 **IntelliSense**  
  
 El editor de código también admite varias características que, juntas, se conocen como Intellisense. Puede mantener el mouse sobre un método y ver su documentación básica. Después de escribir el nombre de una variable de clase y un . o ->, aparecerá una lista de miembros de instancia de esa clase. Si escribe el nombre de una clase y, luego, un ::, se mostrará una lista de miembros estáticos. Cuando empieza a escribir un nombre de clase o método, el editor de código le ofrece sugerencias para completar la instrucción. Para obtener más información, vea [Usar IntelliSense](/visualstudio/ide/using-intellisense).  
  
 **Fragmentos de código**  
  
 Puede usar fragmentos de código de IntelliSense para generar construcciones de código muy utilizadas o complicadas con solo pulsar un método abreviado. Para obtener más información, vea [Fragmentos de código](/visualstudio/ide/code-snippets).  
  
## <a name="navigating-code"></a>Navegar por el código  
 El **vista** menú proporciona acceso a muchas ventanas y herramientas para navegar por los archivos de código. Para obtener información detallada acerca de estas ventanas, vea [ver la estructura del código](/visualstudio/ide/viewing-the-structure-of-code).  
  
 **Explorador de soluciones**  
  
 En todas las ediciones de Visual Studio, use el panel del Explorador de soluciones para navegar por los archivos de un proyecto. Expanda un icono de archivo .h o .cpp para ver las clases que hay en el archivo. Expanda una clase para ver sus miembros. Haga doble clic en un miembro para ir hasta su definición o implementación en el archivo.  
  
 **Vista de clases y ventana Definición de código**  
  
 Use la **vista de clases** panel para ver los espacios de nombres y clases de todos los archivos, incluidas las clases parciales. Puede expandir cada espacio de nombres o clase para ver sus miembros y hacer doble clic en el miembro para ir hasta ese lugar del archivo de origen. Si abre la ventana Definición de código, puede ver la definición o implementación del tipo al elegirlo en la Vista de clases.  
  
 **Examinador de objetos**  
  
 Use **Examinador de objetos** para examinar la información de tipo en los componentes en tiempo de ejecución de Windows (archivos .winmd), los ensamblados .NET y COM las bibliotecas de tipos. No se utiliza con archivos DLL de Win32.  
  
 **Ir a definición/declaración**  
  
 Presione F12 en cualquier variable de miembro o nombre de API para ir a su definición. Si la definición se encuentra en un archivo .winmd (para una aplicación [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)]), se muestra la información de tipo en el Examinador de objetos. También puede elegir **ir a definición** o **ir a declaración** con el botón secundario en el nombre de variable o de tipo y eligiendo la opción en el menú contextual.  
  
 **Buscar todas las referencias**  
  
 En un archivo de código fuente, haga clic en el cursor del mouse sobre el nombre de un tipo o método o variable y elija **buscar todas las referencias** para devolver una lista de todas las ubicaciones del archivo, proyecto o solución donde se usa el tipo. **Buscar todas las referencias** de forma inteligente y solo devuelve las instancias de la misma variable, aunque otras variables de otro ámbito tengan el mismo nombre.  
  
 **Explorador de arquitectura y gráficos de dependencias (Ultimate)**  
  
 Use **Explorador de arquitectura** para ver las relaciones entre varios elementos en el código. Para obtener más información, consulte [Buscar código con el Explorador de arquitectura](http://msdn.microsoft.com/en-us/b1707926-ef73-47f9-92cd-e00d0fac7e76). Usar gráficos de dependencias para ver las relaciones de dependencia. Para obtener más información, consulte [Cómo: generar gráficos de dependencias para código C y C++](http://msdn.microsoft.com/en-us/3bd5cf9f-62f6-41d0-9f35-d4b2637cba3c).  
  
## <a name="adding-and-editing-resources--msbuild"></a>Agregar y editar recursos (MSBuild)
 El término “recurso” en el contexto de un proyecto de escritorio de Visual Studio incluye elementos como cuadros de diálogo, iconos, cadenas localizables, pantallas de presentación, cadenas de conexión de base de datos o cualquier dato arbitrario que desee incluir en el archivo ejecutable.  
  
 Para obtener más información sobre cómo agregar y editar recursos en proyectos nativos de C++ de escritorio, consulte [trabajar con archivos de recursos](../windows/working-with-resource-files.md).  
  
## <a name="building-compiling-and-linking"></a>Compilación (compilar y vincular)  
 Presione **Ctrl + Mayús + B** para compilar y vincular un proyecto. Para crear código ejecutable, Visual Studio usa [MSBuild](/visualstudio/msbuild/msbuild1) o CMake o el entorno de compilación establecen mediante **Abrir carpeta**. Para los proyectos de MSBuild, establecer opciones de compilación general en **herramientas &#124; Opciones &#124; Proyectos y soluciones** y se pueden establecer propiedades para proyectos específicos en **proyecto &#124; Propiedades**. Errores de compilación y las advertencias se muestran en la lista de errores (**Ctrl +\\, E**). Proyectos de MSBuild no se configuran con archivos JSON que se crean en el Explorador de soluciones. El sistema utiliza, la ventana de salida de compilación (**Alt + 2**) muestra información sobre el proceso de compilación. Para obtener más información acerca de las configuraciones de MSBuild, vea [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md) y [compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).  
  
 También puede usar el compilador de Visual C++ (cl.exe) y muchas otras herramientas independientes relacionadas con la compilación, como NMAKE y LIB, directamente desde la línea de comandos. Para obtener más información, consulte [de compilación de C/C ++ en la línea de comandos](../build/building-on-the-command-line.md) y [referencia de compilación de C/C ++](../build/reference/c-cpp-building-reference.md).  
  
## <a name="testing"></a>Pruebas  
 Visual Studio incluye un marco de pruebas unitarias para código C++/CLI y C++ nativo. Para obtener más información, consulte [comprobar código utilizando pruebas unitarias](/visualstudio/test/unit-test-your-code) y [escribir pruebas unitarias para C/C ++ con el marco de pruebas unitarias de Microsoft para C++](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)  
  
## <a name="debugging"></a>Depuración  
 Puede depurar el programa presionando **F5** cuando se establece la configuración del proyecto para la depuración. Durante la depuración puede establecer puntos de interrupción presionando **F9**, recorrer el código presionando **F10**, ver los valores de variables especificadas o registros, incluso en algunos casos, realizar cambios en el código y continuar depuración sin tener que volver a compilar. Para obtener más información, vea [Depurar en Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
## <a name="deploying-completed-applications"></a>Implementar aplicaciones completadas  
 Implementar un [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] a los clientes a través de la tienda Windows mediante el **proyecto &#124; Almacén de** opción de menú. La implementación de CRT se controla automáticamente en segundo plano. Para obtener más información, consulte [Llevar las aplicaciones al mercado](http://go.microsoft.com/fwlink/p/?LinkId=262280).  
  
 Al implementar una aplicación de escritorio de C++ nativo en otro equipo, debe instalar tanto la aplicación como todos los archivos de biblioteca de los que dependa la aplicación. Hay tres maneras de implementar el runtime de Visual C++ con una aplicación: implementación central, implementación local o vinculación estática. Para obtener más información, consulte [implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md).  
  
 Para obtener más información sobre la implementación de C++ / programa CLI, consulte [Deployment Guide for Developers](/dotnet/framework/deployment/deployment-guide-for-developers),  

## <a name="related-articles"></a>Artículos relacionados  
  
|||  
|-|-|  
|[Herramientas y características de Visual C++ en las ediciones de Visual Studio](../ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)|Muestra qué características están disponibles en las diferentes ediciones de Visual Studio.|  
|[Crear y administrar proyectos basados en MSBuild](../ide/creating-and-managing-visual-cpp-projects.md)|Proporciona información general sobre proyectos basados en MSBuild de C++ en Visual Studio y vínculos a otros artículos que explican cómo crearlas y administrarlas.|  
|[CMake proyectos en Visual C++](cmake-tools-for-visual-cpp.md).|Describe cómo crear CMake u otros proyectos de MSBuild no en Visual C++.|
|[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)|Describe cómo compilar proyectos de C++.|  
|[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)|Proporciona información general sobre la implementación de aplicaciones de C++ y vínculos a otros artículos que describen de forma detallada la implementación.|  
|[Guía de migración y actualización de Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)|Información detallada sobre cómo actualizar las aplicaciones de C++ que se crearon en versiones anteriores de Visual Studio y también cómo migrar las aplicaciones que se crearon con herramientas distintas a Visual Studio.|  
|[Visual C++](../top/visual-cpp-in-visual-studio.md)|Describe las principales características de Visual C++ en Visual Studio y vínculos al resto de la documentación sobre Visual C++.|
