---
title: "IDE y herramientas para desarrollo de Visual C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "Visual C++, herramientas de desarrollo"
ms.assetid: 56eabafb-1956-4f0f-bec5-29b887763559
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IDE y herramientas para desarrollo de Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como parte del Entorno de desarrollo integrado (IDE) de Visual Studio, Visual C++ tiene muchas ventanas y herramientas en común con otros lenguajes. Muchas de ellas, como el **Explorador de soluciones**, el Editor de código o el Depurador, están documentadas en MSDN Library en [Visual Studio IDE](../Topic/Visual%20Studio%20IDE.md). A menudo, una herramienta o una ventana compartida tiene un conjunto de características ligeramente diferentes para C++ que para los lenguajes .NET o Javascript. Algunas ventanas o herramientas solo están disponibles en Visual Studio Pro o Visual Studio Enterprise. Este tema presenta el IDE de Visual Studio desde la perspectiva de Visual C++ y proporciona vínculos a otros temas relacionados con Visual C++.  
  
 Además de las herramientas compartidas en el IDE de Visual Studio, Visual C++ dispone de varias herramientas específicas para desarrollar código nativo. Esas herramientas también se indican en este artículo. Para obtener una lista de las herramientas disponibles en cada edición de Visual Studio, consulte [Visual C++ Tools and Templates in Visual Studio Editions](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md).  
  
## <a name="creating-a-solution-and-projects"></a>Crear una solución y uno o varios proyectos  
 En todas las ediciones de Visual C++, el código fuente y los archivos relacionados de un archivo ejecutable (como .exe, .dll o .lib) se organizan en un proyecto. Un proyecto tiene un archivo de proyecto en formato XML (.vcxproj) que especifica todos los archivos y los recursos necesarios para compilar el programa, así como otras opciones de configuración, como la plataforma de destino (x86, x64 o ARM) y si está creando una versión de lanzamiento o una versión de depuración del programa. Un proyecto (o muchos proyectos) se incluyen dentro de una *Solución*: por ejemplo, una solución podría contener varios proyectos de archivos DLL para Win32 y una única aplicación de consola Win32 que utilice dichos archivos DLL. Al compilar el proyecto, el motor de MSBuild consume el archivo de proyecto y genera el archivo ejecutable o cualquier otro resultado personalizado que se haya especificado.  
  
 **Plantillas de proyecto**  
  
 Visual C++ incluye varias plantillas de proyecto, que contienen código de inicio y la configuración necesaria para diversos tipos de programas básicos. Normalmente se empieza por elegir **archivo &#124; Nuevo proyecto** para crear un proyecto desde una plantilla de proyecto, a continuación, agregar nuevos archivos de código fuente para ese proyecto, o empezar a codificar en los archivos proporcionados. Para obtener información específica de proyectos de C++ y los asistentes para proyectos, consulte [Creating and Managing Visual C++ Projects](../ide/creating-and-managing-visual-cpp-projects.md).  
  
 **Asistentes para aplicaciones**  
  
 Visual C++ proporciona asistentes para algunos tipos de proyecto. Un asistente le guía paso a paso durante el proceso de creación de un nuevo proyecto. Esto es útil para los tipos de proyectos que tienen muchas opciones y configuración. Para obtener más información, vea [Creating Desktop Projects By Using Application Wizards](../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
## <a name="creating-user-interfaces-with-designers"></a>Crear interfaces de usuario con diseñadores  
 Si el programa tiene interfaz de usuario, una de las primeras tareas que se deben realizar consiste en rellenar la interfaz de controles, como botones, cuadros de lista, etc. Visual Studio incluye una superficie de diseño visual y un cuadro de herramientas para cada tipo de aplicación de C++. Independientemente del tipo de aplicación que quiera crear, la idea básica es siempre la misma: arrastrar un control desde la ventana del cuadro de herramientas y colocarlo en el lugar que se desee de la superficie de diseño. Visual Studio genera en segundo plano los recursos y el código necesario para que todo funcione.  
  
 Para obtener más información sobre cómo diseñar una interfaz de usuario para una aplicación de plataforma Universal de Windows, consulte  [Diseño y la interfaz de Usuario](https://developer.microsoft.com/en-us/windows/design).  
  
 Para más información sobre cómo crear una interfaz de usuario para una aplicación de MFC, consulte [MFC Desktop Applications](../mfc/mfc-desktop-applications.md). Para obtener información acerca de los programas de Windows de Win32, vea [aplicaciones de escritorio de Windows](../windows/windows-desktop-applications-cpp.md).  
  
 Para ver información sobre las aplicaciones de Windows Forms con C++/CLI, consulte [Crear una aplicación de Windows Forms mediante .NET Framework (C++)](http://msdn.microsoft.com/es-es/8e007885-6c8b-4fb2-a41d-91febd114a9b).  
  
## <a name="writing-and-editing-code"></a>Escribir y editar código  
 **Coloración semántico**  
  
 Después de crear un proyecto, todos los archivos del proyecto se muestran en la ventana Explorador de soluciones. Al hacer clic en un archivo .h o .cpp en el Explorador de soluciones, se abre el archivo en el editor de código. El editor de código es un procesador de textos especializado para código fuente en C++. Este editor codifica mediante colores las palabras clave, los nombres de los métodos y las variables del lenguaje, así como otros elementos del código para que el código sea más fácil de leer y entender.  
  
 **IntelliSense**  
  
 El editor de código también admite varias características que, juntas, se conocen como Intellisense. Puede mantener el mouse sobre un método y ver su documentación básica. Después de escribir el nombre de una variable de clase y un . o ->, aparecerá una lista de miembros de instancia de esa clase. Si escribe el nombre de una clase y, luego, un ::, se mostrará una lista de miembros estáticos. Cuando empieza a escribir un nombre de clase o método, el editor de código le ofrece sugerencias para completar la instrucción. Para obtener más información, vea [Using IntelliSense](../Topic/Using%20IntelliSense.md).  
  
 **Fragmentos de código**  
  
 Puede usar fragmentos de código de IntelliSense para generar construcciones de código muy utilizadas o complicadas con solo pulsar un método abreviado. Para obtener más información, vea [Code Snippets](../Topic/Code%20Snippets.md).  
  
## <a name="navigating-code"></a>Navegar por el código  
 El menú VISTA proporciona acceso a muchas ventanas y herramientas que le permiten navegar por los archivos de código. Para obtener información detallada sobre estas ventanas, consulte [Viewing the Structure of Code](../Topic/Viewing%20the%20Structure%20of%20Code.md).  
  
 **Explorador de soluciones**  
  
 En todas las ediciones de Visual Studio, use el panel del Explorador de soluciones para navegar por los archivos de un proyecto. Expanda un icono de archivo .h o .cpp para ver las clases que hay en el archivo. Expanda una clase para ver sus miembros. Haga doble clic en un miembro para ir hasta su definición o implementación en el archivo.  
  
 **Vista de clases y la ventana Definición de código**  
  
 Utilice el panel Vista de clases para ver los espacios de nombres y las clases de todos los archivos, incluidas las clases parciales. Puede expandir cada espacio de nombres o clase para ver sus miembros y hacer doble clic en el miembro para ir hasta ese lugar del archivo de origen. Si abre la ventana Definición de código, puede ver la definición o implementación del tipo al elegirlo en la Vista de clases.  
  
 **Examinador de objetos**  
  
 Utilice el Examinador de objetos para examinar la información de tipo en los componentes en tiempo de ejecución de Windows (archivos .winmd), los ensamblados .NET y las bibliotecas de tipo COM. No se utiliza con archivos DLL de Win32.  
  
 **Ir a definición o declaración**  
  
 Presione F12 en cualquier variable de miembro o nombre de API para ir a su definición. Si la definición se encuentra en un archivo .winmd (para una aplicación [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] ), se muestra la información de tipo en el Examinador de objetos. También puede Ir a definición o Ir a declaración haciendo clic con el botón derecho en el nombre de variable o de tipo y eligiendo la opción correspondiente en el menú contextual.  
  
 **Buscar todas las referencias**  
  
 En un archivo de código fuente, haga clic con el botón derecho con el cursor del mouse sobre el nombre de un tipo, método o variable y elija Buscar todas las referencias para obtener una lista de todas las ubicaciones del archivo, proyecto o solución donde se usa el tipo. Buscar todas las referencias funciona de forma inteligente y solo devuelve las instancias de la misma variable, aunque otras variables de otro ámbito tengan el mismo nombre.  
  
 **Explorador de arquitectura y gráficos de dependencia (Ultimate)**  
  
 Use el Explorador de arquitectura para ver las relaciones entre varios elementos de su código. Para obtener más información, consulte [Buscar código con el Explorador de arquitectura](http://msdn.microsoft.com/es-es/b1707926-ef73-47f9-92cd-e00d0fac7e76). Use gráficos de dependencias para ver las relaciones de dependencia. Para obtener más información, vea [How to: Generate Dependency Graphs for C and C++ Code](http://msdn.microsoft.com/es-es/3bd5cf9f-62f6-41d0-9f35-d4b2637cba3c).  
  
## <a name="adding-and-editing-resources"></a>Agregar y editar recursos  
 El término “recurso” en el contexto de un proyecto de escritorio de Visual Studio incluye elementos como cuadros de diálogo, iconos, cadenas localizables, pantallas de presentación, cadenas de conexión de base de datos o cualquier dato arbitrario que desee incluir en el archivo ejecutable.  
  
 Para obtener más información sobre cómo agregar y editar recursos en proyectos nativos de C++ de escritorio, consulte [Working with Resource Files](../mfc/working-with-resource-files.md).  
  
## <a name="building-compiling-and-linking"></a>Compilación (compilar y vincular)  
 Presione **Ctrl + Mayús + B** para compilar y vincular un proyecto. Visual Studio usa [MSBuild](MSBuild1.md) para crear código ejecutable. Puede establecer opciones de compilación general bajo **Herramientas &#124; Opciones &#124; Proyectos y soluciones** y puede establecer las propiedades de proyectos específicos en **proyecto &#124; Propiedades**. Errores de compilación y advertencias se muestran en la lista de errores (**Ctrl +\\, E**). A veces se muestra información adicional en la Ventana de salida (**Alt + 2**). Para obtener más información, consulte  [trabajar con propiedades de proyecto](../ide/working-with-project-properties.md) y [Generar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md).  
  
 También puede usar el compilador de Visual C++ (cl.exe) y muchas otras herramientas independientes relacionadas con la compilación, como NMAKE y LIB, directamente desde la línea de comandos. Para obtener más información, vea [Building on the Command Line](../build/building-on-the-command-line.md) y [C/C++ Building Reference](../build/reference/c-cpp-building-reference.md).  
  
## <a name="testing"></a>Pruebas  
 Visual Studio incluye un marco de pruebas unitarias para código C++/CLI y C++ nativo. Para más información, consulte [Comprobar código utilizyo pruebas unitarias](../Topic/Unit%20Test%20Your%20Code.md) y [Escribir pruebas unitarias para C/C++ con el Framework de pruebas unitarias de Microsoft para C++](../Topic/Writing%20Unit%20tests%20for%20C-C++%20with%20the%20Microsoft%20Unit%20Testing%20Framework%20for%20C++.md).  
  
## <a name="debugging"></a>Depuración  
 Puede depurar el programa presionando F5 cuando la configuración del proyecto esté establecida como Depurar. Durante la depuración puede establecer puntos de interrupción presionando F9, recorrer el código presionando F10, ver los valores de registros o variables especificados e, incluso, en algunos casos, realizar cambios en el código y continuar la depuración sin tener que volver a compilar. Para obtener más información, vea [Debugging in Visual Studio](../Topic/Debugging%20in%20Visual%20Studio.md).  
  
## <a name="deploying-completed-applications"></a>Implementar aplicaciones completadas  
 Implementar un [!INCLUDE[win8_appname_long](../build/includes/win8_appname_long_md.md)] los clientes a través de la tienda de Windows a través de la **PROYECTO &#124; Almacén de** opción de menú. La implementación de CRT se controla automáticamente en segundo plano. Para obtener más información, consulte [Llevar las aplicaciones al mercado](http://go.microsoft.com/fwlink/p/?LinkId=262280).  
  
 Al implementar una aplicación de escritorio de C++ nativo en otro equipo, debe instalar tanto la aplicación como todos los archivos de biblioteca de los que dependa la aplicación. Hay tres maneras de implementar el runtime de Visual C++ con una aplicación: implementación central, implementación local o vinculación estática. Para obtener más información, consulte [implementación de aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md).  
  
 Para obtener más información acerca de la implementación C + + / programa CLI, consulte [Deployment Guide for Developers](../Topic/.NET%20Framework%20Deployment%20Guide%20for%20Developers.md),  
  
## <a name="other-tools"></a>Otras herramientas  
  
## <a name="related-articles"></a>Artículos relacionados  
  
|||  
|-|-|  
|[Herramientas de Visual C++ y plantillas en las ediciones de Visual Studio](../ide/visual-cpp-tools-and-templates-in-visual-studio-editions.md)|Muestra qué características están disponibles en las diferentes ediciones de Visual Studio.|  
|[Paseo guiado por Visual C++](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)|Proporciona información general sobre el entorno de desarrollo de Visual Studio y los tipos de aplicaciones de C++ que se pueden crear.|  
|[Crear y administrar proyectos de Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)|Proporciona información general sobre los proyectos de C++ de Visual Studio y vínculos a otros artículos que explican cómo crearlos y administrarlos.|  
|[Compilar programas de C o C++](../build/building-c-cpp-programs.md)|Describe cómo compilar proyectos de C++.|  
|[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)|Proporciona información general sobre la implementación de aplicaciones de C++ y vínculos a otros artículos que describen de forma detallada la implementación.|  
|[Trasladar y actualizar programas](http://msdn.microsoft.com/es-es/c36c44b3-5a9b-4bb4-9b7a-469aa770ed00)|Vínculos a artículos que describen cómo abrir aplicaciones de C++ que se crearon en versiones anteriores de Visual Studio y, también, cómo abrir aplicaciones que se crearon con herramientas distintas a Visual Studio.|  
|||  
|[Visual C++](../top/visual-cpp-in-visual-studio-2015.md)|Describe las principales características de Visual C++ en Visual Studio y vínculos al resto de la documentación sobre Visual C++.|