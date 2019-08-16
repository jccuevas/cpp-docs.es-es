---
title: /NXCOMPAT (compatible con la prevención de ejecución de datos)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: 7c788f5ec499f0edf0c44f1ff269af9767af6c08
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492660"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible con la prevención de ejecución de datos)

Indica que un ejecutable es compatible con la característica prevención de ejecución de datos de Windows.

## <a name="syntax"></a>Sintaxis

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Comentarios

De forma predeterminada, **/NXCompat** está activado.

**/NXCompat: no** se puede usar para especificar explícitamente un ejecutable como incompatible con la prevención de ejecución de datos.

Para obtener más información sobre la Prevención de ejecución de datos, vea estos artículos:

- [Una descripción detallada de la característica prevención de ejecución de datos (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Prevención de ejecución de datos](/windows/win32/Memory/data-execution-prevention)

- [Prevención de ejecución de datos (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Elija la página de propiedades**línea de comandos** del**vinculador** > de **propiedades** > de configuración.

1. Escriba la opción en el cuadro **opciones adicionales** . Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
