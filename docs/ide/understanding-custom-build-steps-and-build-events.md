---
title: Descripción de los pasos de compilación personalizada y los eventos de compilación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6522eb88eb282a1a3803e180e53027591f79374a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443896"
---
# <a name="understanding-custom-build-steps-and-build-events"></a>Descripción de los pasos de compilación personalizada y los eventos de compilación

Desde dentro del entorno de desarrollo de Visual C++, hay tres maneras básicas de personalizar el proceso de compilación:

- **Pasos de compilación personalizada**

   Un paso de compilación personalizada es una regla de compilación asociada a un proyecto. Un paso de compilación personalizada puede especificar una línea de comandos para su ejecución, cualquier archivo de entrada o salida adicional, y un mensaje para mostrar. Para obtener más información, vea [Procedimiento para agregar un paso de compilación personalizada a proyectos de MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md).

- **Herramientas de compilación personalizadas**

   Una herramienta de compilación personalizada es una regla de compilación asociada a uno o varios archivos. Un paso de compilación personalizada puede pasar archivos de entrada a una herramienta de compilación personalizada, lo que da lugar a uno o más archivos de salida. Por ejemplo, los archivos de ayuda de una aplicación MFC se crean con una herramienta de compilación personalizada. Para obtener más información, vea [Procedimiento para agregar herramientas de compilación personalizadas a proyectos de MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md) y [Especificar las herramientas de compilación personalizadas](../ide/specifying-custom-build-tools.md).

- **Eventos de compilación**

   Los eventos de compilación permiten personalizar la compilación del proyecto. Hay tres eventos de compilación: *anterior a la compilación*, *anterior a la vinculación* y *posterior a la compilación*. Un evento de compilación permite especificar una acción para que se produzca en un momento concreto en el proceso de compilación. Por ejemplo, se podría usar un evento de compilación para registrar un archivo con **regsvr32.exe** una vez finalizada la compilación del proyecto. Para obtener más información, vea [Especificar eventos de compilación](../ide/specifying-build-events.md).

[Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md) puede ayudar a asegurarse de que los pasos de compilación personalizada y los eventos de compilación se ejecutan según lo esperado.

El formato de salida de un paso de compilación personalizada o de un evento de compilación también puede mejorar la facilidad de uso de la herramienta. Para obtener más información, consulte [Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación](../ide/formatting-the-output-of-a-custom-build-step-or-build-event.md).

Los eventos de compilación y los pasos de compilación personalizada se ejecutan en el orden siguiente junto con otros pasos de compilación:

1. Evento anterior a la compilación

2. Herramientas de compilación personalizadas en archivos individuales

3. MIDL

4. Compilador de recursos

5. El compilador de C/C++

6. Evento anterior a la vinculación

7. Vinculador o bibliotecario (según corresponda)

8. Herramienta Manifiesto

9. BSCMake

10. Paso de compilación personalizada en el proyecto

11. Evento posterior a la compilación

`custom build step on the project` y un `post-build event` se ejecutan secuencialmente después de que finalicen todos los demás procesos de compilación.

## <a name="see-also"></a>Vea también

[Compilar proyectos de C++ en Visual Studio](../ide/building-cpp-projects-in-visual-studio.md)<br>
[Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)
