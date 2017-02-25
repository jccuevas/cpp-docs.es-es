---
title: "R6016 de Error de tiempo de ejecuci&#243;n de C | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6016"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6016"
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Error en tiempo de ejecuci&#243;n de C R6016
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

espacio insuficiente para datos de subproceso  
  
> [!NOTE]
>  Si aparece este mensaje de error, el programa especificado se cerró porque tiene un problema de memoria interna.  Hay muchas razones posibles para que se produzca este error, pero normalmente se deriva de un defecto del programa o de daños en las bibliotecas de Visual C\+\+ que se usan.  
>   
>  Puede intentar seguir estos pasos para corregir este error:  
>   
>  -   Use la página **Programas y características** del **Panel de control** para reparar o reinstalar el programa.  
> -   Use la página **Programas y características** del **Panel de control** para reparar o reinstalar todas las copias de Microsoft Visual C\+\+ Redistributable.  
> -   Active **Windows Update** en el **Panel de control** para obtener actualizaciones de software.  
> -   Busque una versión actualizada del programa.  
  
 Este error se produce porque el programa no recibió memoria suficiente del sistema operativo para completar una llamada [\_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) o `_beginthreadex` o porque `_beginthread` o `_beginthreadex` no han inicializado el almacenamiento local de subprocesos.  
  
 Cuando se inicia un subproceso nuevo, la biblioteca debe crear una base de datos interna para el subproceso.  Si la base de datos no se puede ampliar utilizando la memoria proporcionada por el sistema operativo, el subproceso no se puede iniciar y se detiene el proceso de llamada.  Esto puede ocurrir cuando el proceso ha creado demasiados subprocesos o si se ha agotado el almacenamiento local de subprocesos.  
  
 Recomendamos que los archivos ejecutables que llamen a la biblioteca en tiempo de ejecución de C \(CRT\) utilicen `_beginthreadex` para la creación de subprocesos en lugar de la API de Windows `CreateThread`.  `_beginthreadex` inicializa el almacenamiento estático interno que usan muchas funciones CRT en el almacenamiento local de subprocesos.  Si utiliza `CreateThread` para crear un subproceso, CRT puede finalizar el proceso con R6016 cuando se realiza una llamada a una función CRT que requiere que el almacenamiento estático interno se haya inicializado.