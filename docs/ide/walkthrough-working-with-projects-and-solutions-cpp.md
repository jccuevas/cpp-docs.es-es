---
title: 'Tutorial: Trabajar con proyectos y soluciones (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- solutions [C++]
- projects [C++], about projects
- projects [C++]
- solutions [C++], about solutions
ms.assetid: 93a3f290-e294-46e3-876e-e3084d9ae833
ms.openlocfilehash: 36c64a74310c72df38021aebd8abb3ee430da3f0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375894"
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Tutorial: Trabajar con proyectos y soluciones (C++)

A continuación puede encontrar información de cómo crear un proyecto de C++ en Visual Studio, agregar código y compilar y ejecutar el proyecto. El proyecto de este tutorial es un programa que realiza un seguimiento de cuántos jugadores están jugando a distintos juegos de cartas.

En Visual Studio, el trabajo se organiza en proyectos y soluciones. Una solución puede tener más de un proyecto; por ejemplo, un archivo DLL y una aplicación ejecutable que haga referencia a ese archivo DLL. Para obtener más información, vea [Soluciones y proyectos](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Antes de comenzar

Para completar este tutorial, necesita Visual Studio 2017 o posterior. Si necesita una copia, aquí tiene una guía breve: [Instalación de la compatibilidad con C++ en Visual Studio](../build/vscpp-step-0-installation.md). Si todavía no lo ha hecho, realice los siguientes pasos después de la instalación del tutorial "Hello, World" para asegurarse de que los componentes de C++ están instalados correctamente y de que funciona.

Resulta útil conocer los fundamentos del lenguaje C++ y saber para qué se usa un compilador, un vinculador y un depurador. En el tutorial también se supone que está familiarizado con Windows y cómo usar los menús y los cuadros de diálogo.

## <a name="create-a-project"></a>Crear un proyecto

Para crear un proyecto, primero elija una plantilla del tipo de proyecto. Para cada tipo de proyecto, Visual Studio establece la configuración del compilador y, en función del tipo, genera código de inicio que se puede modificar después. Los siguientes pasos varían según la versión de Visual Studio que use. Para ver la documentación de su versión preferida de Visual Studio, use el control Selector de **versiones.** Se encuentra en la parte superior de la tabla de contenido de esta página.

::: moniker range="vs-2019"

### <a name="to-create-a-project-in-visual-studio-2019"></a>Para crear un proyecto en Visual Studio 2019

1. En el menú principal, seleccione **Archivo** > **Nuevo** > **Proyecto** para abrir el cuadro de diálogo **Crear nuevo proyecto**.

1. En la parte superior del cuadro de diálogo, establezca **Lenguaje** en **C++ **, establezca **Plataforma** en **Windows** y establezca **Tipo de proyecto** en **Consola**.

1. En la lista de plantillas de proyecto, seleccione **Aplicación de consola** y **Siguiente**. En la siguiente página, escriba *Game* como nombre del proyecto.

   Puede aceptar la ubicación predeterminada en la lista desplegable **Ubicación**, escribir otra ubicación o hacer clic en el botón **Examinar** para ir a un directorio donde quiera guardar el proyecto.

   Cuando se crea un proyecto, Visual Studio lo coloca en una solución. De forma predeterminada, la solución tiene el mismo nombre que el proyecto. Puede cambiar el nombre en el cuadro **Nombre de la solución** pero, para este ejemplo, mantenga el nombre predeterminado.

1. Elija el botón **Crear** para crear el proyecto.

   Visual Studio crea la solución y los archivos de proyecto, y abre el editor para el archivo de código fuente Game.cpp que genera.

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017"></a>Para crear un proyecto en Visual Studio 2017

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** y seleccione **Visual C++**, si todavía no está abierto.

1. En la lista de plantillas instaladas en el panel central, seleccione **Aplicación de consola de Windows**.

1. Escriba un nombre para el proyecto en el cuadro **Nombre**. Para este ejemplo, escriba *Game*.

   Puede aceptar la ubicación predeterminada en la lista desplegable **Ubicación**, escribir otra ubicación o hacer clic en el botón **Examinar** para ir a un directorio donde quiera guardar el proyecto.

   Cuando se crea un proyecto, Visual Studio lo coloca en una solución. De forma predeterminada, la solución tiene el mismo nombre que el proyecto. Puede cambiar el nombre en el cuadro **Nombre de la solución** pero, para este ejemplo, mantenga el nombre predeterminado.

1. Seleccione el botón **Aceptar** para crear el proyecto.

   Visual Studio crea la solución y los archivos de proyecto, y abre el editor para el archivo de código fuente Game.cpp que genera.

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-project-in-visual-studio-2015"></a>Para crear un proyecto en Visual Studio 2015

1. En la barra de menús, seleccione **Archivo** > **Nuevo** > **Proyecto**.

1. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Instalado** y seleccione **Visual C++**, si todavía no está abierto.

1. En la lista de plantillas instaladas, en el panel central, seleccione **Aplicación de consola Win32**.

1. Escriba un nombre para el proyecto en el cuadro **Nombre**. Para este ejemplo, escriba *Game*.

   Puede aceptar la ubicación predeterminada en la lista desplegable **Ubicación**, escribir otra ubicación o hacer clic en el botón **Examinar** para ir a un directorio donde quiera guardar el proyecto.

   Cuando se crea un proyecto, Visual Studio lo coloca en una solución. De forma predeterminada, la solución tiene el mismo nombre que el proyecto. Puede cambiar el nombre en el cuadro **Nombre de la solución** pero, para este ejemplo, mantenga el nombre predeterminado.

1. Seleccione el botón **Aceptar** para crear el proyecto.

   Visual Studio crea la solución y los archivos de proyecto, y abre el editor para el archivo de código fuente Game.cpp que genera.

::: moniker-end

## <a name="organize-projects-and-files"></a>Organizar los proyectos y archivos

Puede usar el **Explorador de soluciones** para organizar y administrar los proyectos, archivos y otros recursos de la solución.

Esta parte del tutorial muestra cómo agregar una clase al proyecto. Al agregar la clase, Visual Studio agrega los archivos .h y .cpp correspondientes. Puede ver los resultados en el **Explorador de soluciones**.

### <a name="to-add-a-class-to-a-project"></a>Para agregar una clase a un proyecto

1. Si en Visual Studio no se muestra la ventana **Explorador de soluciones**, en la barra de menús, seleccione **Ver** > **Explorador de soluciones**.

1. En el **Explorador de soluciones**, seleccione el proyecto **Game**. En la barra de menús, elija Clase**de adición** **de proyecto** > .

1. En el cuadro de diálogo **Agregar clase,** escriba *Cardgame* en el cuadro Nombre de **clase.** No modifique los nombres y valores del archivo predeterminado. Elija el botón **Aceptar** .

   Visual Studio crea los archivos y los agrega al proyecto. Puede verlos en la ventana **Explorador de soluciones**. Los archivos Cardgame.h y Cardgame.cpp se abren en el editor.

1. Modifique el archivo Cardgame.h y realice estos cambios:

   - Agregue dos miembros de datos privados después de la llave de apertura de la definición de clase.
     <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Modifique el constructor predeterminado generado por Visual Studio. Después del especificador de acceso de `public:`, busque la línea con el siguiente aspecto:

      `Cardgame();`

      Modifique el constructor para tomar un parámetro del tipo `int`, denominado *players*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Después del destructor predeterminado, agregue una declaración insertada para una función miembro `static int` denominada *GetParticipants* que no tome parámetros y devuelva el valor `totalParticipants`.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   El archivo Cardgame.h debería ser similar al código siguiente después de cambiarlo:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->

    ```cpp
    #pragma once
    class Cardgame
    {
        int players;
        static int totalParticipants;
    public:
        Cardgame(int players);
        ~Cardgame();
        static int GetParticipants() { return totalParticipants; }
    };
    ```

   La línea `#pragma once` indica al compilador que incluya el archivo de encabezado solo una vez. Para obtener más información, vea [once](../preprocessor/once.md). Para obtener información sobre otras palabras clave de C++ del archivo de encabezado anterior, vea [class](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [static](../cpp/storage-classes-cpp.md) y [public](../cpp/public-cpp.md).

1. Haga clic en la pestaña **Cardgame.cpp** en la parte superior del panel de edición para abrirla para la edición.

1. Elimine todo lo que contenga el archivo y sustitúyalo por el código:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->

    ```cpp
    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    int Cardgame::totalParticipants = 0;

    Cardgame::Cardgame(int players)
        : players(players)
    {
        totalParticipants += players;
        cout << players << " players have started a new game.  There are now "
             << totalParticipants << " players in total." << endl;
    }

    Cardgame::~Cardgame()
    {
    }
    ```

   > [!NOTE]
   > Puede utilizar la función de autocompletar mientras escribe código. Por ejemplo, si introduce este código en el teclado, puede introducir *pl* o *tot* y, a continuación, presione **Ctrl**+**Barra espaciadora**. La finalización automática escribe `players` o `totalParticipants` por usted.

## <a name="add-test-code-to-your-main-function"></a>Agregar el código de prueba a la función principal

Agregue código a la aplicación para probar las funciones nuevas.

### <a name="to-add-test-code-to-the-project"></a>Para agregar código de prueba al proyecto

1. En la ventana del editor de **Game.cpp**, reemplace el código existente por:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->

    ```cpp
    // Game.cpp : Defines the entry point for the console application.
    //

    #include "pch.h" // remove this line in Visual Studio 2019
    #include "Cardgame.h"
    #include <iostream>

    using namespace std;

    void PlayGames()
    {
        Cardgame bridge(4);
        Cardgame blackjack(8);
        Cardgame solitaire(1);
        Cardgame poker(5);
    }

    int main()
    {
        PlayGames();
        return 0;
    }
    ```

   El código agrega una función de prueba, `PlayGames`, al código fuente y la llama en `main`.

## <a name="build-and-run-your-app-project"></a>Compilar y ejecutar el proyecto de aplicación

Después, compile el proyecto y ejecute la aplicación.

### <a name="to-build-and-run-the-project"></a>Para compilar y ejecutar el proyecto

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

   El resultado de una compilación se mostrará en la ventana **Salida**. Si la compilación es correcta, el resultado debería ser similar a:

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>pch.cpp
    1>Cardgame.cpp
    1>Game.cpp
    1>Generating Code...
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

   En la ventana **Salida** se pueden mostrar otros pasos, en función de la configuración de la compilación, pero si la compilación del proyecto se realiza correctamente, la última línea debe ser similar a la salida que se muestra.

   Si la compilación no es correcta, compare el código con el que se muestra en los pasos anteriores.

1. Para ejecutar el proyecto, en la barra de menús, elija **Depurar** > **iniciar sin depurar**. Debe aparecer una ventana de consola y el resultado debería ser similar a:

    ```Output
    4 players have started a new game.  There are now 4 players in total.
    8 players have started a new game.  There are now 12 players in total.
    1 players have started a new game.  There are now 13 players in total.
    5 players have started a new game.  There are now 18 players in total.
    ```

   Presione una tecla para cerrar la ventana de consola.

Enhorabuena, ha compilado correctamente un proyecto de aplicación y la solución. Continúe el tutorial para obtener más información sobre cómo compilar proyectos de código de C++ en Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** Uso del IDE de Visual Studio para el desarrollo de [escritorios de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)<br/>
**Siguiente:** [Tutorial: Creación de un proyecto (C++)](../ide/walkthrough-building-a-project-cpp.md)

## <a name="see-also"></a>Consulte también

[Referencia del idioma C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](../build/projects-and-build-systems-cpp.md)<br/>
