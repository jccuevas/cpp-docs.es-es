---
title: /NXCOMPAT (Compatible con la prevención de ejecución de datos) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /NXCOMPAT
dev_langs:
- C++
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb4f8a91545a196bc92fdc0ec44e89a7d5680185
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible con la prevención de ejecución de datos)

Indica que un archivo ejecutable es compatible con la característica de prevención de ejecución de datos de Windows.

## <a name="syntax"></a>Sintaxis

> **/NXCOMPAT**[**: N**]

## <a name="remarks"></a>Comentarios

De forma predeterminada, **/NXCOMPAT** se encuentra en.

**/NXCOMPAT:no** puede utilizarse para especificar explícitamente un archivo ejecutable como no compatible con la prevención de ejecución de datos.

Para obtener más información sobre la Prevención de ejecución de datos, vea estos artículos:

- [Una descripción detallada de la característica de prevención de ejecución de datos (DEP)](http://go.microsoft.com/fwlink/p/?linkid=157771)

- [Prevención de ejecución de datos](http://go.microsoft.com/fwlink/p/?linkid=157770)

- [Prevención de ejecución de datos (Windows Embedded)](http://go.microsoft.com/fwlink/p/?linkid=157768)

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Elija la **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Escriba la opción en la **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
