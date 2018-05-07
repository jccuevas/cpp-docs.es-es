---
title: 'Cómo: crear un proyecto de C++ a partir de código existente | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1786e5704d7afd07576ab738d907eb841518f8be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Cómo: Crear un proyecto de C++ a partir del código existente

En Visual Studio, puede trasladar los archivos de código existentes en un proyecto de Visual C++ mediante el uso de la **crear nuevo proyecto de archivos de código existentes** asistente. Este asistente no está disponible en las ediciones Express anteriores de Visual Studio. Este asistente crea una nueva solución y un proyecto que utiliza el sistema MSBuild para administrar los archivos de origen y la configuración de compilación.  
  
Trasladar los archivos de código existentes a un proyecto de Visual C++ permite usar todas las características de administración de proyectos de MSBuild nativo integradas en el IDE. Si prefiere usar el sistema de compilación existentes, como archivos MAKE de nmake, CMake o alternativas, puede utilizar la opción de Abrir carpeta en su lugar. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](../ide/non-msbuild-projects.md). Ambas opciones le permiten usar características del IDE como [IntelliSense](/visualstudio/ide/using-intellisense) y [propiedades del proyecto](../ide/working-with-project-properties.md).  
  
### <a name="to-create-a-c-project-from-existing-code"></a>Para crear un proyecto de C++ a partir de código existente  
  
1.  En el **archivo** menú, elija **New**y, a continuación, haga clic en **proyecto del código existente**.  
  
1.  En la primera página de la **crear nuevo proyecto de archivos de código existentes** asistente, seleccione **Visual C++** en el **¿qué tipo de proyecto desea crear** lista. Elija **Siguiente** para continuar. 
  
1.  Especifique la ubicación del proyecto y el directorio para los archivos de origen. Para obtener más información en esta página, vea [especificar la ubicación del proyecto y archivos de código fuente, Asistente Crear nuevo proyecto de existente código archivos](../ide/specify-project-location-and-source-files.md). Elija **Siguiente** para continuar.  
  
1.  Especifique la configuración del proyecto para usar. Para obtener más información en esta página, vea [especificar configuración de proyecto, el Asistente Crear nuevo proyecto de existente código archivos](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md). Elija **Siguiente** para continuar.  

1.  Especifique los valores de configuración de depuración para usar. Para obtener más información en esta página, vea [especifique los valores de configuración de Debug, Asistente Crear nuevo proyecto de existente código archivos](../ide/specify-debug-configuration-settings.md). Elija **Siguiente** para continuar.  

1.  Especifique los valores de configuración de la versión para usar. Para obtener más información en esta página, vea [especificar valores de configuración de Release, Asistente Crear nuevo proyecto de existente código archivos](../ide/specify-release-configuration.md). Elija **finalizar** para generar el nuevo proyecto.  
  
## <a name="see-also"></a>Vea también  

[Especifica el proyecto de ubicación y archivos de código fuente, crear nuevo proyecto de Asistente para archivos de código existentes](../ide/specify-project-location-and-source-files.md)   
[Especificar configuración de proyecto, crear nuevo proyecto de Asistente para archivos de código existentes](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[Especifique los valores de configuración de Debug, crear nuevo proyecto de Asistente para archivos de código existentes](../ide/specify-debug-configuration-settings.md)   
[Especificar los valores de configuración de Release, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-release-configuration.md)