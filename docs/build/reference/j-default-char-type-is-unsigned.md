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
ms.openlocfilehash: c709e991574cef481aa8357a789701bba9831d92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528094"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (El tipo de carácter predeterminado no tiene signo)

Cambia el valor predeterminado `char` escriba desde `signed char` a `unsigned char`y el `char` tipo es completa con ceros cuando se lo se amplía a un `int` tipo.

## <a name="syntax"></a>Sintaxis

```
/J
```

## <a name="remarks"></a>Comentarios

Si un `char` valor se declara explícitamente como `signed`, **/j** opción no le afecta y el valor es la extensión de signo cuando se lo se amplía a un `int` tipo.

El **/j** define la opción `_CHAR_UNSIGNED`, que se usa con `#ifndef` en el archivo LIMITS.h para definir el intervalo del valor predeterminado `char` tipo.

ANSI C y C++ no requieren una implementación específica de la `char` tipo. Esta opción es útil cuando se trabaja con datos de caracteres que finalmente se traducirá en un idioma distinto del inglés.

> [!NOTE]
>  Si usa esta opción del compilador con ATL y MFC, es posible que se genera un error. Aunque se podía deshabilitar este error definiendo `_ATL_ALLOW_CHAR_UNSIGNED`, esta solución no se admite y no siempre funcionen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. En el **Explorador de soluciones**, abra el menú contextual del proyecto y, a continuación, elija **Propiedades**.

1. En el proyecto **páginas de propiedades** cuadro de diálogo, en el panel izquierdo bajo **propiedades de configuración**, expanda **C o C++** y, a continuación, seleccione **delíneadecomandos**.

1. En el **opciones adicionales** panel, especifique el **/j** opción del compilador.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md)