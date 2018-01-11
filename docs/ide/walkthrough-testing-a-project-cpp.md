---
title: 'Tutorial: Probar un proyecto (C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- project testing [C++]
- testing projects
- projects [C++], testing
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2ba928d4a81252b76856273160af63ed8707e7e5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-testing-a-project-c"></a>Tutorial: Probar un proyecto (C++)
Al ejecutar un programa en modo de depuración, puede usar los puntos de interrupción para detener el programa para examinar el estado de las variables y objetos.  
  
 En este tutorial, comprueba el valor de una variable mientras se ejecuta el programa y deducirá por qué el valor es no es el esperado.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.  
  
-   También se supone que ha completado los tutoriales anteriores relacionados en la que se muestran en [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-run-a-program-in-debug-mode"></a>Para ejecutar un programa en modo de depuración  
  
1.  Abra TestGames.cpp para su edición.  
  
2.  Seleccione esta línea de código:  
  
     `Cardgame.solitaire(1);`  
  
3.  Para establecer un punto de interrupción en esa línea, en la barra de menús, elija **depurar**, **Alternar puntos de interrupción**, o presione la tecla F9. Aparece un círculo rojo a la izquierda de la línea; indica que se establece un punto de interrupción. Para quitar un punto de interrupción, puede elegir el comando de menú o la tecla F9 nuevo.  
  
     Si está usando un mouse, también puede establecer o quitar un punto de interrupción, haga clic en el margen izquierdo.  
  
4.  En la barra de menús, elija **depurar**, **Iniciar depuración**, o presione la tecla F5.  
  
     Cuando el programa llega a la línea que tiene el punto de interrupción, ejecución se detiene temporalmente, porque el programa está en modo de interrupción. Una flecha amarilla situada a la izquierda de una línea de código indica que es la siguiente línea que se ejecutará.  
  
5.  Para examinar el valor de la `Cardgame::totalParticipants` variable, mueva el puntero sobre `Cardgame` y, a continuación, se mueve sobre el control de expansión de la izquierda de la ventana de información sobre herramientas. El nombre de variable `totalParticipants` y se muestra su valor de 12.  
  
     Abra el menú contextual para el `Cardgame::totalParticipants` variable y, a continuación, elija **Agregar inspección** para mostrar esa variable en el **Inspección 1** ventana. También puede seleccionar una variable y arrástrelo hasta el **Inspección 1** ventana.  
  
6.  Para conocer los pasos a la siguiente línea de código, en la barra de menús, elija **depurar**, **paso a paso por**, o presione la tecla F10.  
  
     El valor de `Cardgame::totalParticipants` en el **Inspección 1** ventana aparece ahora como 13.  
  
7.  Abra el menú contextual para el `return 0;` instrucción y, a continuación, elija **ejecutar hasta el Cursor**. La flecha amarilla a la izquierda de los puntos de código a la siguiente instrucción que se ejecutará.  
  
8.  El `Cardgame::totalParticipants` debe reducir el número cuando finaliza un Cardgame. En este momento, `Cardgame::totalParticipants` debe ser igual a 0 porque se han eliminado todas las instancias de Cardgame, pero la **Inspección 1** ventana indica que `Cardgame::totalparticipants` es igual a 18. Esto indica que hay un error en el código, que puede detectar y corregir tras completar el tutorial siguiente, [Tutorial: depurar un proyecto (C++)](../ide/walkthrough-debugging-a-project-cpp.md).  
  
9. Para detener el programa, en la barra de menús, elija **depurar**, **Detener depuración**, o elija el método abreviado de teclado de MAYÚS + F5.  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [Tutorial: compilar un proyecto (C++)](../ide/walkthrough-building-a-project-cpp.md) &#124; **Siguiente:**[Tutorial: depurar un proyecto (C++)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)