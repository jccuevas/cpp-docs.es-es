---
title: "Personalizaciones de compilación de la solución de problemas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- build events [C++], troubleshooting
- builds [C++], build events
- troubleshooting [C++], builds
- build steps [C++], troubleshooting
- events [C++], build
- builds [C++], troubleshooting
- custom build steps [C++], troubleshooting
ms.assetid: e4ceb177-fbee-4ed3-a7d7-80f0d78c1d07
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fa3b2d3910a71d189f5177e13fbd91930e15ee8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="troubleshooting-build-customizations"></a>Solucionar problemas de personalizaciones de compilación
Si los pasos de compilación personalizado o eventos no se comportan tal y como esperaba, hay varias cosas que puede hacer para intentar comprender la causa del error.  
  
-   Asegúrese de que los archivos de que los pasos de compilación personalizada generan coinciden con los archivos que se declara como salidas.  
  
-   Si los pasos de compilación personalizada generan los archivos que son entradas o dependencias de otros pasos (personalizadas o no) de compilación, asegúrese de dichos archivos se agregan al proyecto. Y asegúrese de que las herramientas que usan esos archivos ejecutan después de paso de compilación personalizado.  
  
-   Para mostrar lo que realmente está haciendo el paso de compilación personalizada, agregue `@echo on` como el primer comando. Los eventos de compilación y los pasos de compilación se colocan en un archivo .bat temporal y ejecutar cuando se compila el proyecto. Por lo tanto, puede agregar comprobación de errores a los eventos de compilación o comandos de paso de compilación.  
  
-   Examine el registro de compilación en el directorio de archivos intermedios para ver lo que realmente se ejecuta. La ruta de acceso y el nombre del registro de compilación se representa mediante el **MSBuild** expresión de macro, **$ (IntDir)\\$(MSBuildProjectName) .log**.  
  
-   Modificar la configuración del proyecto para obtener más información que la cantidad de información en el registro de compilación predeterminada. En el menú **Herramientas** , haga clic en **Opciones**. En el **opciones** cuadro de diálogo, haga clic en el **proyectos y soluciones** nodo y, a continuación, haga clic en el **compilar y ejecutar** nodo. A continuación, en la **contenido de archivo de registro de compilación de proyecto de MSBuild** cuadro, haga clic en **Detailed**.  
  
-   Compruebe que los valores de cualquier archivo directorios o nombres de las macros que usa. Puede repetir las macros individualmente o puede agregar `copy %0 command.bat` al principio del paso de compilación personalizada, que se copiarán los comandos del paso en command.bat con todas las macros expandidas.  
  
-   Ejecutar pasos de compilación personalizada y generar eventos de forma individual para comprobar su comportamiento.  
  
## <a name="see-also"></a>Vea también  
 [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)