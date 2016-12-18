---
title: "Tutorial: Compilar un proyecto (C++) | Microsoft Docs"
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
  - "compilar proyectos [C++]"
  - "proyectos [C++], compilar"
  - "compilación de proyectos [C++]"
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
caps.latest.revision: 14
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Tutorial: Compilar un proyecto (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tutorial, va a introducir deliberadamente un error de sintaxis de Visual C\+\+ en el código para obtener información acerca de cómo es un error de compilación y cómo corregirlo.  Cuando compila el proyecto, un mensaje de error indica cuál es el problema y donde se produjo.  
  
## Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C\+\+.  
  
-   También se presupone que ha completado los tutoriales relacionados anteriores que se enumeran en [Utilizar el IDE de Visual Studio para desarrollo de escritorio de C\+\+](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### Para corregir errores de compilación  
  
1.  En TestGames.cpp, elimine el punto y coma de la última línea para que presente un aspecto similar al siguiente:  
  
     `return 0`  
  
2.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
3.  Un mensaje en la ventana **Lista de errores** indica que se produjo un error en la compilación del proyecto.  La descripción se parecerá a la siguiente:  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     Para ver la información de ayuda sobre este error, resáltelo en la ventana **Lista de errores** y elija la tecla F1.  
  
4.  Vuelva a agregar el punto y coma al final de la línea que tiene el error de sintaxis:  
  
     `return 0;`  
  
5.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
     Un mensaje en la ventana **Resultados** indica que el proyecto se compiló correctamente.  
  
  **1\>\-\-\-\-\-\- Operación Compilar iniciada: proyecto: Game, configuración: Debug Win32 \-\-\-\-\-\-**  
**1\>  TestGames.cpp**  
**1\>  Game.vcxproj \-\> C:\\Users\\\<username\>\\Documents\\Visual Studio *\<version\>*\\Projects\\Game\\Debug\\Game.exe**  
**\=\=\=\=\=\=\=\=\=\= Compilación: 1 correctos, 0 incorrectos, 0 actualizados, 0 omitidos \=\=\=\=\=\=\=\=\=\=**  
  
## Pasos siguientes  
 **Anterior:** [Tutorial: Trabajar con proyectos y soluciones \(C\+\+\)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124; **Siguiente:** [Tutorial: Probar un proyecto \(C\+\+\)](../ide/walkthrough-testing-a-project-cpp.md)  
  
## Vea también  
 [Visual C\+\+ Guided Tour](http://msdn.microsoft.com/es-es/499cb66f-7df1-45d6-8b6b-33d94fd1f17c)   
 [DELETE\_PENDING\_Building and Debugging](http://msdn.microsoft.com/es-es/9f6ba537-5ea0-46fb-b6ba-b63d657d84f1)