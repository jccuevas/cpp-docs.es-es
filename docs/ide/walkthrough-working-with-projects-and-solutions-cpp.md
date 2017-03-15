---
title: "Tutorial: Trabajar con proyectos y soluciones (C++) | Microsoft Docs"
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
  - "proyectos [C++]"
  - "proyectos [C++], acerca de los proyectos"
  - "soluciones [C++]"
  - "soluciones [C++], acerca de las soluciones"
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Trabajar con proyectos y soluciones (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A continuación puede encontrar información de cómo crear un proyecto de C\+\+ en Visual Studio, agregar código y compilar y ejecutar el proyecto.  El proyecto de este tutorial es un programa que realiza un seguimiento de cuántos jugadores están jugando a distintos juegos de cartas.  
  
 En [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)], el trabajo se organiza en proyectos y soluciones.  Una solución puede contener más de un proyecto; por ejemplo, un archivo DLL y una aplicación ejecutable que haga referencia a ese archivo DLL.  Para obtener más información, vea [Soluciones y proyectos](../Topic/Solutions%20and%20Projects%20in%20Visual%20Studio.md).  
  
## Requisitos previos  
  
-   Para completar este tutorial, debe comprender los conceptos básicos del lenguaje C\+\+.  
  
## Crear un proyecto  
 Para crear un proyecto, primero elija una plantilla del tipo de proyecto.  Para cada tipo de proyecto, [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] establece la configuración del compilador y, en función del tipo, genera código inicial que puede modificar después.  
  
#### Para crear un proyecto  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
2.  En el panel izquierdo del cuadro de diálogo de **Nuevo proyecto**, expanda el nodo **Plantillas instaladas**, expanda el nodo **Visual C\+\+** y, a continuación, seleccione **Win32**.  
  
3.  En la lista de plantillas instaladas en el panel central, seleccione **Aplicación de consola Win32**.  
  
4.  Escriba un nombre para el proyecto en el cuadro **Nombre**.  Para este ejemplo, escriba Game.  
  
     Puede aceptar la ubicación predeterminada en la lista desplegable de **Ubicación**, escribir una ubicación diferente o elegir el botón **Examinar** para ir a un directorio donde desee guardar el proyecto.  
  
     Cuando se crea un proyecto, [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] coloca el proyecto en una solución.  De forma predeterminada, la solución tiene el mismo nombre que el proyecto.  Puede cambiar el nombre en el cuadro **Nombre de la solución** pero, para este ejemplo, mantenga el nombre predeterminado.  
  
     Elija el botón **Aceptar** para iniciar el **Asistente para aplicaciones Win32**.  
  
5.  En la página **Información general** del **Asistente para aplicaciones Win32**, elija el botón **Siguiente**.  
  
6.  En la página **Configuración de la aplicación**, en **Tipo de aplicación**, seleccione **Aplicación de consola**.  En **Opciones adicionales**, desactive el valor **Encabezado precompilado** y, a continuación, seleccione la configuración de **Proyecto vacío**.  Elija el botón **Finalizar** para crear el proyecto.  
  
     Ahora tiene un proyecto pero todavía no tiene los archivos de origen.  
  
## Organización de proyectos y archivos en una solución  
 Puede utilizar el **Explorador de soluciones** para organizar y administrar los proyectos, archivos y otros recursos en su solución.  
  
 Esta parte del tutorial muestra cómo agregar una clase al proyecto.  Al agregar la clase, [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] agrega los archivos .h y .cpp correspondientes.  A continuación, agregue un archivo de origen nuevo para el programa principal que prueba la clase.  
  
#### Para agregar una clase a un proyecto  
  
1.  Si no aparece el **Explorador de soluciones**, en la barra de menús, elija **Ver**, **Explorador de soluciones**.  
  
2.  En el **Explorador de soluciones**, abra el menú contextual de la carpeta **Archivos de encabezado** y, después, elija **Agregar**, **Clase**.  
  
     En el panel izquierdo del cuadro de diálogo **Agregar clase**, expanda el nodo **Visual C\+\+** y seleccione **C\+\+** y, en la lista de plantillas instaladas en el panel central, seleccione **Clase de C**.  Elija el botón de **Agregar**.  
  
3.  En **Asistente para clases genéricas de C**, escriba Cardgame en el cuadro **Nombre de clase**.  No modifique los nombres y valores del archivo predeterminado.  Elija el botón **Finalizar**.  
  
4.  El archivo Cardgame.h se abrirá en el editor.  Efectúe estos cambios:  
  
    -   Agregue dos miembros de datos privados después de la llave de apertura de la definición de clase.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)]  
  
    -   Modifique el constructor predeterminado generado por Visual Studio.  Después del especificador de acceso de `public:`, busque la línea con el siguiente aspecto:  
  
         `Cardgame(void);`  
  
         Modifíquela para tomar un parámetro del tipo `int`, denominado jugadores.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]  
  
    -   Después del destructor predeterminado, agregue una declaración alineada para una función miembro int denominada GetParticipants que no tome parámetros y devuelva el valor totalParticipants.  
  
         [!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]  
  
5.  El archivo Cardgame.h se debería parecer a este al cambiarlo:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]  
  
     La línea `#pragma once` indica al compilador que incluya el archivo solo una vez.  Para obtener más información, vea [once](../preprocessor/once.md).  
  
     Para obtener información sobre otras palabras clave de C\+\+ de este archivo de encabezado, vea [clase](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [estático](../misc/static-cpp.md) y [público](../cpp/public-cpp.md).  
  
6.  Elija la pestaña **Cardgame.cpp** en el panel de edición para abrirlo y editarlo.  
  
7.  Elimine todo lo que contenga el archivo y sustitúyalo por este código:  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]  
  
    > [!NOTE]
    >  Puede utilizar la función de autocompletar mientras escribe código.  Por ejemplo, si escribiera este código, podría escribir pl o tot y, a continuación, presionar Ctrl\+barra espaciadora de forma que la función de autocompletar escriba `players` o `totalParticipants` automáticamente.  
  
     Para obtener información sobre `#include`, vea [\#include \(Directiva\)](../preprocessor/hash-include-directive-c-cpp.md).  
  
## Agregar un archivo de código fuente  
 Ahora, agregue un archivo de origen para el programa principal que prueba la clase.  
  
#### Para agregar un nuevo archivo de código fuente  
  
1.  En el **Explorador de soluciones**, abra el menú contextual de la carpeta **Archivos de código fuente** y, después, elija **Agregar**, **Nuevo elemento**.  
  
     En el cuadro de diálogo **Agregar nuevo elemento**, en el panel izquierdo, expanda el nodo **Instalado**, expanda el nodo **Visual C\+\+** y, a continuación, seleccione **Código**.  En el panel central, seleccione **Archivo de C\+\+ \(.cpp\)**.  
  
2.  Escriba TestGames.cpp en el cuadro **Nombre** y elija el botón **Agregar**.  
  
3.  En la ventana de edición de TestGames.cpp, escriba el siguiente código.  
  
     [!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]  
  
## Compilación y ejecución de un proyecto  
 Ahora, compile el proyecto y ejecute la aplicación.  
  
#### Para compilar y ejecutar el proyecto  
  
1.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
    > [!NOTE]
    >  Si usa una edición Express que no muestra un menú **Compilar**, en la barra de menús, elija **Herramientas**, **Configuración**, **Configuración para expertos** para habilitarla.  
  
     El resultado de una compilación se mostrará en la ventana **Resultado**.  Si la compilación es correcta, el resultado debería ser similar a este:  
  
  **1\>\-\-\-\-\-\- Operación Compilar iniciada: proyecto: Game, configuración: Debug Win32 \-\-\-\-\-\-**  
**1\>  TestGames.cpp**  
**1\>  Cardgame.cpp**  
**1\>  Generando código...**  
**1\>  Game.vcxproj \-\> c:\\users\\username\\documents\\visual studio\\Projects\\Game\\Debug\\Game.exe**  
**\=\=\=\=\=\=\=\=\=\= Compilación: 1 correctos, 0 incorrectos, 0 actualizados, 0 omitidos \=\=\=\=\=\=\=\=\=\=**     La ventana de **Resultados** puede mostrar pasos diferentes, dependiendo de la edición y de la configuración de la compilación, pero si la compilación del proyecto se realiza correctamente, la última línea debe ser similar al que se muestra.  
  
     Si la compilación no es correcta, compare su código con el código proporcionado en los pasos anteriores.  
  
2.  Para ejecutar el proyecto, en la barra de menús, elija **Depurar**, **Iniciar sin depurar**.  El resultado debería ser similar a lo siguiente:  
  
  **4 jugadores han iniciado un nuevo juego.  Ahora hay 4 jugadores en total.**  
**8 jugadores han iniciado un nuevo juego.  Ahora hay 12 jugadores en total.**  
**1 jugadores han iniciado un nuevo juego.  Ahora hay 13 jugadores en total.**  
**5 jugadores han iniciado un nuevo juego.  Ahora hay 18 jugadores en total.**  
  
## Pasos siguientes  
 **Anterior:** [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  **Siguiente:** [Tutorial: Compilar un proyecto \(C\+\+\)](../ide/walkthrough-building-a-project-cpp.md).  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)