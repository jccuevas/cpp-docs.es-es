---
title: "Tutorial: Crear y utilizar una biblioteca est&#225;tica (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bibliotecas [C++], estáticas"
  - "bibliotecas estáticas [C++]"
ms.assetid: 3cc36411-7d66-4240-851e-dacb9a8fd6ac
caps.latest.revision: 38
caps.handback.revision: 38
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Crear y utilizar una biblioteca est&#225;tica (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tutorial paso a paso se muestra cómo crear una biblioteca estática \(archivo .lib\) para su uso con aplicaciones de C\+\+. Utilizar una biblioteca estática es una excelente manera de reutilizar el código. En lugar de volver a implementar las mismas rutinas en todos las aplicaciones que requieran la funcionalidad, escríbalas una vez en una biblioteca estática y, a continuación, haga referencia a ellas desde las aplicaciones. El código vinculado desde una biblioteca estática pasa a formar parte de la aplicación \(no es necesario instalar otro archivo para utilizar el código\).  
  
 En este tutorial se tratan las siguientes tareas:  
  
-   [Crear un proyecto de biblioteca estática](#BKMK_CreateLibProject)  
  
-   [Agregar una clase a la biblioteca estática](#BKMK_AddClassToLib)  
  
-   [Crear una aplicación de consola que haga referencia a la biblioteca estática](#BKMK_CreateAppToRefTheLib)  
  
-   [Usar la funcionalidad de la biblioteca estática en la aplicación](#BKMK_UseLibInApp)  
  
-   [Ejecutar la aplicación](#BKMK_RunApp)  
  
## Requisitos previos  
 Descripción de los fundamentos del lenguaje C\+\+.  
  
##  <a name="BKMK_CreateLibProject"></a> Crear un proyecto de biblioteca estática  
  
#### Para crear un proyecto de biblioteca estática  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado**, **Plantillas**, **Visual C\+\+** y, a continuación, seleccione **Win32**.  
  
3.  En el panel central, seleccione **Aplicación de consola Win32**.  
  
4.  Especifique un nombre para el proyecto; por ejemplo, **MathFuncsLib**, en el cuadro **Nombre**. Especifique un nombre para la solución, por ejemplo, **StaticLibrary**, en el cuadro **Nombre de la solución**. Elija el botón **Aceptar**.  
  
5.  En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones Win32**, elija el botón **Siguiente**.  
  
6.  En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **Biblioteca estática**.  
  
7.  En la página **Configuración de la aplicación**, en **Opciones adicionales**, desactive la casilla **Encabezado precompilado**.  
  
8.  Elija el botón **Finalizar** para crear el proyecto.  
  
##  <a name="BKMK_AddClassToLib"></a> Agregar una clase a la biblioteca estática  
  
#### Para agregar una clase a la biblioteca estática  
  
1.  Si quiere crear un archivo de encabezado para una nueva clase, abra el menú contextual del proyecto **MathFuncsLib** en el **Explorador de soluciones** y después elija **Agregar**, **Nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento**, en el panel izquierdo, bajo **Visual C\+\+**, seleccione **Código**. En el panel central, seleccione **Archivo de encabezado \(.h\)**. Especifique un nombre para el encabezado de archivo, por ejemplo, **MathFuncsLib.h** y después elija el botón **Agregar**. Se muestra un archivo de encabezado en blanco.  
  
2.  Agregue una clase denominada **MyMathFuncs** para hacer operaciones matemáticas comunes, como la suma, resta, multiplicación y división. El código debe ser similar a este:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#100](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_1.h)]  
  
3.  Para crear un archivo de código fuente para la nueva clase, abra el menú contextual para el proyecto **MathFuncsLib** en el **Explorador de soluciones** y después elija **Agregar**, **Nuevo elemento**. En el cuadro de diálogo **Agregar nuevo elemento**, en el panel izquierdo, bajo **Visual C\+\+**, seleccione **Código**. En el panel central, seleccione **Archivo de C\+\+ \(.cpp\)**. Especifique un nombre para el archivo de origen, por ejemplo, **MathFuncsLib.cpp** y después elija el botón **Agregar**. Se muestra un archivo de código fuente en blanco.  
  
4.  Use este archivo de código fuente para implementar la funcionalidad de **MyMathFuncs**. El código debe ser similar a este:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#110](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_2.cpp)]  
  
5.  Compile la biblioteca estática seleccionando **Compilar**, **Compilar solución** en la barra de menús. Esto crea una biblioteca estática que puede ser utilizada por otros programas.  
  
    > [!NOTE]
    >  Cuando compile desde la línea de comandos de Visual Studio, debe compilar el programa en dos pasos. Primero, ejecute **cl \/c \/EHsc MathFuncsLib.cpp** para compilar el código y crear un archivo de objeto denominado **MathFuncsLib.obj**. \(El comando **cl** invoca el compilador, Cl.exe y la opción **\/c** especifica compilar sin vinculación. Para obtener más información, vea [\/c \(Compilar sin vincular\)](../build/reference/c-compile-without-linking.md)\). En segundo lugar, ejecute **lib MathFuncsLib.obj** para enlazar el código y crear la biblioteca estática **MathFuncsLib.lib**. \(El comando **lib** invoca el Administrador de bibliotecas, Lib.exe. Para obtener más información, vea [Referencia de LIB](../build/reference/lib-reference.md)\).  
  
##  <a name="BKMK_CreateAppToRefTheLib"></a> Crear una aplicación de consola que haga referencia a la biblioteca estática  
  
#### Para crear una aplicación de consola C\+\+ que haga referencia a la biblioteca estática  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el panel izquierdo, debajo de **Visual C\+\+**, seleccione **Win32**.  
  
3.  En el panel central, seleccione **Aplicación de consola Win32**.  
  
4.  Especifique un nombre para el proyecto; por ejemplo, **MyExecRefsLib**, en el cuadro **Nombre**. En la lista desplegable junto a **Solución**, seleccione **Agregar a solución**. Esto agrega el nuevo proyecto a la solución que contiene la biblioteca estática. Elija el botón **Aceptar**.  
  
5.  En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones Win32**, elija el botón **Siguiente**.  
  
6.  En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **Aplicación de consola**.  
  
7.  En la página **Configuración de la aplicación**, en **Opciones adicionales**, desactive la casilla **Encabezado precompilado**.  
  
8.  Elija el botón **Finalizar** para crear el proyecto.  
  
##  <a name="BKMK_UseLibInApp"></a> Usar la funcionalidad de la biblioteca estática en la aplicación  
  
#### Para utilizar la funcionalidad de la biblioteca estática en la aplicación  
  
1.  Después de crear una aplicación de consola, se crea un programa vacío. El nombre del archivo de código fuente será el mismo que el elegido anteriormente. En este ejemplo, se llama **MyExecRefsLib.cpp**.  
  
2.  Para poder usar las rutinas de coincidencia de la biblioteca estática, debe hacer referencia a ella. Para ello, abra el menú contextual del proyecto **MyExecRefsLib** en el **Explorador de soluciones** y luego elija **Referencias**. En el cuadro de diálogo **Páginas de propiedades** de **MyExecRefsLib**, expanda el nodo **Propiedades comunes**, seleccione **Marco de trabajo y referencias** y luego elija el botón **Agregar nueva referencia**. Para obtener más información sobre el cuadro de diálogo **Referencias**, vea [Agregar referencias](../ide/adding-references-in-visual-cpp-projects.md).  
  
3.  El cuadro de diálogo **Agregar referencia** muestra las bibliotecas a las que puede hacer referencia. La pestaña **Proyectos** enumera los proyectos de la solución actual y las bibliotecas que contienen. En la pestaña **Proyectos**, active la casilla situada junto a **MathFuncsLib** y después elija el botón **Aceptar**.  
  
4.  Para hacer referencia al archivo de encabezado **MathFuncsLib.h**, debe modificar la ruta de acceso de los directorios de inclusión. En el cuadro de diálogo **Páginas de propiedades** de **MyExecRefsLib**, expanda los nodos **Propiedades de configuración** y **C\/C\+\+**, y luego seleccione **General**. Junto a **Directorios de inclusión adicionales**, especifique la ruta de acceso del directorio **MathFuncsLib** o búsquela.  
  
     Para buscar la ruta del directorio abra el cuadro de lista desplegable del valor de propiedad y, a continuación, elija **Editar**. En el cuadro de diálogo **Directorios de inclusión adicionales**, en el cuadro de texto, seleccione una línea en blanco y, a continuación, elija los puntos suspensivos \(**...**\) al final de la línea. En el cuadro de diálogo **Seleccionar directorio**, seleccione el directorio **MathFuncsLib** y después elija el botón **Seleccionar carpeta** para guardar la selección y cerrar el cuadro de diálogo. En el cuadro de diálogo **Directorios de inclusión adicionales**, elija el botón **Aceptar** y, en el cuadro de diálogo **Páginas de propiedades**, elija el botón **Aceptar** para guardar los cambios en el proyecto.  
  
5.  Ahora puede usar la clase **MyMathFuncs** en esta aplicación. Para ello, reemplace el contenido de **MyExecRefsLib.cpp** por este código:  
  
     [!code-cpp[NVC_Walkthrough_Create_Static_Lib#120](../windows/codesnippet/CPP/walkthrough-creating-and-using-a-static-library-cpp_3.cpp)]  
  
6.  Compile el archivo ejecutable; para ello, elija **Compilación**, **Compilar solución** en la barra de menús.  
  
##  <a name="BKMK_RunApp"></a> Ejecutar la aplicación  
  
#### Para ejecutar la aplicación  
  
1.  Asegúrese de que **MyExecRefsLib** esté seleccionado como proyecto predeterminado abriendo el menú contextual de **MyExecRefsLib** en el **Explorador de soluciones** y eligiendo **Establecer como proyecto de inicio**.  
  
2.  Para ejecutar el proyecto, en la barra de menús, elija **Depurar**, **Iniciar sin depurar**. El resultado debería ser similar a lo siguiente:  
  
    ```Output  
    a + b = 106.4 a - b = -91.6 a * b = 732.6 a / b = 0.0747475  
    ```  
  
## Vea también  
 [Paseo guiado de Visual C\+\+](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Tutorial: Crear y utilizar una biblioteca de vínculos dinámicos \(C\+\+\)](../build/walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)   
 [Aplicaciones de escritorio de Windows \(Visual C\+\+\)](../windows/desktop-applications-visual-cpp.md)