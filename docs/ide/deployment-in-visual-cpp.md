---
title: Implementación en Visual C++ | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2018
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
ms.openlocfilehash: 5b9dfdcdce618df3f2bfec64892f62aec20b6db9
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256101"
---
# <a name="deployment-in-visual-c"></a>Implementación en Visual C++

La instalación de la aplicación en un equipo que no sea el equipo de desarrollo se conoce como *implementación*. Al implementar una aplicación de Visual C++ en otro equipo, debe instalar tanto la aplicación como todos los archivos de biblioteca de los que dependa. Visual Studio ofrece tres maneras de implementar las bibliotecas de Visual C++ junto con la aplicación: *implementación central*, *implementación local* y *vinculación estática*. La implementación central coloca los archivos de biblioteca en el directorio de Windows, donde el servicio Windows Update puede actualizarlos de forma automática. La implementación local coloca los archivos de biblioteca en el mismo directorio que la aplicación. Debe volver a implementar las bibliotecas implementadas localmente para actualizarlas. La vinculación estática enlaza el código de biblioteca en la aplicación. Debe volver a compilar e implementar la aplicación para aprovechar las ventajas de las actualizaciones de las bibliotecas cuando se usa la vinculación estática.

En Visual Studio 2015, la biblioteca en tiempo de ejecución de C de Microsoft se refactorizó en componentes de biblioteca locales específicos de la versión, y ahora una nueva biblioteca de tiempo de ejecución de C Universal forma parte de Windows. Para obtener más información sobre la implementación de CRT Universal, vea [Implementación de CRT Universal](universal-crt-deployment.md).

## <a name="central-deployment"></a>Implementación central

En la implementación central, los archivos DLL de biblioteca se instalan en el directorio Windows\System32, o bien, para los archivos de biblioteca de 32 bits en sistemas x64, en el directorio Windows\SysWow64. Microsoft actualiza automáticamente sus bibliotecas que se implementan centralmente. En el caso de las bibliotecas de Visual C++ que se implementan localmente o se vinculan estáticamente, debe proporcionar las actualizaciones usted mismo.

Para implementar de forma centralizada las bibliotecas de Visual C++, puede usar uno de estos dos orígenes para los archivos de instalación:

- Archivos de *paquete redistribuible*, que son archivos ejecutables de la línea de comandos independientes que contienen todas las bibliotecas redistribuibles de Visual C++ en formato comprimido, o bien

- *Módulos de combinación redistribuibles (archivos .msm)*, que se pueden usar para implementar bibliotecas específicas, y que se incluyen en el archivo de Windows Installer (.msi) de la aplicación.

Un archivo de paquete redistribuible instala todas las bibliotecas de Visual C++ para una arquitectura del sistema concreta. Por ejemplo, si la aplicación se compila para x64, se puede usar el paquete redistribuible vcredist_x64.exe para instalar todas las bibliotecas de Visual C++ que usa la aplicación. Se puede programar el instalador de la aplicación para que ejecute el paquete redistribuible como un requisito previo antes de instalar la aplicación.

Un módulo de combinación permite incluir lógica de instalación para una biblioteca concreta de Visual C++ en un archivo de instalación de la aplicación de Windows Installer. Se pueden incluir tantos módulos de combinación como la aplicación necesite. Use los módulos de combinación cuando necesite minimizar el tamaño de los archivos binarios de la implementación.

Como la implementación central mediante un paquete redistribuible o módulos de combinación permite que Windows Update actualice de forma automática las bibliotecas de Visual C++, se recomienda usar los archivos DLL de biblioteca de la aplicación en lugar de las bibliotecas estáticas y usar la implementación central en lugar de la implementación local.

## <a name="local-deployment"></a>Implementación local

En la implementación local, los archivos de biblioteca se instalan en la carpeta de la aplicación junto con el archivo ejecutable. Se pueden instalar otras versiones de las bibliotecas redistribuibles de Visual C++ en la misma carpeta porque el nombre de archivo de cada versión incluye su número de versión. Por ejemplo, la versión 12 de la biblioteca en tiempo de ejecución de C++ es msvcp120.dll y la versión 14 es msvcp140.dll.

Una biblioteca se puede distribuir entre varios archivos DLL adicionales, conocidos como *bibliotecas DOT*. Por ejemplo, algunas funciones de la biblioteca estándar que se publicó en la versión 15.6 de Visual Studio 2017 se agregaron a msvcp140_1.dll, para conservar la compatibilidad con ABI de msvcp140.dll. Si usa Visual Studio 2017, versión 15.6 (conjunto de herramientas 14.13) o un conjunto de herramientas posterior de Visual Studio 2017, es posible que tenga que implementar localmente estas bibliotecas DOT, así como la biblioteca principal. Estas bibliotecas DOT independientes se implementan después en la siguiente versión principal de la biblioteca base, cuando cambia ABI.

Como Microsoft no puede actualizar automáticamente las bibliotecas de Visual C++ implementadas localmente, no se recomienda la implementación local de estas bibliotecas. Si decide usar la implementación local de bibliotecas redistribuibles, se recomienda que implemente su propio método de actualizar automáticamente las bibliotecas implementadas localmente.

## <a name="static-linking"></a>Vinculación estática

Además de las bibliotecas vinculadas dinámicamente, Visual Studio proporciona la mayor parte de sus bibliotecas como bibliotecas estáticas. Una biblioteca estática se puede vincular de manera estática a la aplicación, es decir, vincular el código de objeto de biblioteca directamente en la aplicación. Esto crea un archivo binario único sin una dependencia DLL, por lo que no es necesario implementar por separado los archivos de biblioteca de Visual C++. Pero este enfoque no se recomienda, porque las bibliotecas vinculadas estáticamente no se pueden actualizar en contexto. Si usa la vinculación estática y desea actualizar una biblioteca vinculada, tiene que recompilar y volver a implementar la aplicación.

## <a name="troubleshooting-deployment-issues"></a>Solución de problemas de implementación

El orden de carga de las bibliotecas de Visual C++ depende del sistema. Para diagnosticar los problemas de cargador, utilice depends.exe o where.exe. Para obtener más información, vea [Dynamic-Link Library Search Order (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx) (Orden de búsqueda de las bibliotecas de vínculos dinámicos [Windows]).

## <a name="see-also"></a>Vea también

- [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Implementación de CRT universal](universal-crt-deployment.md)
