---
title: Ejecutar una aplicación -clr de C++ en una versión anterior de Common Language Runtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8e76930eb9191d27085d92a9d3a678812715fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323620"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Ejecutar una aplicación /clr de C++ en una versión anterior de Common Language Runtime
A menos que se especifique lo contrario, una aplicación .NET Framework de C++ se compila para ejecutarse en la versión de Common Language Runtime (CLR) que usa el compilador para compilar la aplicación. Pero una aplicación .exe compilada para una versión del runtime se puede ejecutar en cualquier otra versión que proporcione la funcionalidad necesaria.  
  
 Para ello, proporcione un archivo app.config que contenga la información de versión del runtime en la etiqueta `supportedRuntime`.  
  
 En tiempo de ejecución, el archivo app.config debe tener un nombre con el formato *nombreDeArchivo.ext*.config, donde *nombreDeArchivo.ext* es el nombre del archivo ejecutable que inició la aplicación, y debe estar en el mismo directorio que el archivo ejecutable. Por ejemplo, si la aplicación se denomina TestApp.exe, el archivo app.config se denominará TestApp.exe.config.  
  
 Si se especifica más de una versión del runtime y la aplicación se ejecuta en un equipo que tiene instalada más de una versión del runtime, la aplicación usa la primera versión que se especifique en el archivo de configuración y se instala.  
  
 Para obtener más información, vea [Cómo: Configurar una aplicación para que admita .NET Framework 4 o 4.5](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Para que se ejecute en la versión 1.0 o 1.1 de CLR, una aplicación compilada mediante el compilador de Visual C++ se debe compilar con [/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)