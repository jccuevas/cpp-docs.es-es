---
title: "Solucionar problemas de personalizaciones de compilaci&#243;n | Microsoft Docs"
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
  - "eventos de compilación [C++], solucionar problemas"
  - "pasos de compilación [C++], solucionar problemas"
  - "compilaciones [C++], eventos de compilación"
  - "compilaciones [C++], solucionar problemas"
  - "pasos de compilación personalizada [C++], solucionar problemas"
  - "eventos [C++], build"
  - "solucionar problemas [C++], compilaciones"
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Solucionar problemas de personalizaciones de compilaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando los pasos o eventos de compilación personalizada no muestren el comportamiento esperado, existen varias formas de intentar comprender la causa del error.  
  
-   Asegúrese de que los archivos compilados por los pasos de compilación personalizada coinciden con los archivos declarados como resultados.  
  
-   Si los pasos de compilación personalizada van a generar archivos que sean entradas o dependencias de otros pasos de compilación \(personalizada o no\), compruebe que tales archivos estén agregados al proyecto.  Y asegúrese de que las herramientas que usan esos archivos se ejecutan después del paso de compilación personalizado.  
  
-   Para ver cómo actúa realmente el paso de compilación personalizado, agregue `@echo on` como el primer comando.  Los eventos de compilación y pasos de compilación se colocan en un archivo temporal .bat y se ejecutan cuando se compila el proyecto.  Por consiguiente, es posible agregar la capacidad de comprobación de errores a los comandos de eventos de compilación o de pasos de generación.  
  
-   Examine el registro de compilación en el directorio de archivos intermedios, para comprobar qué se ha ejecutado en realidad.  La expresión de macro **MSBuild**, **$\(IntDir\)\\$\(MSBuildProjectName\).log**, representa la ruta de acceso y nombre del registro de compilación.  
  
-   Modifique sus valores de proyecto para recopilar más información que la predeterminada en el registro de compilación.  En el menú **Herramientas**, haga clic en **Opciones**.  En el cuadro de diálogo **Opciones**, haga clic en el nodo **Proyectos y soluciones** y, después, haga clic en el nodo **Compilar y ejecutar**.  A continuación, en el cuadro **Contenido del archivo de registro de compilación del proyecto de MSBuild**, haga clic en **Detallado**.  
  
-   Compruebe el valor de cualquier macro de directorio o nombre de archivo que use.  Puede repetir las macros una a una o bien agregar `copy %0 command.bat` al principio del paso de compilación personalizado, con lo que los comandos del paso se copiarán en command.bat con todas las macros expandidas.  
  
-   Ejecute uno a uno los pasos de generación personalizada y los eventos de compilación para comprobar su comportamiento.  
  
## Vea también  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)