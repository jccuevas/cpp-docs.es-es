---
title: 'Tutorial: Compilar un proyecto (C++) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- building projects [C++]
- projects [C++], building
- project building [C++]
ms.assetid: d459bc03-88ef-48d0-9f9a-82d17f0b6a4d
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 713a74cc889721259ca99f1622ef5e9919edf573
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="walkthrough-building-a-project-c"></a>Tutorial: Compilar un proyecto (C++)
En este tutorial, va a introducir deliberadamente un error de sintaxis de Visual C++ en el código para obtener información acerca de cómo es un error de compilación y cómo corregirlo. Cuando compila el proyecto, un mensaje de error indica cuál es el problema y donde se produjo.  
  
## <a name="prerequisites"></a>Requisitos previos  
  
-   En este tutorial se da por supuesto que conoce los fundamentos del lenguaje C++.  
  
-   También se supone que ha completado los tutoriales anteriores relacionados en la que se muestran en [mediante el IDE de Visual Studio para el desarrollo de escritorio de C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
### <a name="to-fix-compilation-errors"></a>Para corregir errores de compilación  
  
1.  En TestGames.cpp, elimine el punto y coma de la última línea para que presente un aspecto similar al siguiente:  
  
     `return 0`  
  
2.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
3.  Un mensaje en el **lista de errores** ventana indica que se produjo un error en la compilación del proyecto. La descripción se parecerá a la siguiente:  
  
     `error C2143: syntax error : missing ';' before '}'`  
  
     Para ver información de ayuda sobre este error, resáltelo en la **lista de errores** ventana y, a continuación, elija la tecla F1.  
  
4.  Vuelva a agregar el punto y coma al final de la línea que tiene el error de sintaxis:  
  
     `return 0;`  
  
5.  En la barra de menús, elija **Compilar**, **Compilar solución**.  
  
     Un mensaje en el **salida** ventana indica que el proyecto se compila correctamente.  
  
    ```Output  
    1>------ Build started: Project: Game, Configuration: Debug Win32 ------  
    1>  TestGames.cpp  
    1>  Game.vcxproj -> C:\Users\<username>\Documents\Visual Studio <version>\Projects\Game\Debug\Game.exe  
    ========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========  
    ```  
  
## <a name="next-steps"></a>Pasos siguientes  
 **Anterior:** [Tutorial: trabajar con proyectos y soluciones (C++)](../ide/walkthrough-working-with-projects-and-solutions-cpp.md) &#124; **Siguiente:**[Tutorial: probar un proyecto (C++)](../ide/walkthrough-testing-a-project-cpp.md)  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Compilación de programas de C/C++](../build/building-c-cpp-programs.md)