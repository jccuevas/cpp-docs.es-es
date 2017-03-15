---
title: "Tutorial: Crear y utilizar una biblioteca de v&#237;nculos din&#225;micos (C++) | Microsoft Docs"
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
  - "DLL [C++], tutoriales"
  - "bibliotecas [C++], DLL"
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
caps.latest.revision: 36
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Crear y utilizar una biblioteca de v&#237;nculos din&#225;micos (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tutorial paso a paso muestra cómo crear una biblioteca de vínculos dinámicos \(DLL\) para su uso con aplicaciones de C\+\+.  Utilizar una biblioteca es una excelente manera de reutilizar código.  En lugar de volver a implementar las mismas rutinas en cada programa que crea, las escribe una vez y, luego, hace referencia a ellas desde las aplicaciones que requieren esa funcionalidad.  Al colocar el código en la DLL, ahorra espacio en cada aplicación que hace referencia a ella y puede actualizar la DLL sin tener que recompilar todas las aplicaciones.  Para más información sobre las DLL, consulte [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md).  
  
 En este tutorial se tratan las siguientes tareas:  
  
-   Creación de un proyecto de DLL  
  
-   Adición de una clase a la DLL  
  
-   Creación de una aplicación de consola que usa vinculación dinámica en tiempo de carga para hacer referencia a la DLL  
  
-   Uso de la funcionalidad desde la clase de la aplicación  
  
-   Ejecución de la aplicación  
  
 En este tutorial, se crea una DLL a la que solo se puede llamar desde las aplicaciones que utilizan las convenciones de llamada de C\+\+.  Para obtener información sobre cómo crear DLL que se puedan usar con otros lenguajes, consulte [Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md).  
  
## Requisitos previos  
 En este tema, se da por supuesto que comprende los fundamentos del lenguaje C\+\+.  
  
### Para crear un proyecto de biblioteca de vínculos dinámicos \(DLL\)  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado**, **Plantillas**, **Visual C\+\+** y, a continuación, seleccione **Win32**.  
  
3.  En el panel central, seleccione **Aplicación de consola Win32**.  
  
4.  Especifique un nombre para el proyecto en el cuadro **Nombre**: por ejemplo, MathFuncsDll.  Especifique un nombre para la solución en el cuadro **Nombre de la solución**: por ejemplo, DynamicLibrary.  Elija el botón **Aceptar**.  
  
5.  En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones Win32**, elija el botón **Siguiente**.  
  
6.  En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **DLL**.  
  
7.  Elija el botón **Finalizar** para crear el proyecto.  
  
### Para agregar una clase a la biblioteca de vínculos dinámicos  
  
1.  Para crear un archivo de encabezado para una nueva clase, en la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  En el cuadro de diálogo **Agregar nuevo elemento**, en el panel izquierdo, bajo **Visual C\+\+**, seleccione **Código**.  En el panel central, seleccione **Archivo de encabezado \(.h\)**.  Especifique un nombre para el archivo de encabezado \(por ejemplo, MathFuncsDll.h\) y, después, elija el botón **Agregar**.  Se muestra un archivo de encabezado en blanco.  
  
2.  Agregue el siguiente código a la parte superior del archivo de encabezado:  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#100](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_1.h)]  
  
3.  Agregue una clase básica llamada MyMathFuncs para realizar operaciones matemáticas comunes, como suma, resta, multiplicación y división.  El código debe ser similar a este:  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#101](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_2.h)]  
  
     Cuando el símbolo MATHFUNCSDLL\_EXPORTS está definido, el símbolo MATHFUNCSDLL\_API establece el modificador `__declspec(dllexport)` en las declaraciones de funciones miembros de este código.  Este modificador permite que la DLL exporte la función para que otras aplicaciones puedan usarla.  Cuando MATHFUNCSDLL\_EXPORTS está sin definir \(por ejemplo, cuando es una aplicación la que incluye el archivo de encabezado\), MATHFUNCSDLL\_API define el modificador `__declspec(dllimport)` en las declaraciones de funciones miembros.  Este modificador optimiza la importación de la función en una aplicación.  De forma predeterminada, la plantilla Nuevo proyecto de una DLL agrega `PROJECTNAME`\_EXPORTS a los símbolos definidos del proyecto de DLL.  En este ejemplo, MATHFUNCSDLL\_EXPORTS se define al compilar el proyecto MathFuncsDll.  Para obtener más información, vea [dllexport, dllimport](../cpp/dllexport-dllimport.md).  
  
    > [!NOTE]
    >  Si compila el proyecto de DLL en la línea de comandos, utilice la opción del compilador **\/D** para definir el símbolo MATHFUNCSDLL\_EXPORTS.  
  
4.  En el proyecto **MathFuncsDll**, en el **Explorador de soluciones**, dentro de la carpeta **Archivos de código fuente**, abra MathFuncsDll.cpp.  
  
5.  Implemente la funcionalidad de MyMathFuncs en el código fuente.  El código debe ser similar a este:  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#110](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_3.cpp)]  
  
6.  Compile la biblioteca de vínculos dinámicos eligiendo **Compilar**, **Compilar solución** en la barra de menús.  
  
    > [!NOTE]
    >  Si está utilizando una edición Express que no muestre el menú **Compilar**, en la barra de menús, elija **Herramientas**, **Configuración**, **Configuración para expertos** para habilitarlo y, luego, elija **Compilar**, **Compilar solución**.  
  
    > [!NOTE]
    >  Si compila un proyecto desde la línea de comandos, utilice la opción del compilador **\/LD** para especificar que el archivo de salida debe ser una DLL.  Para obtener más información, vea [\/MD, \/MT, \/LD \(Utilizar la biblioteca en tiempo de ejecución\)](../build/reference/md-mt-ld-use-run-time-library.md).  Utilice la opción del compilador **\/EHsc** para habilitar el control de excepciones de C\+\+.  Para obtener más información, vea [\/EH \(Modelo de control de excepciones\)](../build/reference/eh-exception-handling-model.md).  
  
### Para crear una aplicación que haga referencia a la DLL  
  
1.  Para crear una aplicación de C\+\+ que haga referencia a la DLL que acaba de crear y la utilice, en la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el panel izquierdo, debajo de **Visual C\+\+**, seleccione **Win32**.  
  
3.  En el panel central, seleccione **Aplicación de consola Win32**.  
  
4.  Especifique un nombre para el proyecto en el cuadro **Nombre**: por ejemplo, MyExecRefsDll.  Junto a **Solución**, seleccione **Agregar a solución** en la lista desplegable.  De este modo, agregará el nuevo proyecto a la solución que contiene la DLL.  Elija el botón **Aceptar**.  
  
5.  En la página **Información general** del cuadro de diálogo **Asistente para aplicaciones Win32**, elija el botón **Siguiente**.  
  
6.  En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **Aplicación de consola**.  
  
7.  En la página **Configuración de la aplicación**, en **Opciones adicionales**, desactive la casilla **Encabezado precompilado**.  
  
8.  Elija el botón **Finalizar** para crear el proyecto.  
  
### Para utilizar la funcionalidad de la biblioteca de clases en la aplicación  
  
1.  Después de crear una aplicación de consola, se crea un programa vacío.  El nombre del archivo de código fuente será el mismo que el elegido anteriormente.  En este ejemplo, se llama MyExecRefsDll.cpp.  
  
2.  Para usar en la aplicación las rutinas matemáticas que creó en la DLL, debe hacer referencia a ellas.  Para ello, seleccione el proyecto MyExecRefsDll en el **Explorador de soluciones** y, luego, en la barra de menús, elija **Proyecto**, **Referencias**.  En el cuadro de diálogo **Páginas de propiedades**, expanda el nodo **Propiedades comunes**, seleccione **Marco de trabajo y referencias** y, después, elija el botón **Agregar nueva referencia**.  Para obtener más información sobre el cuadro de diálogo **Referencias**, vea [Agregar referencias](../ide/adding-references-in-visual-cpp-projects.md).  
  
3.  El cuadro de diálogo **Agregar referencia** muestra las bibliotecas a las que puede hacer referencia.  La pestaña **Proyectos** muestra una lista de los proyectos de la solución actual y las bibliotecas que contienen.  En la pestaña **Proyectos**, active la casilla situada junto a MathFuncsDll y, después, elija el botón **Aceptar**.  
  
4.  Para hacer referencia a los archivos de encabezado de la DLL, debe modificar la ruta de acceso de los directorios de inclusión.  Para ello, en el cuadro de diálogo **Páginas de propiedades**, expanda el nodo **Propiedades de configuración**, expanda el nodo **C\/C\+\+** y, luego, seleccione **General**.  Junto a **Directorios de inclusión adicionales**, especifique la ruta de acceso de la ubicación donde se encuentra el archivo de encabezado MathFuncsDll.h.  Puede usar una ruta de acceso relativa \(por ejemplo, ..\\MathFuncsDll\\\) y, después, elegir el botón **Aceptar**.  
  
5.  Ahora puede utilizar la clase MyMathFuncs en esta aplicación.  Reemplace el contenido de MyExecRefsDll.cpp por el código siguiente:  
  
     [!code-cpp[NVC_Create_DLL_Walkthrough#120](../build/codesnippet/CPP/walkthrough-creating-and-using-a-dynamic-link-library-cpp_4.cpp)]  
  
6.  Compile el archivo ejecutable; para ello, elija **Compilación**, **Compilar solución** en la barra de menús.  
  
### Para ejecutar la aplicación  
  
1.  Compruebe que MyExecRefsDll está seleccionado como proyecto predeterminado.  En el **Explorador de soluciones**, seleccione MyExecRefsDll y, luego, en la barra de menús, elija **Proyecto**, **Establecer como proyecto de inicio**.  
  
2.  Para ejecutar el proyecto, en la barra de menús, elija **Depurar**, **Iniciar sin depurar**.  El resultado debería ser similar a lo siguiente:  
  
  **a \+ b \= 106,4**  
**a \- b \= \-91,6**  
**a \* b \= 732,6**  
**a \/ b \= 0,0747475**  
**Se detectó una excepción: b no puede ser cero.**  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)   
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)   
 [Tutorial: Implementar el programa \(C\+\+\)](../ide/walkthrough-deploying-your-program-cpp.md)   
 [Llamar a funciones de un archivo DLL desde aplicaciones programadas en Visual Basic](../build/calling-dll-functions-from-visual-basic-applications.md)