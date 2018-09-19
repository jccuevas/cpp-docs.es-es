---
title: /FILEALIGN (Alinear secciones de archivos) | Microsoft Docs
ms.date: 10/23/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /filealign
dev_langs:
- C++
helpviewer_keywords:
- linker align sections
- /FILEALIGN linker option
- -FILEALIGN linker option
- FILEALIGN linker option
ms.assetid: c1017a35-8d71-4ad9-934b-a3e3ea037fa0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 630fe7014c87487a9b4df61de60ac8f5518593e0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720023"
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