---
title: /errorReport (Informar de los errores del compilador)
description: Referencia de la opción de líneaC++ de comandos de Microsoft C/Compiler/errorreport.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: 8d4a3c4d5fd918973bbf8057e0c073c680e6995e
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257655"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (Informar de los errores del compilador)

> [!NOTE]
> La opción **/errorreport** está en desuso. A partir de Windows Vista, los informes de errores se controlan mediante la configuración de [Informe de errores de Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Sintaxis

> **/errorreport:** \[**none** \| **prompt** \| **Queue** \| **send** ]

## <a name="remarks"></a>Observaciones

Se produce un error interno del compilador (ICE) cuando el compilador no puede procesar un archivo de código fuente. Cuando se produce un ICE, el compilador no genera un archivo de salida ni ningún diagnóstico útil que pueda usar para corregir el código.

La configuración del servicio Informe de errores de Windows invalida los argumentos **/errorreport** . El compilador envía automáticamente informes de errores internos a Microsoft, si los informes se habilitan mediante Informe de errores de Windows. No se envía ningún informe si está deshabilitado por Informe de errores de Windows.


### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Abra las **propiedades de configuración** > página de propiedades **avanzadas** de **CC++ /**  > .

1. Modifique la propiedad **informes de errores** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Consulte también

\ [Opciones del compilador MSVC](compiler-options.md)
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
