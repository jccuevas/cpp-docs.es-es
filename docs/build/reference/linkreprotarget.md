---
title: /LINKREPROTARGET (nombre de archivo de reproducción de vínculos)
description: Opción de herramienta de biblioteca o vinculador para establecer un nombre de archivo de destino para una reproducción de vínculo.
ms.date: 09/24/2019
f1_keywords:
- /LINKREPROTARGET
helpviewer_keywords:
- LINKREPROTARGET linker option
- /LINKREPROTARGET linker option
- -LINKREPROTARGET linker option
- linker repro reporting
ms.openlocfilehash: 4912e8bc64d31e3ecc97ea25783c7329e7d7861c
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686909"
---
# <a name="linkreprotarget-link-repro-file-name"></a>/LINKREPROTARGET (nombre de archivo de reproducción de vínculos)

Indica al vinculador o a la herramienta de biblioteca que genere una reproducción de vínculo solo cuando el destino tiene el nombre de archivo especificado.

## <a name="syntax"></a>Sintaxis

> **/LINKREPROTARGET:** _nombre de archivo_

### <a name="arguments"></a>Argumentos

**/LINKREPROTARGET:** _nombre de archivo_\
Nombre del archivo de destino por el que se va a filtrar. Una reproducción de vínculo solo se genera cuando el archivo con nombre es el destino de salida. Los nombres de archivo que incluyen espacios deben ir entre comillas dobles. El nombre de archivo debe incluir el nombre base y la extensión, pero no la ruta de acceso.

## <a name="remarks"></a>Comentarios

La opción **/LINKREPROTARGET** se usa para especificar un nombre de archivo de destino para el que se va a generar una *reproducción de vínculo* . Una reproducción de vínculo es un conjunto de artefactos de compilación que permiten a Microsoft reproducir un problema que se produce en el momento de la vinculación o durante las operaciones de la biblioteca. La herramienta enlazador o biblioteca genera una reproducción de vínculo cuando se especifica la opción [/LINKREPRO](linkrepro.md) , o cuando se establece la variable de entorno `link_repro` en el entorno de compilación de la línea de comandos.

La opción **/LINKREPROTARGET** es útil en compilaciones complejas que invocan la herramienta de biblioteca o de vinculador más de una vez. Permite especificar un destino específico para la reproducción de vínculos, como *Problem. dll*. Permite generar la reproducción de vínculos solo cuando la herramienta genera un archivo específico.

Para obtener más información sobre cómo y cuándo crear una reproducción de vínculos, vea [la sección sobre](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros) [Cómo notificar un problema con el conjunto de herramientas C++ de Microsoft](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Las opciones **/LINKREPRO** y [/out](out-output-file-name.md) deben establecerse para que la opción **/LINKREPROTARGET** tenga algún efecto.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**línea de comandos** del vinculador ** >  del** **enlazador** > .

1. Escriba la opción **/LINKREPROTARGET:** _nombre-archivo_ en el cuadro **opciones adicionales** . Seleccione **Aceptar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

@No__t de [Referencia del enlazador de MSVC](linking.md)-1
[MSVC opciones del vinculador](linker-options.md)\
[/LINKREPRO](linkrepro.md)
