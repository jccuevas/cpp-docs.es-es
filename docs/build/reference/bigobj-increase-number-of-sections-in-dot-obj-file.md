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
ms.openlocfilehash: 46399dc0c1ff552b4fc963b686ac6aa6df8b6f71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272980"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Aumentar el número de secciones en el archivo .Obj)

**/bigobj** aumenta el número de secciones que puede contener un archivo de objeto.

## <a name="syntax"></a>Sintaxis

> **/bigobj**

## <a name="remarks"></a>Comentarios

De forma predeterminada, un archivo objeto puede contener hasta 65.279 (casi 2 ^ 16) secciones direccionables. Este límite se aplica independientemente de qué destino de plataforma especificada. **/bigobj** incrementa esa capacidad de direccionamiento a 4.294.967.296 (2 ^ 32).

La mayoría de los módulos nunca generan un archivo .obj que contiene más de 65.279 secciones. Sin embargo, el código generado a la máquina o código que hace un uso intensivo de las bibliotecas de plantillas, puede requerir archivos .obj que puedan contener más secciones. **/ bigobj** está habilitada de forma predeterminada en los proyectos de plataforma Universal de Windows (UWP) porque el código XAML generado por la máquina incluye un gran número de encabezados. Si deshabilita esta opción en un proyecto de aplicación para UWP, el código puede generar el error del compilador C1128.

Para obtener información sobre el formato de archivo objeto COFF de PE, consulte [formato PE](/windows/desktop/debug/pe-format) en la documentación de Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Escriba el **/bigobj** opción del compilador en el **opciones adicionales** cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
