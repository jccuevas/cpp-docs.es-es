---
title: /NXCOMPAT (compatible con la prevención de ejecución de datos)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: a8550337189f9c92a1c8a8d86f2f9b2b829bbc3e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813323"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible con la prevención de ejecución de datos)

Indica que un archivo ejecutable es compatible con la característica Prevención de ejecución de datos de Windows.

## <a name="syntax"></a>Sintaxis

> **/NXCOMPAT**[**:NO**]

## <a name="remarks"></a>Comentarios

De forma predeterminada, **/NXCOMPAT** está activado.

**: No** puede usarse para especificar explícitamente un archivo ejecutable como no compatible con la prevención de ejecución de datos.

Para obtener más información sobre la Prevención de ejecución de datos, vea estos artículos:

- [Una descripción detallada de la característica de prevención de ejecución de datos (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Prevención de ejecución de datos](/windows/desktop/Memory/data-execution-prevention)

- [Prevención de ejecución de datos (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Elija la **propiedades de configuración** > **vinculador** > **línea de comandos** página de propiedades.

1. Especifique la opción en el **opciones adicionales** cuadro. Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
