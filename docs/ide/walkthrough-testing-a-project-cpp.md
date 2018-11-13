---
title: 'Tutorial: Probar un proyecto (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
ms.openlocfilehash: a604d8ef0b44db04d9a6da8fdc959d08384f1bf3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437315"
---
# <a name="walkthrough-testing-a-project-c"></a>Tutorial: Probar un proyecto (C++)

Al ejecutar un programa en modo de depuración, se pueden usar puntos de interrupción para detener el programa para examinar el estado de las variables y los objetos.

En este tutorial, verá el valor de una variable mientras el programa se ejecuta y deducirá por qué el valor no es el esperado.

## <a name="prerequisites"></a>Requisitos previos

- En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.

- También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-run-a-program-in-debug-mode"></a>Para ejecutar el programa en modo de depuración

1. Abra Games.cpp para modificarlo.

1. Seleccione esta línea de código:

   `Cardgame.solitaire(1);`

1. Para establecer un punto de interrupción en esa línea, en la barra de menús, seleccione **Depurar** > **Alternar puntos de interrupción**, o bien presione la tecla **F9**. Aparece un círculo de color rojo a la izquierda de la línea; indica que se ha establecido un punto de interrupción. Para quitar un punto de interrupción, puede volver elegir el comando de menú o la tecla **F9**.

   Si usa un mouse, también puede establecer o quitar un punto de interrupción si hace clic en el margen izquierdo.

1. En la barra de menús, seleccione **Depurar** > **Iniciar depuración**, o bien presione la tecla **F5**.

   Cuando el programa llega a la línea que tiene el punto de interrupción, la ejecución se detiene temporalmente, porque el programa está en modo de interrupción. Una flecha de color amarillo situada a la izquierda de una línea de código indica que es la siguiente línea que se va a ejecutar.

1. Para examinar el valor de la variable `Cardgame::totalParticipants`, mueva el puntero sobre `Cardgame` y después sobre el control de expansión situado a la izquierda de la ventana de información sobre herramientas. Se muestra el nombre de la variable `totalParticipants` y su valor de **12**.

   Abra el menú contextual para la variable `Cardgame::totalParticipants` y, después, seleccione **Agregar inspección** para mostrar esa variable en la ventana **Inspección 1**. También puede resaltar una variable y arrastrarla hasta la ventana **Inspección 1**.

1. Para ejecutar paso a paso hasta la línea de código siguiente, en la barra de menús, seleccione **Depurar** > **Paso a paso por procedimientos**, o bien presione la tecla **F10**.

   Ahora el valor de `Cardgame::totalParticipants` en la ventana **Inspección 1** se muestra como **13**.

1. Abra el menú contextual de la instrucción `return 0;` y después seleccione **Ejecutar hasta el cursor**. La flecha de color amarillo situada a la izquierda del código apunta a la siguiente instrucción que se va a ejecutar.

1. El número `Cardgame::totalParticipants` debe reducirse cuando finalice un `Cardgame`. En este momento, `Cardgame::totalParticipants` debe ser igual a 0 porque se han eliminado todas las instancias de `Cardgame`, pero en la ventana **Inspección 1** se indica que `Cardgame::totalparticipants` es igual a **18**. La diferencia indica que hay un error en el código, que puede detectar y corregir tras completar el tutorial siguiente, [Tutorial: Depurar un proyecto (C++)](../ide/walkthrough-debugging-a-project-cpp.md).

1. Para detener el programa, en la barra de menús, seleccione **Depurar** > **Detener depuración**, o presione el método abreviado de teclado **Mayús**+**F5**.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [Tutorial: Compilar un proyecto (C++)](../ide/walkthrough-building-a-project-cpp.md)<br/>
**Siguiente:** [Tutorial: Depurar un proyecto (C++)](../ide/walkthrough-debugging-a-project-cpp.md)<br/>

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
