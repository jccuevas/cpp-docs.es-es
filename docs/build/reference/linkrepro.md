---
title: /LINKREPRO (nombre del directorio de reproducción de vínculos)
description: Opción de herramienta de biblioteca o vinculador para establecer el directorio de una reproducción de vínculo.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPRO
helpviewer_keywords:
- LINKREPRO linker option
- /LINKREPRO linker option
- -LINKREPRO linker option
- linker repro reporting
ms.openlocfilehash: d81fb529cdbb0741c6dff58032dad97df89b4d4f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686921"
---
# <a name="linkrepro-link-repro-directory-name"></a>/LINKREPRO (nombre del directorio de reproducción de vínculos)

Indica al vinculador o a la herramienta de biblioteca que genere una reproducción de vínculo en un directorio especificado.

## <a name="syntax"></a>Sintaxis

> **/LINKREPRO:** _nombre del directorio_

### <a name="arguments"></a>Argumentos

**/LINKREPRO:** _nombre de directorio_\
Directorio especificado por el usuario en el que se va a almacenar la reproducción de vínculos. Los nombres de directorio que incluyen espacios deben ir entre comillas dobles.

## <a name="remarks"></a>Comentarios

La opción **/LINKREPRO** se usa para crear una *reproducción de vínculo*. Es un conjunto de artefactos de compilación que permiten a Microsoft reproducir un problema que se produce en el momento de la vinculación o durante las operaciones de la biblioteca. Resulta útil para problemas como un bloqueo de back-end que implique la generación de código en tiempo de vínculo (LTCG), un error del vinculador LNK1000 o un bloqueo del enlazador. La herramienta genera una reproducción de vínculo al especificar la opción del vinculador **/LINKREPRO** , o al establecer la variable de entorno `link_repro` en el entorno de compilación de la línea de comandos. Para obtener más información, vea [la sección acerca de](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) [Cómo notificar un problema con el conjunto de C++ herramientas de Microsoft](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Tanto la opción del vinculador **/LINKREPRO** como la variable de entorno `link_repro` requieren que se especifique un directorio de salida para la reproducción de vínculos. En la línea de comandos o en el IDE, especifique el directorio con una opción **/LINKREPRO:** _Directory-name_ . El _nombre de directorio_ que especifique puede ser una ruta de acceso absoluta o relativa, pero el directorio debe existir. La opción de línea de comandos reemplaza cualquier valor de directorio establecido en la variable de entorno `link_repro`.

Para obtener información sobre cómo limitar la generación de reproducción de vínculos a un nombre de archivo de destino específico, consulte la opción [/LINKREPROTARGET](linkreprotarget.md) . Esta opción se puede usar para especificar un destino específico para el que se va a generar una reproducción de vínculo. Es útil en compilaciones complejas que invocan la herramienta de biblioteca o de vinculador más de una vez.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**línea de comandos** del vinculador ** >  **del**enlazador** > .

1. Escriba la opción **/LINKREPRO:** _Directory-name_ en el cuadro **opciones adicionales** . El valor _de nombre de directorio_ que especifique debe existir. Seleccione **Aceptar** para aplicar el cambio.

Una vez que haya generado la reproducción de vínculos, vuelva a abrir esta página de propiedades para quitar la opción **/LINKREPRO** de las compilaciones.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

@No__t de [Referencia del enlazador de MSVC](linking.md)-1
[MSVC opciones del vinculador](linker-options.md)\
[/LINKREPROTARGET](linkreprotarget.md)
