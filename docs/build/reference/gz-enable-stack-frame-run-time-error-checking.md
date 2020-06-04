---
title: /GZ (Habilitar comprobación de errores del marco de pila en tiempo de ejecución)
ms.date: 11/04/2016
f1_keywords:
- /gz
helpviewer_keywords:
- -GZ compiler option [C++]
- release-build errors
- /GZ compiler option [C++]
- GZ compiler option [C++]
- debug builds, catch release-build errors
ms.assetid: b3efeeff-d5e3-4057-91c9-f6fc73d0270c
ms.openlocfilehash: 3e6ffce487cc8183e45f3a911e7060ea22b28216
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292064"
---
# <a name="gz-enable-stack-frame-run-time-error-checking"></a>/GZ (Habilitar comprobación de errores del marco de pila en tiempo de ejecución)

Realiza las mismas operaciones que el [/RTC (comprobaciones de errores de tiempo de ejecución)](rtc-run-time-error-checks.md) opción. Desusado.

## <a name="syntax"></a>Sintaxis

```
/GZ
```

## <a name="remarks"></a>Comentarios

**/GZ** es sólo para su uso en una generación ([/Od (deshabilitar (depurar))](od-disable-debug.md)) de compilación.

**/GZ** está en desuso desde Visual Studio 2005; use [/RTC (comprobaciones de errores de tiempo de ejecución)](rtc-run-time-error-checks.md) en su lugar. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
