---
title: 'Tutorial: Trabajar con proyectos y soluciones (C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: "25"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6b30cd4885d5fdd65831c8044a088fcb87b52ae3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Tutorial: Trabajar con proyectos y soluciones (C++)
A continuación puede encontrar información de cómo crear un proyecto de C++ en Visual Studio, agregar código y compilar y ejecutar el proyecto. El proyecto de este tutorial es un programa que realiza un seguimiento de cuántos jugadores están jugando a distintos juegos de cartas.  
  
 En Visual Studio, el trabajo se organiza en proyectos y soluciones. Una solución puede contener más de un proyecto; por ejemplo, un archivo DLL y una aplicación ejecutable que haga referencia a ese archivo DLL. Para obtener más información, vea [Soluciones y proyectos](/visualstudio/ide/solutions-and-projects-in-visual-studio).  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   Para completar este tutorial, debe comprender los conceptos básicos del lenguaje C++.  
  
## <a name="creating-a-project"></a>Crear un proyecto  
 Para crear un proyecto, primero elija una plantilla del tipo de proyecto. Para cada tipo de proyecto, Visual Studio establece la configuración del compilador y, dependiendo del tipo, genera código de inicio que se puede modificar más adelante.  
  
#### <a name="to-create-a-project"></a>Para crear un proyecto  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, expanda el **plantillas instaladas** nodo, expanda el **Visual C++** nodo y, a continuación, seleccione **Win32**.  
  
3.  En la lista de plantillas instaladas en el panel central, seleccione **aplicación de consola Win32**.  
  
4.  Escriba un nombre para el proyecto en el **nombre** cuadro. En este ejemplo, escriba **juego**.  
  
     Puede aceptar la ubicación predeterminada en la **ubicación** la lista desplegable, escriba una ubicación diferente o elija la **examinar** botón para desplazarse a un directorio donde desea guardar el proyecto.  
  
     Cuando crea un proyecto, Visual Studio coloca el proyecto en una solución. De forma predeterminada, la solución tiene el mismo nombre que el proyecto. Puede cambiar el nombre de la **nombre de la solución** cuadro, pero en este ejemplo, conserve el nombre predeterminado.  
  
     Elija la **Aceptar** botón para iniciar la **Asistente para aplicaciones Win32**.  
  
5.  En el **Introducción** página de la **Asistente para aplicaciones Win32**, elija la **siguiente** botón.  
  
6.  En el **configuración de la aplicación** página, en **tipo de aplicación**, seleccione **aplicación de consola**. En **opciones adicionales**, desactive el **encabezado precompilado** configuración y, a continuación, seleccione la **proyecto vacío** configuración. Elija el botón **Finalizar** para crear el proyecto.  
  
     Ahora tiene un proyecto pero todavía no tiene los archivos de origen.  
  
## <a name="organizing-projects-and-files-in-a-solution"></a>Organización de proyectos y archivos en una solución  
 Puede usar **el Explorador de soluciones** para organizar y administrar los proyectos, archivos y otros recursos de la solución.  
  
 Esta parte del tutorial muestra cómo agregar una clase al proyecto. Cuando se agrega la clase, Visual Studio agrega los archivos de .cpp y .h correspondiente. A continuación, agregue un archivo de origen nuevo para el programa principal que prueba la clase.  
  
#### <a name="to-add-a-class-to-a-project"></a>Para agregar una clase a un proyecto  
  
1.  Si **el Explorador de soluciones** no es aparece, en la barra de menús, elija **vista**, **el Explorador de soluciones**.  
  
2.  En **el Explorador de soluciones**, abra el menú contextual para el **archivos de encabezado** carpeta y, a continuación, elija **agregar**, **clase**.  
  
     En el panel izquierdo de la **Agregar clase** cuadro de diálogo, expanda el **Visual C++** nodo y seleccione **C++**y, a continuación, en la lista de plantillas instaladas en el panel central, seleccione  **Clase de C++**. Elija el botón de **Agregar** .  
  
3.  En el **Asistente de clases genéricas de C++**, escriba **Cardgame** en el **nombre de la clase** cuadro. No modifique los nombres y valores del archivo predeterminado. Elija la **finalizar** botón.  
  
4.  El archivo Cardgame.h se abrirá en el editor. Efectúe estos cambios:  
  
    -   Agregue dos miembros de datos privados después de la llave de apertura de la definición de clase.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)]  
  
    -   Modifique el constructor predeterminado generado por Visual Studio. Después del especificador de acceso de `public:`, busque la línea con el siguiente aspecto:  
  
         `Cardgame(void);`  
  
         Modifíquela para tomar un parámetro de tipo `int`, que se denomina **reproductores**.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]  
  
    -   Después del destructor predeterminado, agregue una declaración alineada para una función de miembro int denominada **GetParticipants** que no toma ningún parámetro y devuelve el **totalParticipants** valor.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]  
  
5.  El archivo Cardgame.h se debería parecer a este al cambiarlo:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]  
  
     La línea `#pragma once` indica al compilador que incluya el archivo solo una vez. Para obtener más información, consulte [una vez](../preprocessor/once.md).  
  
     Para obtener información sobre otras palabras clave de C++ de este archivo de encabezado, vea [clase](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [estático](../cpp/storage-classes-cpp.md), y [público](../cpp/public-cpp.md).  
  
6.  Elija la **Cardgame.cpp** ficha en el panel de edición para abrirlo y editarlo.  
  
7.  Elimine todo lo que contenga el archivo y sustitúyalo por este código:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]  
  
    > [!NOTE]
    >  Puede utilizar la función de autocompletar mientras escribe código. Por ejemplo, si escribiera este código, puede escribir **pl** o **tot** y, a continuación, presione CTRL+BARRA ESPACIADORA para que la función de Autocompletar escriba `players` o `totalParticipants` para usted.  
  
     Para obtener información acerca de `#include`, consulte [#include (directiva) (C/C ++)](../preprocessor/hash-include-directive-c-cpp.md).  
  
## <a name="adding-a-source-file"></a>Agregar un archivo de código fuente  
 Ahora, agregue un archivo de origen para el programa principal que prueba la clase.  
  
#### <a name="to-add-a-new-source-file"></a>Para agregar un nuevo archivo de código fuente  
  
1.  En **el Explorador de soluciones**, abra el menú contextual para el **archivos de código fuente** carpeta y, a continuación, elija **agregar**, **nuevo elemento**.  
  
     En el **Agregar nuevo elemento** cuadro de diálogo, en el panel izquierdo, expanda el **instalado** nodo, expanda el **Visual C++** nodo y, a continuación, seleccione **código**. En el panel central, seleccione **Archivo de C++ (.cpp)**.  
  
2.  Escriba **TestGames.cpp** en el **nombre** cuadro y, a continuación, elija la **agregar** botón.  
  
3.  En la ventana de edición de TestGames.cpp, escriba el siguiente código.  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]  
  
## <a name="building-and-running-a-project"></a>Compilación y ejecución de un proyecto  
 Ahora, compile el proyecto y ejecute la aplicación.  
  
#### <a name="to-build-and-run-the-project"></a>Para compilar y ejecutar el proyecto  
  
1.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
    > [!NOTE]
    >  Si está usando una edición de Express que no se muestra un **generar** menú, en la barra de menús, elija **herramientas**, **configuración**, **configuración para expertos**para habilitarla.  
  
     Resultado de una compilación se muestra en el **salida** ventana. Si la compilación es correcta, el resultado debería ser similar a este:  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Cardgame.cpp  
    1>  Generating Code...  
    1>  Game.vcxproj -> c:\users\username\documents\visual studio\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
  
    ```  
  
     El **salida** ventana puede mostrar pasos diferentes, dependiendo de la edición y la configuración de compilación, pero si se realiza correctamente la compilación del proyecto, la última línea debe ser similar a la salida mostrada.  
  
     Si la compilación no es correcta, compare su código con el código proporcionado en los pasos anteriores.  
  
2.  Para ejecutar el proyecto, en la barra de menús, elija **Depurar**, **Iniciar sin depurar**. El resultado debería ser similar a lo siguiente:  
  
    ```Output  
    4 players have started a new game.  There are now 4 players in total.  
    8 players have started a new game.  There are now 12 players in total.  
    1 players have started a new game.  There are now 13 players in total.  
    5 players have started a new game.  There are now 18 players in total.  
    ```  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). **Siguiente:**[Tutorial: compilar un proyecto (C++)](../ide/walkthrough-building-a-project-cpp.md).  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)