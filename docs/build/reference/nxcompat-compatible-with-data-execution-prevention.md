---
title: /NXCOMPAT (compatible con la prevención de ejecución de datos)
description: Describe la opción del vinculador Microsoft C/C++ (MSVC)/NXCompat, que marca un ejecutable como compatible con la prevención de ejecución de datos (DEP).
ms.date: 12/17/2019
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: f3a0906a49e3524fff3e1ef1643d1eceee28f169
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298992"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (compatible con la prevención de ejecución de datos)

Indica que un ejecutable es compatible con la característica prevención de ejecución de datos de Windows.

## <a name="syntax"></a>Sintaxis

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Notas

De forma predeterminada, **/NXCompat** está activado.

**/NXCompat: no** se puede usar para especificar explícitamente un ejecutable como incompatible con la prevención de ejecución de datos.

Para obtener más información sobre la Prevención de ejecución de datos, vea estos artículos:

- [Prevención de ejecución de datos](/windows/win32/Memory/data-execution-prevention)

- [Prevención de ejecución de datos (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Para establecer esta opción del vinculador en Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Elija las **propiedades de configuración** > **enlazador** > página de propiedades **línea de comandos** .

1. Escriba la opción en el cuadro **opciones adicionales** . Elija **Aceptar** o **aplicar** para aplicar el cambio.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador de MSVC](linking.md)\
[Opciones del enlazador MSVC](linker-options.md)
