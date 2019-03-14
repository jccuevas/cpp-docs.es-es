---
title: 'Tutorial: Depuración de un proyecto (C++)'
ms.date: 09/14/2018
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
ms.openlocfilehash: 4cd0f81ccf768938d585c206d5f50b20f6a0ae19
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741351"
---
# <a name="walkthrough-debugging-a-project-c"></a>Tutorial: Depuración de un proyecto (C++)

En este tutorial, modificará el programa para corregir el problema que detectó al probar el proyecto.

## <a name="prerequisites"></a>Requisitos previos

- En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.

- También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

### <a name="to-fix-a-program-that-has-a-bug"></a>Para corregir un programa que presenta un error

1. Para ver lo que ocurre cuando se destruye un objeto `Cardgame`, vea el destructor para la clase `Cardgame`.

   En la barra de menús, seleccione **Ver** > **Vista de clases**.

   En la ventana **Vista de clases**, expanda el árbol de proyecto **Game** y seleccione la clase **Cardgame** para mostrar los miembros y métodos de la clase.

   Abra el menú contextual del destructor **~Cardgame(void)** y después seleccione **Ir a definición**.

1. Para disminuir el valor de `totalParticipants` cuando finaliza un Cardgame, agregue el código siguiente entre las llaves de apertura y de cierre del destructor `Cardgame::~Cardgame`.

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]

1. El archivo Cardgame.cpp debería ser similar al código siguiente después de cambiarlo:

   [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]

1. En la barra de menús, elija **Compilar** > **Compilar solución**.

1. Cuando se complete la compilación, ejecútela en modo de depuración eligiendo **Depurar** > **Iniciar depuración** en la barra de menús, o bien presionando la tecla **F5**. El programa se detiene en el primer punto de interrupción.

1. Para recorrer paso a paso el programa, en la barra de menús, seleccione **Depurar** > **Paso a paso por procedimientos**, o bien presione la tecla **F10**.

   Observe que después de ejecutarse cada constructor de `Cardgame`, el valor de `totalParticipants` se incrementa. Cuando la función `PlayGames` vuelve, a medida que cada instancia de `Cardgame` sale del ámbito y se elimina y se llama al destructor, el valor de `totalParticipants` disminuye. Justo antes de que se ejecute la instrucción `return`, `totalParticipants` es igual a 0.

1. Siga recorriendo el programa hasta que se cierre o déjelo que se ejecute seleccionando **Depurar** > **Ejecutar** en la barra de menús, o bien presione la tecla **F5**.

## <a name="next-steps"></a>Pasos siguientes

**Anterior:** [Tutorial: Probar un proyecto (C++)](../ide/walkthrough-testing-a-project-cpp.md)<br/>
**Siguiente:** [Tutorial: Implementar el programa (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>

## <a name="see-also"></a>Vea también

[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Compilación de programas de C/C++](../build/building-c-cpp-programs.md)<br/>
