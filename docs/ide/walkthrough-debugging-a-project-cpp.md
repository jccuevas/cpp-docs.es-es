---
title: 'Tutorial: Depurar un proyecto (C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- projects [C++], debugging
- project debugging [C++]
- debugging projects
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6c9789a7deafacf09ad615f416a446da4eba8150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-debugging-a-project-c"></a>Tutorial: Depurar un proyecto (C++)
En este tutorial, modificará el programa para corregir el problema que detectó al probar el proyecto.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.  
  
-   También se supone que ha completado los tutoriales anteriores relacionados en la que se muestran en [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-a-program-that-has-a-bug"></a>Para corregir un programa que presenta un error  
  
1.  Para ver lo que ocurre cuando se destruye un objeto `Cardgame`, vea el destructor para la clase `Cardgame`.  
  
     En la barra de menús, elija **vista**, **vista de clases**.  
  
     En el **vista de clases** ventana, expanda la **juego** árbol del proyecto y seleccione el **Cardgame** clase para mostrar los miembros de clases y métodos.  
  
     Abra el menú contextual para el **~Cardgame(void)** destructor y, a continuación, elija **ir a definición**.  
  
2.  Para disminuir el valor de `totalParticipants` cuando finaliza un Cardgame, agregue el código siguiente entre las llaves de apertura y de cierre del destructor `Cardgame::~Cardgame`.  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  El archivo Cardgame.cpp se debería parecer a este al cambiarlo:  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
5.  Cuando se complete la compilación, ejecútela en modo de depuración eligiendo **depurar**, **Iniciar depuración** en la barra de menús, o eligiendo la tecla F5. El programa se detiene en el primer punto de interrupción.  
  
6.  Para conocer los pasos a través del programa, en la barra de menús, elija **depurar**, **paso a paso por**, o presione la tecla F10.  
  
     Observe que después de ejecutarse cada constructor de Cardgame, el valor de `totalParticipants` se incrementa. Cuando la función `PlayGames` vuelve, a medida que cada instancia de Cardgame sale del ámbito y se elimina (y se llama al destructor), el valor de `totalParticipants` disminuye. Justo antes de que se ejecute la instrucción `return`, `totalParticipants` es igual a 0.  
  
7.  Continuar la ejecución paso a paso el programa hasta que se cierre o deje que se ejecute eligiendo **depurar**, **ejecutar** en la barra de menús, o eligiendo la tecla F5.  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [Tutorial: probar un proyecto (C++)](../ide/walkthrough-testing-a-project-cpp.md) &#124; **Siguiente:**[Tutorial: implementar el programa (C++)](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)