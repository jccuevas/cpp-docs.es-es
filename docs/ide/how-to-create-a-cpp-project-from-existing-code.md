---
title: 'Cómo: Crear un proyecto de C++ a partir del código existente | Microsoft Docs'
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
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33330140"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Cómo: Crear un proyecto de C++ a partir del código existente

En Visual Studio, se pueden trasladar los archivos de código existentes a un proyecto de Visual C++ mediante el asistente **Crear nuevo proyecto de archivos de código fuente existentes**. Este asistente no está disponible en las ediciones Express anteriores de Visual Studio. Este asistente crea una solución y un proyecto que usa el sistema MSBuild para administrar los archivos de código fuente y la configuración de compilación.  
  
Trasladar los archivos de código existentes a un proyecto de Visual C++ permite usar todas las características nativas de administración de proyectos de MSBuild integradas en el IDE. Si prefiere usar el sistema de compilación existente, como archivos Make de nmake, CMake u otras alternativas, en su lugar puede usar la opción Abrir carpeta. Para más información, consulte el artículo sobre los [proyectos Abrir carpeta en Visual C++](../ide/non-msbuild-projects.md). Ambas opciones permiten usar características del IDE como [IntelliSense](/visualstudio/ide/using-intellisense) y [Propiedades del proyecto](../ide/working-with-project-properties.md).  
  
### <a name="to-create-a-c-project-from-existing-code"></a>Para crear un proyecto de C++ a partir de código existente  
  
1.  En el menú **Archivo**, seleccione **Nuevo** y, después, haga clic en **Proyecto a partir de código existente**.  
  
1.  En la primera página del asistente **Crear nuevo proyecto de archivos de código fuente existentes**, seleccione **Visual C++** en la lista **¿Qué tipo de proyecto desea crear?**. Elija **Siguiente** para continuar. 
  
1.  Especifique la ubicación del proyecto y el directorio para los archivos de código fuente. Para obtener más información sobre esta página, vea [Especificar la ubicación del proyecto y los archivos de código fuente, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-project-location-and-source-files.md). Elija **Siguiente** para continuar.  
  
1.  Especifique la configuración del proyecto que se va a usar. Para obtener más información sobre esta página, vea [Especificar configuración de proyecto, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md). Elija **Siguiente** para continuar.  

1.  Especifique los valores de configuración de depuración que se van a usar. Para obtener más información sobre esta página, vea [Especificar los valores de configuración de Debug, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-debug-configuration-settings.md). Elija **Siguiente** para continuar.  

1.  Especifique los valores de configuración de Release que se van a usar. Para obtener más información sobre esta página, vea [Especificar los valores de configuración de Release, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-release-configuration.md). Haga clic en **Finalizar** para generar el proyecto nuevo.  
  
## <a name="see-also"></a>Vea también  

[Especificar la ubicación del proyecto y los archivos de código fuente, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-project-location-and-source-files.md)   
[Especificar configuración de proyecto, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[Especificar los valores de configuración de Debug, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-debug-configuration-settings.md)   
[Especificar los valores de configuración de Release, Asistente para crear nuevo proyecto de archivos de código fuente existentes](../ide/specify-release-configuration.md)