---
title: Establezca las variables de ruta y entorno para las compilaciones de línea de comandos
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
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335584"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Establezca las variables de ruta y entorno para las compilaciones de línea de comandos

Las herramientas de compilación de línea de comandos de Microsoft C++ (MSVC) requieren varias variables de entorno personalizadas para la instalación y la configuración de compilación. Cuando el instalador de Visual Studio instala una carga de trabajo de C++, crea archivos de comandos personalizados o archivos por lotes que establecen las variables de entorno necesarias. A continuación, el instalador utiliza estos archivos de comandos para crear accesos directos para el menú Inicio de Windows para abrir una ventana del símbolo del sistema para desarrolladores. Estos accesos directos configuran las variables de entorno para una configuración de compilación específica. Si desea utilizar las herramientas de línea de comandos, puede ejecutar uno de estos accesos directos, o puede abrir una ventana de símbolo del sistema sin formato y, a continuación, ejecutar uno de los archivos de comandos personalizados para establecer el entorno de configuración de compilación usted mismo. Para obtener más información, consulte Usar el conjunto de [herramientas MSVC desde la línea](building-on-the-command-line.md)de comandos . Para utilizar los archivos de comandos con un símbolo del sistema sin formato, consulte la sección titulada Ubicaciones de archivos de [comandos del](building-on-the-command-line.md#developer_command_file_locations)desarrollador .

Las herramientas de línea de comandos de MSVC utilizan las variables de entorno PATH, TMP, INCLUDE, LIB y LIBPATH, y también utilizan otras variables de entorno específicas de las herramientas, plataformas y sDK instalados. Incluso una instalación simple de Visual Studio puede establecer veinte o más variables de entorno. Dado que los valores de estas variables de entorno son específicos de la instalación y la configuración de compilación que elija, y se pueden cambiar mediante actualizaciones o actualizaciones de productos, se recomienda encarecidamente que utilice un acceso directo del símbolo del sistema para desarrolladores o uno de los archivos de comandos personalizados para establecerlos, en lugar de establecerlos en el entorno de Windows usted mismo.

Para ver qué variables de entorno establece un acceso directo del símbolo del sistema para desarrolladores, puede utilizar el comando SET. Abra una ventana de símbolo del sistema sin formato y capture la salida del comando SET para una línea base. Abra una ventana del símbolo del sistema para desarrolladores y capture la salida del comando SET para la comparación. Una herramienta diff como la integrada en el IDE de Visual Studio puede ser útil para comparar las variables de entorno y ver lo que establece el símbolo del sistema para desarrolladores. Para obtener información sobre las variables de entorno específicas utilizadas por el compilador y el vinculador, vea [Variables](reference/cl-environment-variables.md)de entorno CL .

> [!NOTE]
> Varias herramientas de línea de comandos u opciones de herramientas pueden requerir permiso de administrador. Si tiene problemas de permisos al usarlos, le recomendamos que abra la ventana del símbolo del sistema para desarrolladores mediante la opción **Ejecutar como administrador.** En Windows 10, haga clic con el botón derecho para abrir el menú contextual de la ventana del símbolo del sistema y, a continuación, elija **Más**, **Ejecutar como administrador**.

## <a name="see-also"></a>Consulte también

[Uso del conjunto de herramientas de MSVC desde la línea de comandos](building-on-the-command-line.md)<br/>
[Referencia del enlazador MSVC](reference/linking.md)<br/>
[Opciones de MSVC Linker](reference/linker-options.md)<br/>
[Referencia del compilador MSVC](reference/compiling-a-c-cpp-program.md)<br/>
[Opciones del compilador de MSVC](reference/compiler-options.md)
