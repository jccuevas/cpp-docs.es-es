---
title: "Ejecuta una aplicación de - clr de C++ en una versión anterior del Runtime | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1f64c0dc31be260332d4d79e8fa38d63bbf6357c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Ejecutar una aplicación /clr de C++ en una versión anterior de Common Language Runtime
A menos que se especifique lo contrario, una aplicación de .NET Framework de C++ se ha compilado en la versión de common language runtime (CLR) que usa el compilador para compilar la aplicación. Sin embargo, es posible que una aplicación .exe compilado para una versión de runtime que se ejecutan en cualquier otra versión que proporciona la funcionalidad necesaria.  
  
 Para ello, proporcione un archivo app.config que contiene información de versión en tiempo de ejecución en la `supportedRuntime` etiqueta.  
  
 En tiempo de ejecución, el archivo app.config debe tener un nombre de la forma *nombreDeArchivo.ext*.config, donde *nombreDeArchivo.ext* es el nombre del archivo ejecutable que inició la aplicación, y debe estar en el mismo directorio que la aplicación ejecutable. Por ejemplo, si la aplicación se denomina TestApp.exe, el archivo app.config se denominará TestApp.exe.config.  
  
 Si especifica más de una versión en tiempo de ejecución y la aplicación se ejecuta en un equipo que tiene más de una versión en tiempo de ejecución instalada, la aplicación utiliza la primera versión que se especifica en el archivo de configuración y se instala.  
  
 Para obtener más información, consulte [Cómo: configurar una aplicación que tenga como destino una versión de .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Para que se ejecute en la versión 1.0 o 1.1 de CLR, una aplicación que se genera mediante Visual C++ compilador debe compilarse con [/CLR: initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="see-also"></a>Vea también  
 [Implementar aplicaciones de escritorio](../ide/deploying-native-desktop-applications-visual-cpp.md)