---
title: "Descripci&#243;n de los pasos de compilaci&#243;n personalizada y los eventos de compilaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "eventos de compilación [C++], orden de eventos y pasos de compilación"
  - "pasos de compilación [C++]"
  - "pasos de compilación [C++], eventos de compilación"
  - "compilaciones [C++], pasos de compilación personalizada"
  - "compilaciones [C++], eventos"
  - "pasos de compilación personalizada [C++]"
  - "pasos de compilación personalizada [C++], personalizar compilaciones"
  - "eventos [C++], build"
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Descripci&#243;n de los pasos de compilaci&#243;n personalizada y los eventos de compilaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el entorno de desarrollo de Visual C\+\+, existen tres métodos básicos para personalizar el proceso de compilación:  
  
 **Pasos de compilación personalizada**  
 Un paso de compilación personalizado es una regla de compilación asociada con un proyecto.  Un paso de compilación personalizado puede especificar una línea de comandos que se debe ejecutar, cualquier archivo de entrada o salida adicional, y el mensaje que se debe mostrar.  Para obtener más información, vea [Cómo: Agregar un paso de compilación personalizado a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).  
  
 **Herramientas de compilación personalizadas**  
 Una herramienta de compilación personalizada es una regla de compilación asociada a uno o varios archivos.  Un paso de compilación personalizado puede pasar archivos de entrada a una herramienta de compilación personalizada, con lo que se producen uno o varios archivos de salida.  Por ejemplo, los archivos de ayuda de una aplicación MFC se generan con una herramienta de compilación personalizada.  Para obtener más información, vea [Cómo: Agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) y [Especificar las herramientas de compilación personalizadas](../ide/specifying-custom-build-tools.md).  
  
 **Eventos de compilación**  
 Los eventos de compilación permiten personalizar la generación de un proyecto.  Existen tres eventos de compilación: *anterior a la compilación*, *anterior a la vinculación* y *posterior a la compilación*.  Un evento de compilación permite especificar que ocurra una acción en un momento concreto del proceso de compilación.  Por ejemplo, se puede usar un evento de compilación para registrar un archivo con **regsvr32.exe** al finalizar la generación del proyecto.  Para obtener más información, vea [Especificar eventos de compilación](../ide/specifying-build-events.md).  
  
 [Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md) puede ayudarle a comprobar que sus pasos de compilación personalizados y sus eventos de compilación se ejecutan de la forma esperada.  
  
 El formato de presentación de un paso de compilación personalizada o un evento de compilación también puede mejorar las posibilidades de uso de la herramienta.  Para obtener más información, vea [Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).  
  
 Los eventos de compilación y los pasos de generación personalizada se ejecutan en el orden siguiente, junto con otros pasos de generación:  
  
1.  Evento de compilación previa  
  
2.  Herramientas de compilación personalizadas en archivos individuales  
  
3.  MIDL  
  
4.  Compilador de recursos  
  
5.  Compilador de C\/C\+\+  
  
6.  Evento de vinculación previa  
  
7.  Vinculador o bibliotecario \(según proceda\)  
  
8.  Herramienta Manifiesto  
  
9. BSCMake  
  
10. Paso de compilación personalizada en el proyecto  
  
11. Evento de compilación posterior  
  
 `custom build step on the project` y `post-build event` se ejecutan secuencialmente después de finalizar el resto de los procesos de compilación.  
  
## Vea también  
 [Compilar proyectos de C\+\+ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)   
 [Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)   
 [Tool Build Order Dialog Box](http://msdn.microsoft.com/es-es/6204c5b1-7ce9-4948-9ff6-0268642ee14c)