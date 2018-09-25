---
title: Especificar eventos de compilación | Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-ide
ms.topic: conceptual
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dfdedf01c6203c483c1aa30d5d2934caa66e76d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375973"
---
# <a name="specifying-build-events"></a>Especificar eventos de compilación

Los eventos de compilación se pueden usar para especificar comandos que se ejecuten antes de que se inicie la compilación, antes del proceso de vinculación o después de que finalice la compilación.

Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación. Si se produce un error en la compilación, no se produce el evento *posterior a la compilación*; si el error se produce antes de la fase de vinculación, no se producen los eventos *anterior a la vinculación* ni *posterior a la compilación*. Además, si no es necesario vincular ningún archivo, el evento *anterior a la vinculación* no se produce. El evento *anterior a la vinculación* no está disponible en los proyectos que no contengan un paso de vinculación.

Si no es necesario compilar ningún archivo, no se producirá ningún evento de compilación.

Para obtener información general sobre los eventos de compilación, vea [Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Para especificar un evento de compilación

1. En el **Explorador de soluciones**, seleccione el proyecto para el que quiere especificar el evento de compilación.

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../ide/working-with-project-properties.md).

1. En la carpeta **Eventos de compilación**, seleccione una página de propiedades de evento de compilación.

1. Especifique las propiedades asociadas al evento de compilación:

   - En **Línea de comandos**, especifique un comando como si estuviera especificándolo en el símbolo del sistema. Especifique un comando o archivo por lotes válido, y los archivos de entrada o salida necesarios. Especifique el comando por lotes **call** antes del nombre de un archivo por lotes para garantizar que se ejecuten todos los comandos siguientes.

      Se pueden especificar varios archivos de entrada y salida simbólicamente mediante macros de MSBuild. Para obtener información sobre cómo especificar la ubicación de los archivos o los nombres de los conjuntos de archivos, vea [Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md).

      Como el carácter "%" está reservado por MSBuild, si se especifica una variable de entorno, reemplace todos los caracteres con escape **%** con la secuencia de escape hexadecimal **%25**. Por ejemplo, reemplace **%WINDIR%** con **%25WINDIR%25**. MSBuild reemplaza todas las secuencias **%25** con el carácter **%** antes de acceder a la variable de entorno.

   - En **Descripción**, escriba una descripción para este evento. La descripción se imprime en la ventana **Salida** cuando se produce este evento.

   - En **Excluir de la compilación**, especifique **Sí** si no quiere que el evento se ejecute.

## <a name="see-also"></a>Vea también

[Descripción de los pasos de compilación personalizada y los eventos de compilación](../ide/understanding-custom-build-steps-and-build-events.md)<br>
[Macros comunes para propiedades y comandos de compilación](../ide/common-macros-for-build-commands-and-properties.md)<br>
[Solucionar problemas de personalizaciones de compilación](../ide/troubleshooting-build-customizations.md)
