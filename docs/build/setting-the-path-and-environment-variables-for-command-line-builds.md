---
title: Establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos
ms.custom: conceptual
ms.date: 11/04/2016
f1_keywords:
- include
- Lib
- Path
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: dee8f4ee08f9922c4bfc79c5103618681058e56e
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415375"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Establecer la ruta de acceso y las Variables de entorno para compilaciones de línea de comandos

Las herramientas de línea de comandos de compilación de Visual C++, requieren varias variables de entorno personalizadas para la configuración de instalación y compilación. Cuando se instala una carga de trabajo de C++ mediante el instalador de Visual Studio, crea archivos de comandos personalizada o archivos por lotes, que establece las variables de entorno necesarias. El instalador utiliza, a continuación, estos archivos de comandos para crear accesos directos del menú Inicio de Windows abrir una ventana de símbolo del sistema para desarrolladores. Estos métodos abreviados de establecer las variables de entorno para una determinada configuración de compilación. Cuando desea utilizar las herramientas de línea de comandos, puede ejecutar uno de estos métodos abreviados, o puede abrir una ventana del símbolo del sistema sin formato y, a continuación, ejecute uno de los archivos de comandos personalizada para establecer el entorno de configuración de compilación por sí mismo. Para obtener más información, consulte [compilar el código de C o C++ en la línea de comandos](building-on-the-command-line.md).

Las herramientas de línea de comandos de Visual C++ usan las variables de entorno PATH, TMP, INCLUDE, LIB y LIBPATH y también utilizar otras variables de entorno específicas de sus herramientas instaladas, plataformas y SDK. Incluso una simple instalación de Visual Studio puede establecer veinte o más variables de entorno. Dado que los valores de estas variables de entorno son específicos de la instalación y elija la configuración de compilación y pueden cambiarse mediante las actualizaciones del producto, se recomienda que use un acceso directo del símbolo desarrollador o uno de los personalizar archivos de comandos para establecerlos, en lugar de establecerlos en el entorno de Windows por su cuenta.

Para ver qué variables de entorno se establecen mediante un acceso directo del símbolo para desarrolladores, puede usar el comando. Abra una ventana del símbolo del sistema sin formato y capturar la salida del comando SET para una línea base. Abra una ventana de símbolo del sistema para desarrolladores y capturar la salida del comando SET para la comparación. Una herramienta de comparación como el integrado en el IDE de Visual Studio puede ser útil para comparar las variables de entorno y ver lo que se establece mediante el símbolo del sistema para desarrolladores. Para obtener información acerca de las variables de entorno específico utilizado por el compilador y vinculador, vea [Variables de entorno de CL](../build/reference/cl-environment-variables.md) y [Variables de entorno de LINK](../build/reference/link-environment-variables.md).

> [!NOTE]
>  Varias herramientas de línea de comandos u opciones de herramientas pueden requerir un permiso de administrador. Si tiene problemas de permisos cuando se usan, se recomienda que abra la ventana de símbolo del sistema para desarrolladores mediante el uso de la **ejecutar como administrador** opción. En Windows 10, haga doble clic para abrir el menú contextual de la ventana de símbolo del sistema y luego elija **más**, **ejecutar como administrador**.

## <a name="see-also"></a>Vea también

[Compilación de código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md)<br/>
[Vinculación](../build/reference/linking.md)<br/>
[Opciones del vinculador](../build/reference/linker-options.md)<br/>
[Compilación de un programa de C/C++](../build/reference/compiling-a-c-cpp-program.md)<br/>
[Opciones del compilador](../build/reference/compiler-options.md)
