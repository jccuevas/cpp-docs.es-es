---
title: "Especificar eventos de compilación | Documentos de Microsoft"
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
dev_langs:
- C++
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 825eec000a2b08bd7a5a4d7769405df2f5570523
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="specifying-build-events"></a>Especificar eventos de compilación

Puede usar eventos de compilación para especificar los comandos que se ejecutan antes de iniciarse la compilación, antes del proceso de vinculación o una vez finalizada la compilación.

Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación. Si se produce un error en la compilación, el *posterior a la compilación* no producirán eventos; si el error se produce antes de la fase de vinculación, ni la *anterior a la vinculación* ni *posterior a la compilación* eventos se produce. Además, si no hay archivos deben vincularse, el *anterior a la vinculación* no se produce el evento. El *anterior a la vinculación* eventos no está disponible en los proyectos que no contengan un paso de vinculación.

Si no hay archivos deben compilarse, se producirá ningún evento de compilación.

Para obtener información general sobre los eventos de compilación, consulte [Introducción a los pasos de compilación personalizada y eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Para especificar un evento de compilación

1. En el **Explorador de soluciones**, seleccione el proyecto para el que quiere especificar el evento de compilación.

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../ide/working-with-project-properties.md).

1. En el **eventos de compilación** carpeta, seleccione una página de propiedades de evento de compilación.

1. Especifique las propiedades asociadas al evento de compilación:

   - En **línea de comandos**, especifique un comando como si estuviera especificándolo en el símbolo del sistema. Especifique un comando válido o archivo por lotes, y cualquier entrada necesaria o archivos de salida. Especifique el **llamar** el comando antes del nombre de un archivo por lotes para garantizar que todos los comandos subsiguientes se ejecutan por lotes.

      Varios archivos de entrada y salidos se pueden especificar simbólicamente con macros MSBuild. Para obtener información sobre cómo especificar la ubicación de archivos o los nombres de los conjuntos de archivos, consulte [comunes Macros para propiedades y comandos de generación](../ide/common-macros-for-build-commands-and-properties.md).

      Dado que el carácter '%' está reservado por MSBuild, si especifica una variable de entorno reemplaza cada  **%**  carácter con escape la **% 25** secuencia de escape hexadecimal. Por ejemplo, reemplace **% WINDIR %** con **25WINDIR % 25**. MSBuild reemplaza cada **% 25** de secuencia con el  **%**  antes de tener acceso a la variable de entorno de caracteres.

   - En **descripción**, escriba una descripción para este evento. La descripción se imprime en la **salida** ventana cuando se produce este evento.

   - En **excluir de la generación**, especifique **Sí** si no desea que se ejecute el evento.

## <a name="see-also"></a>Vea también

[Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)  
[Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)  
[Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md)  
