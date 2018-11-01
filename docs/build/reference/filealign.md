---
title: /FILEALIGN (Alinear secciones de archivos)
ms.date: 10/23/2017
f1_keywords:
- /filealign
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
ms.openlocfilehash: d218ce4793e68fe3b700a0776fa5db665568f736
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494591"
---
# <a name="filealign-align-sections-in-files"></a>/FILEALIGN (Alinear secciones de archivos)

El **/FILEALIGN** opción del vinculador le permite especificar la alineación de las secciones que se escriben en el archivo de salida como un múltiplo de un tamaño especificado.

## <a name="syntax"></a>Sintaxis

> __/ FILEALIGN:__*tamaño*

### <a name="parameters"></a>Parámetros

*size*<br/>
El tamaño de alineación de sección en bytes, que debe ser una potencia de dos.

## <a name="remarks"></a>Comentarios

El **/FILEALIGN** opción hace que el vinculador alinear cada sección en el archivo de salida en un límite que es un múltiplo de la *tamaño* valor. De forma predeterminada, el vinculador no utiliza un tamaño fijo de alineación.

El **/FILEALIGN** opción puede utilizarse para hacer más eficaz el uso de disco o hacer página carga desde el disco más rápido. Un tamaño más pequeño de la sección puede ser útil para aplicaciones que se ejecutan en dispositivos más pequeños, o para mantener las descargas más pequeñas. Alineación de sección en el disco no afecta a la alineación en memoria.

Use [DUMPBIN](dumpbin-reference.md) para ver información sobre las secciones en el archivo de salida.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **línea de comandos** página de propiedades de la **vinculador** carpeta.

1. Escriba el nombre de opción **/FILEALIGN:** y el tamaño de la **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)