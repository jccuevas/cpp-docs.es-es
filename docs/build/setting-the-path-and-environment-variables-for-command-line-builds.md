---
title: Establecer las variables de ruta y entorno para las compilaciones de línea de comandos
ms.custom: conceptual
ms.date: 07/24/2019
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
ms.openlocfilehash: aeafe806e5d29b89c243586974814aa7cfc16d1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335584"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Establecer las variables de ruta y entorno para las compilaciones de línea de comandos

Las herramientas de compilación de línea de comandos de Microsoft C++ (MSVC) requieren diversas variables de entorno que estén personalizadas para su instalación y configuración de compilación. Cuando el instalador de Visual Studio instala una carga de trabajo de C++, crea archivos de comandos personalizados, o archivos por lotes, que establecen las variables de entorno necesarias. Después, el instalador usa estos archivos de comandos para crear accesos directos para que el menú Inicio de Windows abra una ventana del símbolo del sistema para desarrolladores. Estos accesos directos configuran las variables de entorno para una configuración de compilación específica. Cuando quiera usar las herramientas de línea de comandos, puede ejecutar uno de estos accesos directos o abrir una ventana del símbolo del sistema convencional y, después, ejecutar uno de los archivos de comandos personalizados para establecer usted mismo el entorno de configuración de compilación. Para obtener más información, vea [Usar el conjunto de herramientas de MSVC desde la línea de comandos](building-on-the-command-line.md). Para usar los archivos de comandos con un símbolo del sistema convencional, vea la sección titulada [Ubicaciones de archivos de comandos para desarrolladores](building-on-the-command-line.md#developer_command_file_locations).

Las herramientas de línea de comandos de MSVC emplean las variables de entorno PATH, TMP, INCLUDE, LIB y LIBPATH, así como otras variables de entorno específicas de las herramientas, plataformas y SDK instalados. Incluso una sencilla instalación de Visual Studio puede establecer veinte o más variables de entorno. Dado que los valores de estas variables de entorno son específicos de la instalación y de la opción de configuración de compilación, y dado que se pueden cambiar mediante actualizaciones de productos, le recomendamos encarecidamente que use un acceso directo del símbolo del sistema para desarrolladores o uno de los archivos de comandos personalizados para establecerlos, en lugar de hacerlo por su cuenta en el entorno de Windows.

Para ver qué variables de entorno se establecen mediante un acceso directo del símbolo del sistema para desarrolladores, puede usar el comando SET. Abra una ventana del símbolo del sistema convencional y capture la salida del comando SET para una línea base. Abra una ventana del símbolo del sistema para desarrolladores y capture la salida del comando SET para comparar. Puede ser útil usar una herramienta de comparación, como la integrada en el IDE de Visual Studio, para comparar las variables de entorno y ver lo que establece el símbolo del sistema para desarrolladores. Para obtener información sobre las variables de entorno específicas que usan el compilador y el enlazador, consulte [Variables de entorno de CL](reference/cl-environment-variables.md).

> [!NOTE]
> Hay varias herramientas de línea de comandos u opciones de herramientas que podrían requerir el permiso de administrador. Si tiene problemas de permisos al usarlas, le recomendamos que abra la ventana del símbolo del sistema para desarrolladores mediante la opción **Ejecutar como administrador**. En Windows 10, haga clic con el botón derecho para abrir el menú contextual de la ventana del símbolo del sistema y elija **Más**, **Ejecutar como administrador**.

## <a name="see-also"></a>Vea también

[Uso del conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md)<br/>
[Referencia del enlazador MSVC](reference/linking.md)<br/>
[Opciones del enlazador MSVC](reference/linker-options.md)<br/>
[Referencia del compilador MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
