---
title: Ejecutar una aplicación /clr de C++ en una versión anterior de Runtime
ms.date: 11/04/2016
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
ms.openlocfilehash: 9b26439d389cb4035541cedde8a5b5cf50682098
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786479"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Ejecutar una aplicación /clr de C++ en una versión anterior de Common Language Runtime

A menos que se especifique lo contrario, una aplicación .NET Framework de C++ se compila para ejecutarse en la versión de Common Language Runtime (CLR) que usa el compilador para compilar la aplicación. Pero una aplicación .exe compilada para una versión del runtime se puede ejecutar en cualquier otra versión que proporcione la funcionalidad necesaria.

Para ello, proporcione un archivo app.config que contenga la información de versión del runtime en la etiqueta `supportedRuntime`.

En tiempo de ejecución, el archivo app.config debe tener un nombre con el formato *nombreDeArchivo.ext*.config, donde *nombreDeArchivo.ext* es el nombre del archivo ejecutable que inició la aplicación, y debe estar en el mismo directorio que el archivo ejecutable. Por ejemplo, si la aplicación se denomina TestApp.exe, el archivo app.config se denominará TestApp.exe.config.

Si se especifica más de una versión del runtime y la aplicación se ejecuta en un equipo que tiene instalada más de una versión del runtime, la aplicación usa la primera versión que se especifique en el archivo de configuración y se instala.

## <a name="see-also"></a>Vea también

[Implementar aplicaciones de escritorio](deploying-native-desktop-applications-visual-cpp.md)
