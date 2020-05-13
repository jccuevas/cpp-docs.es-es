---
title: /J (El tipo de carácter predeterminado no tiene signo)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: 7bcf0f2eb2bef08757250999d0a6696b256fb15c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322196"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (El tipo de carácter predeterminado no tiene signo)

Cambia el `char` tipo `signed char` `unsigned char`predeterminado de `char` a , y el tipo se `int` extiende cero cuando se ensancha a un tipo.

## <a name="syntax"></a>Sintaxis

```
/J
```

## <a name="remarks"></a>Observaciones

Si `char` un valor se `signed`declara explícitamente como , la opción **/J** no le afecta y el `int` valor se extiende cuando se amplía a un tipo.

La opción **/J** define `_CHAR_UNSIGNED`, `#ifndef` que se utiliza con el archivo `char` LIMITS.h para definir el intervalo del tipo predeterminado.

ANSI C y C++ no requieren `char` una implementación específica del tipo. Esta opción es útil cuando se trabaja con datos de caracteres que, finalmente, se traducirán a un idioma distinto del inglés.

> [!NOTE]
> Si utiliza esta opción del compilador con ATL/MFC, es posible que se genere un error. Aunque podría deshabilitar este error `_ATL_ALLOW_CHAR_UNSIGNED`definiendo , esta solución alternativa no se admite y puede que no siempre funcione.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. En el **Explorador**de soluciones , abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.

1. En el cuadro de diálogo **Páginas** de propiedades del proyecto, en el panel izquierdo, en **Propiedades de configuración**, expanda **C/C++** y, a continuación, seleccione **Línea de comandos**.

1. En el panel **Opciones adicionales,** especifique la opción del compilador **/J.**

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md)
