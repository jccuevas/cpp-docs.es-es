---
title: Establecer la ruta de acceso y las variables de entorno para compilaciones de línea de comandos
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
ms.openlocfilehash: 6e7882b169805e3c62596341986a83d476ac5ec1
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492154"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Establecer la ruta de acceso y las variables de entorno para compilaciones de línea de comandos

Las herramientas C++ de compilación de línea de comandos de Microsoft (MSVC) requieren varias variables de entorno personalizadas para la instalación y la configuración de compilación. Cuando el C++ instalador de Visual Studio instala una carga de trabajo, crea archivos de comandos personalizados o archivos por lotes que establecen las variables de entorno necesarias. A continuación, el instalador usa estos archivos de comandos para crear accesos directos para que el menú Inicio de Windows abra una ventana del símbolo del sistema para desarrolladores. Estos métodos abreviados configuran las variables de entorno para una configuración de compilación específica. Si desea utilizar las herramientas de línea de comandos, puede ejecutar uno de estos métodos abreviados, o puede abrir una ventana del símbolo del sistema sin formato y, a continuación, ejecutar uno de los archivos de comandos personalizados para establecer el entorno de configuración de compilación. Para obtener más información, consulte [uso del conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md). Para usar los archivos de comandos con un símbolo del sistema sin formato, vea la sección titulada [ubicaciones de archivos de comandos de desarrollador](building-on-the-command-line.md#developer_command_file_locations).

Las herramientas de línea de comandos de MSVC usan las variables de entorno PATH, TMP, INCLUDE, LIB y LIBPATH, y también usan otras variables de entorno específicas de las herramientas, plataformas y SDK instalados. Incluso una instalación sencilla de Visual Studio puede establecer veinte o más variables de entorno. Dado que los valores de estas variables de entorno son específicos de la instalación y de la opción de configuración de compilación, y se pueden cambiar mediante actualizaciones o actualizaciones de productos, se recomienda encarecidamente usar un acceso directo del símbolo del sistema para desarrolladores o uno de los archivos de comandos personalizados para establecerlos, en lugar de establecerlos en el entorno de Windows.

Para ver qué variables de entorno se establecen mediante un acceso directo del símbolo del sistema para desarrolladores, puede usar el comando SET. Abra una ventana del símbolo del sistema sin formato y Capture la salida del comando SET para una línea base. Abra una ventana del símbolo del sistema para desarrolladores y Capture la salida del comando SET para la comparación. Una herramienta de comparación, como la integrada en el IDE de Visual Studio, puede ser útil para comparar las variables de entorno y ver lo que establece el símbolo del sistema para desarrolladores. Para obtener información sobre las variables de entorno específicas utilizadas por el compilador y el vinculador, vea [variables de entorno de cl](reference/cl-environment-variables.md).

> [!NOTE]
>  Varias herramientas de línea de comandos o opciones de herramienta pueden requerir permiso de administrador. Si tiene problemas de permisos al usarlos, se recomienda que abra la ventana del símbolo del sistema para desarrolladores mediante la opción **Ejecutar como administrador** . En Windows 10, haga clic con el botón derecho para abrir el menú contextual de la ventana del símbolo del sistema y, a continuación, elija **más**, **Ejecutar como administrador**.

## <a name="see-also"></a>Vea también

[Uso del conjunto de herramientas MSVC desde la línea de comandos](building-on-the-command-line.md)<br/>
[Referencia del enlazador MSVC](reference/linking.md)<br/>
[Opciones del enlazador MSVC](reference/linker-options.md)<br/>
[Referencia del compilador MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
