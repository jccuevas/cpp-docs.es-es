---
title: /ERRORREPORT (Informar de los errores del compilador)
description: Guía de referencia de las opciones de la línea de comandos de Microsoft NMAKE.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 5e919d4f7eb59524b9145c8e3e59613e60aef1d2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257694"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Informar de los errores del compilador)

La opción **/errorreport** está en desuso. A partir de Windows Vista, los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Sintaxis

> **/Errorreport:** \[ **none** \| **prompt** \| **Queue** \| **send** ]

## <a name="remarks"></a>Observaciones

La configuración del servicio Informe de errores de Windows invalida los argumentos **/errorreport** . El enlazador envía automáticamente informes de errores internos a Microsoft, si los informes están habilitados por Informe de errores de Windows. No se envía ningún informe si está deshabilitado por Informe de errores de Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Abra las **propiedades de configuración** > **enlazador** > página de propiedades **avanzadas** .

1. Modifique la propiedad **informes de errores** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Consulte también

\ de [Referencia del enlazador de MSVC](linking.md)
[Opciones del vinculador MSVC](linker-options.md)
