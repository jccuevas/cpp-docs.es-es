---
title: /bigobj (Aumentar el número de secciones en el archivo .Obj)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 30c02c72496e3bb91da3b39e1870f1dc5a2c040a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493112"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Aumentar el número de secciones en el archivo .Obj)

**/bigobj** aumenta el número de secciones que puede contener un archivo objeto.

## <a name="syntax"></a>Sintaxis

> **/bigobj**

## <a name="remarks"></a>Comentarios

De forma predeterminada, un archivo objeto puede contener hasta 65.279 (casi 2 ^ 16) secciones direccionables. Este límite se aplica independientemente de la plataforma de destino que se especifique. **/bigobj** aumenta la capacidad de la dirección a 4.294.967.296 (2 ^ 32).

La mayoría de los módulos nunca generan un archivo. obj que contiene más de 65.279 secciones. Sin embargo, el código generado por el equipo o el código que hace un uso intensivo de las bibliotecas de plantillas puede requerir archivos. obj que pueden contener más secciones. **/bigobj** está habilitado de forma predeterminada en los proyectos de plataforma universal de Windows (UWP) porque el código XAML generado por el equipo incluye un gran número de encabezados. Si deshabilita esta opción en un proyecto de aplicación para UWP, el código puede generar el error del compilador C1128.

Para obtener información sobre el formato de archivo de objeto PE-COFF, consulte [formato PE](/windows/win32/debug/pe-format) en la documentación de Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **Línea de comandos**.

1. Escriba la opción del compilador **/bigobj** en el cuadro **opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
