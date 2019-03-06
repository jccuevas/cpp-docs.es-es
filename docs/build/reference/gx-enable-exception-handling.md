---
title: /GX (Habilitar el control de excepciones)
ms.date: 11/04/2016
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 4ac2b86c19845a092c743c484ad48d0cd0b6fb35
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416038"
---
# <a name="gx-enable-exception-handling"></a>/GX (Habilitar el control de excepciones)

Desusado. Habilita control sincrónico de excepciones mediante la suposición de que las funciones declarada mediante `extern "C"` nunca producen una excepción.

## <a name="syntax"></a>Sintaxis

```
/GX
```

## <a name="remarks"></a>Comentarios

**/GX** está en desuso. Use el equivalente [/EHsc](../../build/reference/eh-exception-handling-model.md) opción en su lugar. Para obtener una lista de opciones del compilador en desuso, vea el **en desuso y opciones del compilador quitó** sección [Compiler Options Listed por categoría](../../build/reference/compiler-options-listed-by-category.md).

De forma predeterminada, **/EHsc**, el equivalente de **/GX**, está en vigor cuando se compila utilizando el entorno de desarrollo de Visual Studio. Al usar las herramientas de línea de comandos, no se especifica ningún controlador de excepciones. Este es el equivalente de **/GX-**.

Para obtener más información, consulte [control de excepciones de C++](../../cpp/cpp-exception-handling.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. En el panel de navegación, elija **propiedades de configuración**, **C o C++**, **línea de comandos**.

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/EH (Modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md)
