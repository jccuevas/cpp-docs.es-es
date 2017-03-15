---
title: "Tutorial: Probar un proyecto (C++) | Microsoft Docs"
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
  - "pruebas de proyectos [C++]"
  - "proyectos [C++], pruebas"
  - "probar proyectos"
ms.assetid: 88cdd377-c5c8-4201-889d-32f5653ebead
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Probar un proyecto (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando ejecuta un programa en modo de depuración, puede utilizar los puntos de interrupción para detener el programa y examinar el estado de variables y objetos.  
  
 En este tutorial, va a observar el valor de una variable cuando se ejecuta el programa y deducirá por qué el valor no es el esperado.  
  
## Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C\+\+.  
  
-   También supone que ha completado los tutoriales relacionados anteriores que se enumeran en [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### Para ejecutar un programa en modo de depuración  
  
1.  Abrir TestGames.cpp para edición.  
  
2.  Seleccione esta línea de código:  
  
     `Cardgame.solitaire(1);`  
  
3.  Para establecer un punto de interrupción en esa línea, en la barra de menús, elija **Depuración**, **Alternar puntos de interrupción** o elija la tecla F9.  Un círculo rojo a la izquierda de la línea; indicando que un punto de interrupción está establecido.  Para quitar un punto de interrupción, puede elegir el comando de menú o la tecla F9 de nuevo.  
  
     Si usa un mouse, también puede establecer o quitar un punto de interrupción haciendo clic en el margen izquierdo.  
  
4.  En la barra de menú, elija **Depurar**, **Iniciar depuración**, o elija la tecla F5.  
  
     Cuando el programa llega a la línea que tiene el punto de interrupción, la ejecución se detiene temporalmente, porque el programa está en modo de interrupción.  Una flecha amarilla situada a la izquierda de una línea de código indica que esa es la próxima línea que se va a ejecutar.  
  
5.  Para examinar el valor de la variable `Cardgame::totalParticipants`, mueva el puntero sobre `Cardgame` y después muévalo sobre el control de la extensión a la izquierda de la ventana de la información sobre herramientas.  Se muestran el nombre de variable `totalParticipants` y el valor 12.  
  
     Abra el menú contextual para la variable de `Cardgame::totalParticipants` y después elija **Agregar inspección** para mostrar esa variable en la ventana de **Inspección 1**.  También puede seleccionar una variable y arrastrarla a la ventana **Inspección 1**.  
  
6.  Para ir a la línea siguiente de código, en la barra de menús, elija **Depuración**, **Paso a paso por procedimientos** o elija la tecla F10.  
  
     El valor de `Cardgame::totalParticipants` en la ventana **Inspección 1** se muestra ahora como 13.  
  
7.  Abra el menú contextual para la instrucción de `return 0;` y después elija **Ejecutar hasta el Cursor**.  La flecha amarilla situada a la izquierda del código indica la siguiente instrucción que se va a ejecutar.  
  
8.  El número de `Cardgame::totalParticipants` debería disminuir cuando un Cardgame finaliza.  En este punto, `Cardgame::totalParticipants` debe ser igual a 0 porque se han eliminado todas las instancias Cardgame, pero la ventana **Inspección 1** indica que `Cardgame::totalparticipants` es igual a 18.  Esto indica que hay un error en el código, que puede detectar y corregir completando el tutorial siguiente, [Tutorial: Depurar un proyecto \(C\+\+\)](../ide/walkthrough-debugging-a-project-cpp.md).  
  
9. Para detener el programa, en la barra de menú, elija **Depurar**, **Detener depuración** o elija el método abreviado de teclado Mayús\+F5.  
  
## Pasos siguientes  
 **Anterior:** [Tutorial: Compilar un proyecto \(C\+\+\)](../ide/walkthrough-building-a-project-cpp.md) &#124; **Siguiente:** [Tutorial: Depurar un proyecto \(C\+\+\)](../ide/walkthrough-debugging-a-project-cpp.md)  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/es-es/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)