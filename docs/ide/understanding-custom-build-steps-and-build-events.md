---
title: "Descripción de los pasos de compilación personalizada y los eventos de compilación | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- builds [C++], events
- custom build steps [C++], customizing builds
- events [C++], build
- custom build steps [C++]
- build steps [C++]
- build events [C++], order of events and build steps
- build steps [C++], build events
- builds [C++], custom build steps
ms.assetid: beb2f017-3e9f-4b2c-9b57-2572fd2628e4
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9b724190fc409d14a0bffdbc63b369b9643f321c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Descripción de los pasos de compilación personalizada y los eventos de compilación
Desde dentro del entorno de desarrollo de Visual C++, hay tres maneras básicas para personalizar el proceso de compilación:  
  
 **Pasos de compilación personalizada**  
 Un paso de compilación personalizada es una regla de compilación asociada a un proyecto. Un paso de compilación personalizado puede especificar una línea de comandos para su ejecución, cualquier entrada adicional o archivos de salida y un mensaje para mostrar. Para obtener más información, consulte [Cómo: agregar un paso de compilación personalizado a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).  
  
 **Herramientas de compilación personalizadas**  
 Una herramienta de compilación personalizada es una regla de compilación asociada a uno o varios archivos. Un paso de compilación personalizado puede pasar archivos de entrada a una herramienta de compilación personalizada, que da lugar a uno o más archivos de salida. Por ejemplo, se crean los archivos de ayuda en una aplicación MFC con una herramienta de compilación personalizada. Para obtener más información, consulte [Cómo: agregar Custom Build Tools para proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) y [Specifying Custom Build Tools](../ide/specifying-custom-build-tools.md).  
  
 **Eventos de compilación**  
 Los eventos de compilación permiten personalizar la generación del proyecto. Hay tres eventos de compilación: *anterior a la compilación*, *anterior a la vinculación*, y *posterior a la compilación*. Un evento de compilación, puede especificar una acción para que se produzca en un momento concreto en el proceso de compilación. Por ejemplo, podría usar un evento de compilación para registrar un archivo con **regsvr32.exe** finalizada compilar el proyecto. Para obtener más información, consulte [especificar eventos de compilación](../ide/specifying-build-events.md).  
  
 [Solución de problemas de las personalizaciones de compilación](../ide/troubleshooting-build-customizations.md) puede ayudar a asegurarse de que los pasos de compilación personalizada y generar eventos que se ejecutan según lo esperado.  
  
 El formato de salida personalizado paso de compilación o eventos de compilación también pueden mejorar la facilidad de uso de la herramienta. Para obtener más información, consulte [Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).  
  
 Los eventos de compilación y generación personalizada pasos que se ejecutan en el orden siguiente junto con otros pasos de compilación:  
  
1.  Evento de generación previa  
  
2.  Herramientas en archivos individuales de compilación personalizadas  
  
3.  MIDL  
  
4.  Compilador de recursos  
  
5.  El compilador de C o C++  
  
6.  Evento anterior a la vinculación  
  
7.  Vinculador o bibliotecario (según corresponda)  
  
8.  Herramienta Manifiesto  
  
9. BSCMake  
  
10. Paso de compilación personalizada en el proyecto  
  
11. Evento posterior a la compilación  
  
 El `custom build step on the project` y un `post-build event` ejecución secuencialmente después de que todos los demás compilación procesa Finalizar.  
  
## <a name="see-also"></a>Vea también  
 [Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)   
 [Común Macros para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)   
 [Cuadro de diálogo de orden de compilación de herramienta](http://msdn.microsoft.com/en-us/6204c5b1-7ce9-4948-9ff6-0268642ee14c)