---
title: 'Tutorial: Trabajar con proyectos y soluciones (C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 12/13/2017
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
ms.workload: cplusplus
ms.openlocfilehash: a20c0ee933d49465a841b638a8260181d7175ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-working-with-projects-and-solutions-c"></a>Tutorial: Trabajar con proyectos y soluciones (C++)

A continuación puede encontrar información de cómo crear un proyecto de C++ en Visual Studio, agregar código y compilar y ejecutar el proyecto. El proyecto de este tutorial es un programa que realiza un seguimiento de cuántos jugadores están jugando a distintos juegos de cartas.

En Visual Studio, el trabajo se organiza en proyectos y soluciones. Una solución puede contener más de un proyecto; por ejemplo, un archivo DLL y una aplicación ejecutable que haga referencia a ese archivo DLL. Para obtener más información, vea [Soluciones y proyectos](/visualstudio/ide/solutions-and-projects-in-visual-studio).

## <a name="before-you-start"></a>Antes de empezar

Para completar este tutorial, necesita Visual Studio 2017 versión 15,3 o posterior. Si necesita una copia, ésta es una guía breve: [compatibilidad instalar C++ en Visual Studio](../build/vscpp-step-0-installation.md). Si aún no lo ha hecho aún, siga los pasos siguientes después de la instalación el tutorial "Hello, World" para asegurarse de que Visual C++ está instalado correctamente y todo funciona.

Resulta útil si conoce los fundamentos del lenguaje C++ y sabe un compilador, vinculador y un depurador para qué se utilizan. El tutorial también se supone que está familiarizado con Windows y cómo usar los menús, cuadros de diálogo,

## <a name="create-a-project"></a>Crear un proyecto

Para crear un proyecto, primero elija una plantilla del tipo de proyecto. Para cada tipo de proyecto, Visual Studio establece la configuración del compilador y, dependiendo del tipo, genera código de inicio que se puede modificar más adelante.

### <a name="to-create-a-project"></a>Para crear un proyecto

1. En la barra de menús, elija **archivo > Nuevo > proyecto**.

1. En el panel izquierdo de la **nuevo proyecto** cuadro de diálogo, expanda **instalado** y seleccione **Visual C++**, si no está abierto ya.

1. En la lista de plantillas instaladas en el panel central, seleccione **aplicación de consola de Windows**.

1. Escriba un nombre para el proyecto en el **nombre** cuadro. En este ejemplo, escriba **juego**.

   Puede aceptar la ubicación predeterminada en la **ubicación** la lista desplegable, escriba una ubicación diferente o elija la **examinar** botón para desplazarse a un directorio donde desea guardar el proyecto.

   Cuando crea un proyecto, Visual Studio coloca el proyecto en una solución. De forma predeterminada, la solución tiene el mismo nombre que el proyecto. Puede cambiar el nombre de la **nombre de la solución** cuadro, pero en este ejemplo, conserve el nombre predeterminado.

1. Seleccione el botón **Aceptar** para crear el proyecto.

   Visual Studio crea la nueva solución y archivos de proyecto y abre el editor para el archivo de código fuente de Game.cpp que genera.

## <a name="organize-projects-and-files"></a>Organizar los proyectos y archivos

Puede usar **el Explorador de soluciones** para organizar y administrar los proyectos, archivos y otros recursos de la solución.

Esta parte del tutorial muestra cómo agregar una clase al proyecto. Cuando se agrega la clase, Visual Studio agrega los archivos de .cpp y .h correspondiente. Puede ver los resultados en **el Explorador de soluciones**.

### <a name="to-add-a-class-to-a-project"></a>Para agregar una clase a un proyecto

1. Si el **el Explorador de soluciones** ventana no se muestra en Visual Studio, en la barra de menús, elija **Vista > Explorador de soluciones**.

1. En **el Explorador de soluciones**, seleccione la **juego** proyecto. En la barra de menús, elija **proyecto > Agregar clase**.

1. En el **Agregar clase** cuadro de diálogo, escriba *Cardgame* en el **nombre de la clase** cuadro. No modifique los nombres y valores del archivo predeterminado. Elija el botón **Aceptar** .

   Visual Studio crea nuevos archivos y agrega a su proyecto. Podrá verlas en el **el Explorador de soluciones** ventana. Los archivos Cardgame.h y Cardgame.cpp se abren en el editor.

1. Editar el archivo Cardgame.h y realice estos cambios:

   - Agregue dos miembros de datos privados después de la llave de apertura de la definición de clase.
      <!--      [!code-cpp[NVC_Walkthrough_Working_With_Projects#100](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_1.h)] -->

      ```cpp
      int players;
      static int totalParticipants;
      ```

   - Modifique el constructor predeterminado generado por Visual Studio. Después del especificador de acceso de `public:`, busque la línea con el siguiente aspecto:

      `Cardgame();`

      Modifique este constructor para tomar un parámetro de tipo `int`, que se denomina *reproductores*.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#101](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_2.h)]-->
      `Cardgame(int players);`

   - Después del destructor predeterminado, agregue una declaración alineada para una `static int` función miembro denominada *GetParticipants* que no toma ningún parámetro y devuelve el `totalParticipants` valor.

      <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#102](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_3.h)]-->
      `static int GetParticipants() { return totalParticipants; }`

   El archivo Cardgame.h se debería parecer a este al cambiarlo:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#103](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_4.h)]-->
   ```cpp
   #pragma once
   class Cardgame
   {
       int players;
       static int totalParticipants;
   public:
       Cardgame(int players);
       ~Cardgame(void);
       static int GetParticipants() { return totalParticipants; }
   };
   ```

   La línea `#pragma once` indica al compilador que incluya el archivo de encabezado solo una vez. Para obtener más información, consulte [una vez](../preprocessor/once.md). Para obtener información sobre otras palabras clave de C++ de este archivo de encabezado, vea [clase](../cpp/class-cpp.md), [int](../cpp/fundamental-types-cpp.md), [estático](../cpp/storage-classes-cpp.md), y [público](../cpp/public-cpp.md).

1. Elija la **Cardgame.cpp** ficha en la parte superior del panel de edición para abrirlo y editarlo.

1. Elimine todo lo que contenga el archivo y sustitúyalo por este código:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#111](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_5.cpp)]-->
   ```cpp
   #include "stdafx.h"
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
   > Puede utilizar la función de autocompletar mientras escribe código. Por ejemplo, si escribe este código en el teclado, puede escribir *pl* o *tot* y, a continuación, presione Ctrl + barra espaciadora. Finalización automática entra en `players` o `totalParticipants` para usted.

## <a name="add-test-code-to-your-main-function"></a>Agregue el código de prueba a la función principal

Agregar código a la aplicación que prueba las nuevas funciones.

### <a name="to-add-test-code-to-the-project"></a>Para agregar código de prueba al proyecto

1. En la ventana del editor Game.cpp, reemplace el código existente a este:

   <!--[!code-cpp[NVC_Walkthrough_Working_With_Projects#120](../ide/codesnippet/CPP/walkthrough-working-with-projects-and-solutions-cpp_6.cpp)]-->
   ```cpp
   // Game.cpp : Defines the entry point for the console application.
   //

   #include "stdafx.h"
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
Este código agrega una función de prueba, `PlayGames`, para el código fuente y las llamadas en `main`. 

## <a name="build-and-run-your-app-project"></a>Compilar y ejecutar el proyecto de aplicación

A continuación, compile el proyecto y ejecutar la aplicación.

### <a name="to-build-and-run-the-project"></a>Para compilar y ejecutar el proyecto

1. En la barra de menús, elija **Compilar > Compilar solución**.

   Resultado de una compilación se muestra en el **salida** ventana. Si la compilación es correcta, el resultado debería ser similar a este:

   ```Output
   1>------ Build started: Project: Game, Configuration: Debug Win32 ------
   1>  stdafx.cpp
   1>  Game.cpp
   1>  Cardgame.cpp
   1>  Generating Code...
   1>  Game.vcxproj -> C:\Users\username\Source\Repos\Game\Debug\Game.exe
   ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
   ```

   El **salida** ventana puede mostrar pasos diferentes, dependiendo de la configuración de compilación, pero si se realiza correctamente la compilación del proyecto, la última línea debe ser similar a la salida mostrada.

   Si la compilación no es correcta, compare su código con el código que se muestra en los pasos anteriores.

1. Para ejecutar el proyecto, en la barra de menús, elija **Depurar > Iniciar sin depurar**. Debe aparecer una ventana de consola y el resultado debería ser similar a este:

   ```Output
   4 players have started a new game.  There are now 4 players in total.
   8 players have started a new game.  There are now 12 players in total.
   1 players have started a new game.  There are now 13 players in total.
   5 players have started a new game.  There are now 18 players in total.
   ```
Presione una tecla para cerrar la ventana de consola.

Enhorabuena, ha generado correctamente un proyecto de aplicación y la solución. Seguir el tutorial para obtener más información sobre cómo crear proyectos de código de C++ en Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
**Siguiente:** [Tutorial: compilar un proyecto (C++)](../ide/walkthrough-building-a-project-cpp.md).

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)  
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)