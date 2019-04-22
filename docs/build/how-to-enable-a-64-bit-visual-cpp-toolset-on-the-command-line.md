---
title: Procedimiento Habilitar un conjunto de herramientas MSVC de 64 bits en la línea de comandos
ms.date: 03/29/2018
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
ms.openlocfilehash: 8436254a3d8c5c1dae018c2309ceaad7bd5b2408
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58769282"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Procedimiento Habilitar 64 bits, x64 hospeda el conjunto de herramientas MSVC en la línea de comandos

Visual Studio incluye los compiladores de C++, los enlazadores y otras herramientas que puede usar para crear versiones específicas de la plataforma de las aplicaciones que se pueden ejecutar en los sistemas operativos de Windows de 32 bits, 64 bits o basados en ARM. Otras cargas de trabajo opcionales de Visual Studio le permiten usar herramientas de C++ como destino otras plataformas como iOS, Android y Linux. La arquitectura de compilación predeterminada usa herramientas de 32 bits, hospedados en x86 para compilar código de Windows de 32 bits, nativo x86. Sin embargo, probablemente tiene un equipo de 64 bits. Se puede aprovechar el procesador y el espacio de memoria disponible para el código de 64 bits utilizando el conjunto de herramientas de 64 bits, hospedadas en x64 64 al compilar código para x86, x64 o procesadores ARM.

> [!NOTE]
> Para obtener información acerca de las herramientas específicas que se incluyen con cada edición de Visual Studio, consulte [herramientas de Visual C++ y las características de Visual Studio Editions](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Para obtener información acerca de cómo usar el IDE de Visual Studio para crear aplicaciones de 64 bits, vea [Cómo: sobre cómo configurar proyectos de Visual C++ en plataformas de destino de 64 bits, x64](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Cuando se instala una carga de trabajo de C++ en el instalador de Visual Studio, siempre se instala 32 bits, hospedados en x86, nativa y cruzada las herramientas del compilador para compilar código x86 y x64. Si incluye la carga de trabajo de la plataforma Universal de Windows, también instala las herramientas de compilador cruzado x86 hospedadas para compilar código ARM. Si instala estas cargas de trabajo en un x64 64 bits, procesador, también obtiene nativo de 64 bits y herramientas del compilador para generar x86, x 64 y ARM de código. Las herramientas de 32 bits y 64 bits generan código idéntico, pero las herramientas de 64 bits admiten más memoria para los símbolos de encabezado precompilado y Whole Program Optimization ([/GL](reference/gl-whole-program-optimization.md) y [/LTCG](reference/ltcg-link-time-code-generation.md)) opciones. Si experimenta los límites de memoria al usar las herramientas de 32 bits, pruebe las herramientas de 64 bits.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Usar un acceso directo del símbolo para desarrolladores hospedado de 64 bits

Cuando se instala Visual Studio en un sistema operativo de Windows de 64 bits, están disponibles métodos abreviados del símbolo de desarrollador adicionales para el nativo de 64 bits, hospedadas en x64 64 y compiladores cruzados. Para obtener acceso a estos símbolos del sistema en Windows 10, en el **iniciar** menú, abra la carpeta para su versión de Visual Studio, por ejemplo **Visual Studio 2017**y, a continuación, elija uno de los x64 nativo o entre herramientas símbolos del sistema para desarrolladores. Para obtener acceso a estos símbolos del sistema en Windows 8, en el **iniciar** pantalla, abra **todas las aplicaciones**. En el encabezado de la versión instalada de Visual Studio, abra el **Visual Studio** carpeta (en versiones anteriores de Visual Studio, puede llamarse **Visual Studio Tools**). En versiones anteriores de Windows, elija **iniciar**, expanda **todos los programas**, la carpeta para su versión de **Visual Studio** (y en versiones anteriores de Visual Studio,  **Herramientas de Visual Studio**). Para obtener más información, vea [Developer command prompt shortcuts](building-on-the-command-line.md#developer_command_prompt_shortcuts) (Accesos directos al símbolo del sistema para desarrolladores).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Utilizar Vcvarsall.bat para establecer una arquitectura de 64 bits de compilación hospedado

Cualquiera de nativo o herramientas del compilador se pueden usar las configuraciones de compilación en la línea de comandos ejecutando el vcvarsall.bat archivo de comandos. Este archivo de comandos configura la ruta de acceso y las variables de entorno que permiten una determinada arquitectura en una ventana de símbolo del sistema existente de compilación. Para obtener instrucciones específicas, consulte [ubicaciones de archivos de comandos de desarrollador](building-on-the-command-line.md#developer_command_file_locations).

## <a name="see-also"></a>Vea también

[Configurar los proyectos de C++ de 64 bits, x64 destinos](configuring-programs-for-64-bit-visual-cpp.md)<br/>
