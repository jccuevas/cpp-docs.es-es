---
title: 'Cómo: habilitar un conjunto de herramientas de MSVC de 64 bits en la línea de comandos'
ms.date: 07/24/2019
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
ms.openlocfilehash: 60399994cd5fc2f39efeadc6ffcf917138aada37
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078539"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Cómo: habilitar 64 un conjunto de herramientas de MSVC hospedado x64 en la línea de comandos

Visual Studio incluye compiladores, enlazadores y otras herramientas de C++ que puede usar para crear versiones específicas de la plataforma de las aplicaciones que se pueden ejecutar en sistemas operativos Windows de 32 bits, 64 bits o basados en ARM. Hay otras cargas de trabajo opcionales de Visual Studio que permiten usar herramientas de C++ para incluir como destino otras plataformas, como iOS, Android y Linux. La arquitectura de compilación predeterminada usa herramientas hospedadas en x86 de 32 bits para compilar código de Windows nativo x86 de 32 bits. Pero probablemente tenga un equipo de 64 bits. Cuando Visual Studio está instalado en un sistema operativo Windows de 64 bits, hay disponibles más accesos directos del símbolo del sistema para desarrolladores para los compiladores nativos y cruzados hospedados en x64 de 64 bits. Si es así, puede aprovechar el procesador y el espacio de memoria disponible para el código de 64 bits mediante el conjunto de herramientas hospedadas en x64 de 64 bits al compilar código para procesadores x86, x64 o ARM.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Usar un acceso directo del símbolo del sistema para desarrolladores hospedado de 64 bits

Para acceder a estos símbolos del sistema en Windows 10, en el menú **Inicio** abra la carpeta de su versión de Visual Studio, como por ejemplo **Visual Studio 2019** y, después, elija uno de los símbolos del sistema para desarrolladores de herramientas cruzadas o nativas x64.

![símbolo del sistema de las herramientas nativas x64](media/x64-native-tools-command-prompt.png "Herramientas nativas x64 en el menú Inicio")

Para acceder a estos símbolos del sistema en Windows 8, en la pantalla **Inicio**, abra **Todas las aplicaciones**. Bajo el encabezado de la versión instalada de Visual Studio, abra la carpeta **Visual Studio** (en versiones anteriores de Visual Studio, es posible que se llame **Visual Studio Tools**). En versiones anteriores de Windows, abra **Inicio**, expanda **Todos los programas** y elija la carpeta de su versión de **Visual Studio** (y en versiones anteriores de Visual Studio,  **Visual Studio Tools**). Para obtener más información, vea [Developer command prompt shortcuts](building-on-the-command-line.md#developer_command_prompt_shortcuts) (Accesos directos al símbolo del sistema para desarrolladores).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Usar Vcvarsall.bat para establecer una arquitectura de compilación hospedada de 64 bits

Se puede usar cualquiera de las configuraciones de compilación de las herramientas del compilador cruzado o nativo en la línea de comandos, mediante la ejecución del archivo de comandos vcvarsall.bat. Este archivo de comandos configura la ruta de acceso y las variables de entorno que habilitan una determinada arquitectura de compilación en una ventana del símbolo del sistema existente. Para obtener instrucciones específicas, vea [Ubicaciones de archivos de comandos para desarrolladores](building-on-the-command-line.md#developer_command_file_locations).

## <a name="remarks"></a>Observaciones

> [!NOTE]
> Para saber más sobre las herramientas específicas que se incluyen con cada edición de Visual Studio, vea [Visual C++ Tools and Features in Visual Studio Editions](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md) (Características y herramientas de Visual C+++ en ediciones de Visual Studio).
>
> Para obtener información sobre cómo usar el IDE de Visual Studio para crear aplicaciones de 64 bits, consulte [Cómo: configurar proyectos C++ visuales para plataformas de destino de 64 bits y x64](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Cuando se instala una carga de trabajo de C++ en el instalador de Visual Studio, siempre se instalan las herramientas del compilador nativo y cruzado, hospedado en x86, de 32 bits para compilar código x86 y x64. Si incluye la carga de trabajo de la Plataforma universal de Windows, también instala las herramientas del compilador cruzado hospedado en x86 para compilar código ARM. Si instala estas cargas de trabajo en un procesador x64 de 64 bits, también obtiene herramientas del compilador cruzado o nativo de 64 bits para compilar código de x86, x64 y ARM. Las herramientas de 32 bits y 64 bits generan código idéntico, pero las herramientas de 64 bits admiten más memoria para los símbolos de encabezado precompilados y las opciones de Optimización de todo el programa ([/GL](reference/gl-whole-program-optimization.md) y [/LTCG](reference/ltcg-link-time-code-generation.md)). Si llega al límite de memoria cuando usa las herramientas de 32 bits, pruebe con las herramientas de 64 bits.

## <a name="see-also"></a>Consulte también

[Configuración de proyectos de Visual C++ para destinos x64 de 64 bits](configuring-programs-for-64-bit-visual-cpp.md)<br/>
