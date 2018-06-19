---
title: Establecer la ruta de acceso y las Variables de entorno para las compilaciones de línea de comandos | Documentos de Microsoft
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- include
- Lib
- Path
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b72f13fe25330b81a48d1447b707bdc4626ab3f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381140"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Establecer la ruta de acceso y las Variables de entorno para las compilaciones de línea de comandos

Las herramientas de línea de comandos de compilación de Visual C++ requieren varias variables de entorno que se personalizan para la configuración de instalación y compilación. Cuando se instala una carga de trabajo de C++ de la [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] installer, crea los archivos de comandos personalizada o archivos por lotes, que establece las variables de entorno necesarias. El instalador utiliza, a continuación, estos archivos de comandos para crear accesos directos del menú Inicio de Windows para abrir una ventana de símbolo del sistema para desarrolladores. Estos métodos abreviados de establecer las variables de entorno para una determinada configuración de compilación. Si desea utilizar las herramientas de línea de comandos, puede ejecutar uno de estos métodos abreviados, o puede abrir una ventana del símbolo del sistema sin formato y, a continuación, ejecute uno de los archivos de comandos personalizada para establecer el entorno de configuración de compilación por sí mismo. Para obtener más información, consulte [compilar el código de C o C++ en la línea de comandos](building-on-the-command-line.md).  
  
Las herramientas de línea de comandos de Visual C++ utilizan las variables de entorno PATH, TMP, INCLUDE, LIB y LIBPATH y también utilizar otras variables de entorno específicas de las herramientas instaladas, las plataformas y los SDK. Incluso un sencillo [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] instalación puede establecer variables de entorno de veinte o más. Dado que los valores de estas variables de entorno son específicos de la instalación y la elección de la configuración de compilación y pueden cambiarse mediante las actualizaciones del producto, se recomienda que use un acceso directo del símbolo desarrollador o uno de los personalizar archivos de comandos para establecer, en lugar de establecerlos en el entorno Windows usted mismo. 

Para ver qué variables de entorno se establecen con un acceso directo del símbolo para desarrolladores, puede usar el comando SET. Abra una ventana del símbolo del sistema sin formato y capturar la salida del comando SET para una línea base. Abra una ventana de símbolo del sistema para desarrolladores y capturar la salida del comando SET para la comparación. Una herramienta de comparación como el que está integrado en el IDE de Visual Studio puede ser útil para comparar las variables de entorno y ver lo que se establece mediante el símbolo del sistema para desarrolladores. Para obtener información acerca de las variables de entorno específico utilizado por el compilador y el vinculador, vea [Variables de entorno de CL](../build/reference/cl-environment-variables.md) y [Variables de entorno de vínculo](../build/reference/link-environment-variables.md).  
  
> [!NOTE]
>  Varias herramientas de línea de comandos u opciones de herramientas pueden requerir un permiso de administrador. Si tiene problemas de permisos cuando se usan, le recomendamos que abra la ventana de símbolo del sistema para desarrolladores utilizando la **ejecutar como administrador** opción. En Windows 10, haga clic en para abrir el menú contextual de la ventana de símbolo del sistema y luego elija **más**, **ejecutar como administrador**.  
  
## <a name="see-also"></a>Vea también  

[Compilar el código de C o C++ en la línea de comandos](../build/building-on-the-command-line.md)   
[La vinculación](../build/reference/linking.md)   
[Opciones del vinculador](../build/reference/linker-options.md)   
[Compilar un programa de C o C++](../build/reference/compiling-a-c-cpp-program.md)   
[Opciones del compilador](../build/reference/compiler-options.md)