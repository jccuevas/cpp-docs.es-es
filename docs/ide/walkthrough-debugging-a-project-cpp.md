---
title: "Tutorial: Depurar un proyecto (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "depurar proyectos"
  - "depuración de proyectos [C++]"
  - "proyectos [C++], depurar"
ms.assetid: a5cade77-ba51-4b03-a7a0-6897e3cd6a59
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Depurar un proyecto (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tutorial, modificará el programa para corregir el problema que detectó al probar el proyecto.  
  
## Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C\+\+.  
  
-   También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### Para corregir un programa que presenta un error  
  
1.  Para ver lo que ocurre cuando se destruye un objeto `Cardgame`, vea el destructor para la clase `Cardgame`.  
  
     En la barra de menús, elija **Ver**, **Vista de clases**.  
  
     En la ventana **Vista de clases**, expanda el árbol de proyecto **Game** y seleccione la clase **Cardgame** para mostrar los miembros y métodos de la clase.  
  
     Abra el menú contextual del destructor **~Cardgame\(void\)** y después elija **Ir a definición**.  
  
2.  Para disminuir el valor de `totalParticipants` cuando finaliza un Cardgame, agregue el código siguiente entre las llaves de apertura y de cierre del destructor `Cardgame::~Cardgame`.  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#110](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_1.cpp)]  
  
3.  El archivo Cardgame.cpp se debería parecer a este al cambiarlo:  
  
     [!code-cpp[NVC_Walkthrough_Debugging_A_Project#111](../ide/codesnippet/CPP/walkthrough-debugging-a-project-cpp_2.cpp)]  
  
4.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
5.  Cuando se complete la compilación, ejecútela en modo de depuración eligiendo **Depurar**, **Iniciar depuración** en la barra de menús, o eligiendo la tecla F5.  El programa se detiene en el primer punto de interrupción.  
  
6.  Para recorrer paso a paso el programa, en la barra de menús, elija **Depurar**, **Paso a paso por procedimientos**, o elija la tecla F10.  
  
     Observe que después de ejecutarse cada constructor de Cardgame, el valor de `totalParticipants` se incrementa.  Cuando la función `PlayGames` vuelve, a medida que cada instancia de Cardgame sale del ámbito y se elimina \(y se llama al destructor\), el valor de `totalParticipants` disminuye.  Justo antes de que se ejecute la instrucción `return`, `totalParticipants` es igual a 0.  
  
7.  Siga recorriendo el programa hasta que se cierre o déjelo que se ejecute eligiendo **Depurar**, **Ejecutar** en la barra de menús, o eligiendo la tecla F5.  
  
## Pasos siguientes  
 **Anterior:** [Tutorial: Probar un proyecto \(C\+\+\)](../ide/walkthrough-testing-a-project-cpp.md) &#124; **Siguiente:** [Tutorial: Implementar el programa \(C\+\+\)](../ide/walkthrough-deploying-your-program-cpp.md)  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/es-es/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)