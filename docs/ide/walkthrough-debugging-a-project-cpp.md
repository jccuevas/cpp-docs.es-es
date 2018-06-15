---
title: 'Tutorial: Depurar un proyecto (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecfda5e2549b3aa9be1f0471e301cc2a21c6fd5a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340039"
---
# <a name="walkthrough-debugging-a-project-c"></a>Tutorial: Depurar un proyecto (C++)
En este tutorial, modificará el programa para corregir el problema que detectó al probar el proyecto.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.  
  
-   También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Usar el IDE de Visual Studio para desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-a-program-that-has-a-bug"></a>Para corregir un programa que presenta un error  
  
1.  Para ver lo que ocurre cuando se destruye un objeto `Cardgame`, vea el destructor para la clase `Cardgame`.  
  
     En la barra de menús, seleccione **Ver**, **Vista de clases**.  
  
     En la ventana **Vista de clases**, expanda el árbol de proyecto **Game** y seleccione la clase **Cardgame** para mostrar los miembros y métodos de la clase.  
  
     Abra el menú contextual del destructor **~Cardgame(void)** y después seleccione **Ir a definición**.  
  
2.  Para disminuir el valor de `totalParticipants` cuando finaliza un Cardgame, agregue el código siguiente entre las llaves de apertura y de cierre del destructor `Cardgame::~Cardgame`.  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  El archivo Cardgame.cpp se debería parecer a este al cambiarlo:  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
5.  Cuando se complete la compilación, ejecútela en modo de depuración eligiendo **Depurar**, **Iniciar depuración** en la barra de menús, o bien presionando la tecla F5. El programa se detiene en el primer punto de interrupción.  
  
6.  Para recorrer paso a paso el programa, en la barra de menús, seleccione **Depurar**, **Paso a paso por procedimientos**, o bien presione la tecla F10.  
  
     Observe que después de ejecutarse cada constructor de Cardgame, el valor de `totalParticipants` se incrementa. Cuando la función `PlayGames` vuelve, a medida que cada instancia de Cardgame sale del ámbito y se elimina (y se llama al destructor), el valor de `totalParticipants` disminuye. Justo antes de que se ejecute la instrucción `return`, `totalParticipants` es igual a 0.  
  
7.  Siga recorriendo el programa hasta que se cierre o déjelo que se ejecute seleccionando **Depurar**, **Ejecutar** en la barra de menús, o bien presione la tecla F5.  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [Tutorial: Probar un proyecto (C++)](../ide/walkthrough-testing-a-project-cpp.md) &#124; **Siguiente:**[Tutorial: Implementar el programa (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)