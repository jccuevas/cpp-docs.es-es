---
title: Especificar eventos de compilación
ms.date: 12/28/2017
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
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
ms.openlocfilehash: c8097e013f934c45b8e3860b8377bdb2bdb9d9a0
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57827224"
---
# <a name="specifying-build-events"></a>Especificar eventos de compilación

Los eventos de compilación se pueden usar para especificar comandos que se ejecuten antes de que se inicie la compilación, antes del proceso de vinculación o después de que finalice la compilación.

Los eventos de compilación se ejecutan solo si se alcanzan correctamente esos puntos en el proceso de compilación. Si se produce un error en la compilación, no se produce el evento *posterior a la compilación*; si el error se produce antes de la fase de vinculación, no se producen los eventos *anterior a la vinculación* ni *posterior a la compilación*. Además, si no es necesario vincular ningún archivo, el evento *anterior a la vinculación* no se produce. El evento *anterior a la vinculación* no está disponible en los proyectos que no contengan un paso de vinculación.

Si no es necesario compilar ningún archivo, no se producirá ningún evento de compilación.

Para obtener información general sobre los eventos de compilación, vea [Descripción de los pasos de compilación personalizada y los eventos de compilación](understanding-custom-build-steps-and-build-events.md).

### <a name="to-specify-a-build-event"></a>Para especificar un evento de compilación

1. En el **Explorador de soluciones**, seleccione el proyecto para el que quiere especificar el evento de compilación.

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](working-with-project-properties.md).

1. En la carpeta **Eventos de compilación**, seleccione una página de propiedades de evento de compilación.

1. Especifique las propiedades asociadas al evento de compilación:

   - En **Línea de comandos**, especifique un comando como si estuviera especificándolo en el símbolo del sistema. Especifique un comando o archivo por lotes válido, y los archivos de entrada o salida necesarios. Especifique el comando por lotes **call** antes del nombre de un archivo por lotes para garantizar que se ejecuten todos los comandos siguientes.

      Se pueden especificar varios archivos de entrada y salida simbólicamente mediante macros de MSBuild. Para obtener información sobre cómo especificar la ubicación de archivos o los nombres de conjuntos de archivos, consulte [macros comunes para propiedades y comandos de compilación](reference/common-macros-for-build-commands-and-properties.md).

      Como el carácter "%" está reservado por MSBuild, si se especifica una variable de entorno, reemplace todos los caracteres con escape **%** con la secuencia de escape hexadecimal **%25**. Por ejemplo, reemplace **%WINDIR%** con **%25WINDIR%25**. MSBuild reemplaza todas las secuencias **%25** con el carácter **%** antes de acceder a la variable de entorno.

   - En **Descripción**, escriba una descripción para este evento. La descripción se imprime en la ventana **Salida** cuando se produce este evento.

   - En **Excluir de la compilación**, especifique **Sí** si no quiere que el evento se ejecute.

## <a name="see-also"></a>Vea también

[Descripción de los pasos de compilación personalizada y los eventos de compilación](understanding-custom-build-steps-and-build-events.md)<br>
[Macros comunes para propiedades y comandos de compilación](reference/common-macros-for-build-commands-and-properties.md)<br>
[Solucionar problemas de personalizaciones de compilación](troubleshooting-build-customizations.md)
