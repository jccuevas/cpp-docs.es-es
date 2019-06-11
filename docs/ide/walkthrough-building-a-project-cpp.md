---
title: 'Tutorial: Compilación de un proyecto (C++)'
ms.date: 04/25/2019
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
ms.openlocfilehash: ea477e7b2f5435e049b242e68d151cc1f2d20624
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182695"
---
# <a name="walkthrough-building-a-project-c"></a>Tutorial: Compilación de un proyecto (C++)

En este tutorial, va a introducir deliberadamente un error de sintaxis de C++ en el código para obtener información acerca de cómo es un error de compilación y cómo corregirlo. Cuando compila el proyecto, un mensaje de error indica cuál es el problema y donde se produjo.

## <a name="prerequisites"></a>Requisitos previos

- En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.

- También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-compilation-errors"></a>Para corregir errores de compilación

1. En Game.cpp, elimine el punto y coma de la última línea para que tenga un aspecto similar a la instrucción:

   `return 0`

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

1. Un mensaje en la ventana **Lista de errores** indica que se produjo un error en la compilación del proyecto. La descripción se parecerá al mensaje de error:

   `error C2143: syntax error: missing ';' before '}'`

   Para ver la información de ayuda sobre este error, resáltelo en la ventana **Lista de errores** y después presione la tecla **F1**.

1. Vuelva a agregar el punto y coma al final de la línea que tiene el error de sintaxis:

   `return 0;`

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

   Un mensaje en la ventana **Salida** indica que el proyecto se compiló correctamente.

    ```Output
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------
    1>Game.cpp
    1>Game.vcxproj -> C:\Users\<username>\source\repos\Game\Debug\Game.exe
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
    ```

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [Tutorial: Trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md)<br/>
**Siguiente:** [Tutorial: Probar un proyecto (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Proyectos y sistemas de compilación](../build/projects-and-build-systems-cpp.md)<br/>
