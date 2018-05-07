---
title: Implementación en Visual C++ | Documentos de Microsoft
ms.custom: ''
ms.date: 03/13/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9880272a09cde3bec0dbbbe03bfc30821591d6b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="deployment-in-visual-c"></a>Implementación en Visual C++

Instalación de la aplicación en un equipo que no sea el equipo de desarrollo se conoce como *implementación*. Al implementar una aplicación de Visual C++ a otro equipo, debe instalar la aplicación y los archivos de biblioteca que depende. Visual Studio ofrece tres maneras de implementar las bibliotecas de Visual C++ junto con la aplicación: *implementación central*, *implementación local*, y *vinculación estática*. Implementación central coloca los archivos de biblioteca en el directorio de Windows, donde el servicio Windows Update puede actualizarlos automáticamente. Implementación local coloca los archivos de biblioteca en el mismo directorio que la aplicación. Debe volver a implementar las bibliotecas implementadas localmente para actualizarlos. Vinculación estática, enlaza el código de biblioteca en la aplicación. Debe volver a compilar e implementar la aplicación para aprovechar las ventajas de las actualizaciones a las bibliotecas cuando se usa la vinculación estática.

## <a name="central-deployment"></a>Implementación central

En la implementación central, los archivos DLL de biblioteca se instalan en el directorio Windows\System32 o archivos de biblioteca de 32 bits en x64 de sistemas, el directorio Windows\SysWow64. Microsoft actualiza automáticamente sus bibliotecas que se implementan centralmente. Para las bibliotecas de Visual C++ que se implementan localmente o se vinculan estáticamente, debe proporcionar las actualizaciones.

Para implementar de forma centralizada las bibliotecas de Visual C++, puede usar uno de estos dos orígenes para los archivos de instalación:

- *Paquete redistribuible de* archivos, que son ejecutables independientes de línea de comandos que contienen todas las bibliotecas redistribuibles de Visual C++ en un formato comprimido, o

- *Módulos de combinación redistribuibles* (archivos .msm), que puede usar para implementar determinadas bibliotecas y que se incluyen en el archivo de Windows Installer (.msi) de la aplicación.

Un archivo de paquete redistribuible instala todas las bibliotecas de Visual C++ para una arquitectura de sistema determinado. Por ejemplo, si la aplicación se compila para x64, puede usar el paquete redistribuible vcredist_x64.exe para instalar todas las bibliotecas de Visual C++ que utiliza la aplicación. Puede programar el instalador de la aplicación para ejecutar el paquete redistribuible como requisito previo antes de instalar la aplicación.

Un módulo de combinación permite incluir lógica de instalación para una biblioteca específica de Visual C++ en un archivo de configuración de aplicación de Windows Installer. Puede incluir tantos o tan pocos módulos de combinación como requiera la aplicación. Utilice los módulos de combinación cuando necesite minimizar el tamaño de los archivos binarios de implementación.

Como la implementación central mediante un paquete redistribuible o módulos de combinación permite que Windows Update actualizar automáticamente las bibliotecas de Visual C++, se recomienda que utilice la biblioteca DLL de la aplicación en lugar de las bibliotecas estáticas y use central implementación en lugar de la implementación local.

## <a name="local-deployment"></a>Implementación local

En la implementación local, los archivos de biblioteca se instalan en la carpeta de aplicación junto con el archivo ejecutable. Versiones diferentes de bibliotecas de Visual C++ redistributable pueden instalarse en la misma carpeta porque el nombre de archivo de cada versión incluye su número de versión. Por ejemplo, la versión 12 de la biblioteca en tiempo de ejecución de C++ es msvcp120.dll y la versión 14 es msvcp140.dll.

Una biblioteca puede distribuirse entre varios archivos DLL adicionales, conocidas como *punto bibliotecas*. Por ejemplo, algunas funciones en la biblioteca estándar que se publicó en Visual Studio 2017 versión 15.6 se agregan en msvcp140_1.dll, al preverve la compatibilidad de la ABI de msvcp140.dll. Si utiliza la versión de Visual Studio de 2017 15,6 (conjunto de herramientas 14.13) o un conjunto de herramientas de una versión posterior de Visual Studio de 2017, necesitará implementar localmente estas bibliotecas de punto, así como la biblioteca principal. Estas bibliotecas punto independiente, a continuación, se agrupan en la siguiente versión principal de la biblioteca base, cuando cambia de la ABI.

Dado que Microsoft no puede preparar automáticamente actualizaciones localmente implementan bibliotecas de Visual C++, no se recomienda la implementación local de estas bibliotecas. Si decide usar la implementación local de bibliotecas redistribuibles, se recomienda que implemente su propio método de actualizar automáticamente las bibliotecas implementadas localmente.

## <a name="static-linking"></a>Vinculación estática

Además de las bibliotecas vinculadas dinámicamente, Visual Studio proporciona la mayor parte de sus bibliotecas como bibliotecas estáticas. Estáticamente, puede vincular una biblioteca estática a la aplicación, es decir, vincular el código de objeto de biblioteca directamente en la aplicación. Esto crea un archivo binario único sin una dependencia DLL, por lo que no tiene que implementar por separado los archivos de biblioteca de Visual C++. Sin embargo, no se recomienda este enfoque porque las bibliotecas vinculadas estáticamente no se puede actualizar en su lugar. Si usa la vinculación estática y desea actualizar una biblioteca vinculada, tiene que recompilar y volver a implementar la aplicación.

## <a name="troubleshooting-deployment-issues"></a>Solucionar problemas de implementación

El orden de carga de las bibliotecas de Visual C++ es dependiente del sistema. Para diagnosticar los problemas de cargador, utilice depends.exe o where.exe. Para obtener más información, consulte [orden de búsqueda de biblioteca de vínculos dinámicos (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).

## <a name="see-also"></a>Vea también

[Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)