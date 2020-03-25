---
title: Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 2cf2844fd4247c3c69648823302a6ad56ff5fd45
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171781"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Utilizar el IDE de Visual Studio para desarrollo de escritorio de C++

El entorno de desarrollo integrado (IDE) de Visual Studio ofrece un conjunto de características que ayudan a administrar proyectos de código grandes y pequeños, escribir y refactorizar el código, y detectar y corregir errores mediante el uso de análisis estático y herramientas de depuración eficaces. Este conjunto de artículos está diseñado para guiarle a través de los pasos necesarios para administrar los proyectos, escribir, probar y depurar el código, y después implementarlo en otro equipo.

## <a name="prerequisites"></a>Prerequisites

Si todavía no ha instalado Visual Studio, ahora es el momento. Para obtener vínculos de descarga y un tutorial rápido, vea [Instalación de la compatibilidad con C++ en Visual Studio](../build/vscpp-step-0-installation.md). Para obtener más información sobre cómo instalar Visual Studio en general, así como sugerencias para solucionar problemas si algo va mal, vea [Instalar Visual Studio](/visualstudio/install/install-visual-studio). Asegúrese de elegir la carga de trabajo **Desarrollo para el escritorio con C++** para incluir los compiladores, herramientas y bibliotecas de C++ cuando se instala Visual Studio, ya que no se instalan de forma predeterminada.

En estos tutoriales se supone que ha instalado Visual Studio y los componentes de C++ necesarios para el desarrollo de escritorio de Windows. También se asume que entiende los fundamentos del lenguaje C++. Si necesita obtener información sobre C++, hay muchos libros y recursos web disponibles. Un buen lugar para comenzar es la página [Get Started](https://isocpp.org/get-started) (Introducción) del sitio web de la Standard C++ Foundation.

Si todavía no ha instalado Visual Studio, ahora es el momento. En general, recomendamos encarecidamente que use Visual Studio 2019, incluso para compilar el código mediante el compilador de Visual Studio 2017 o Visual Studio 2015. Para obtener más información, vea [Use native multi-targeting in Visual Studio to build old projects](../porting/use-native-multi-targeting.md) (Usar compatibilidad nativa con múltiples versiones en Visual Studio para compilar proyectos antiguos).

**Instalación de Visual Studio 2019**

Para obtener Visual Studio 2019, puede descargarlo de [Descargas de Visual Studio](https://www.visualstudio.com/downloads/). No olvide incluir las herramientas de desarrollo de C++ al instalar Visual Studio, dado que no se instalan de forma predeterminada. Para obtener más información sobre cómo instalar Visual Studio, vea [Instalación de Visual Studio 2017](/visualstudio/install/install-visual-studio).

**Instalación de Visual Studio 2017**

Para obtener Visual Studio 2017, puede descargarlo de [Descargar versiones anteriores de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). No olvide incluir las herramientas de desarrollo de C++ al instalar Visual Studio, dado que no se instalan de forma predeterminada. Para más información sobre cómo instalar Visual Studio, vea [Instalación de Visual Studio](/visualstudio/install/install-visual-studio) y establezca el selector de versión de la página en **Visual Studio 2017**.

**Instalación de Visual Studio 2015**

Para instalar Visual Studio 2015, vaya a [Descargar versiones anteriores de Visual Studio](https://www.visualstudio.com/vs/older-downloads/). Ejecute el programa de instalación y elija **Instalación personalizada** y, a continuación, seleccione el componente de C++.

Una vez completada la instalación de Visual Studio, está listo para continuar.

## <a name="get-started"></a>Introducción

Para comenzar a usar el IDE de Visual Studio para compilar aplicaciones de C++, siga cada uno de estos temas en orden. Cada uno se basa en el trabajo completado en los temas anteriores:

- [Tutorial: Trabajar con proyectos y soluciones (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [Tutorial: Compilar un proyecto (C++)](walkthrough-building-a-project-cpp.md)

- [Tutorial: Probar un proyecto (C++)](walkthrough-testing-a-project-cpp.md)

- [Tutorial: Depurar un proyecto (C++)](walkthrough-debugging-a-project-cpp.md)

- [Tutorial: Implementar el programa (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Pasos siguientes

Una vez que haya completado estos tutoriales, estará listo para comenzar a compilar sus propios proyectos. Para más información y recursos para el desarrollo de C++, vea [Visual C++ en Visual Studio](../overview/visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Consulte también

[Introducción al desarrollo con Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)
