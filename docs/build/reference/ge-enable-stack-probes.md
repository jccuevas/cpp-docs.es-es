---
title: /Ge (Habilitar comprobaciones de la pila)
ms.date: 11/04/2016
f1_keywords:
- /ge
helpviewer_keywords:
- -Ge compiler option [C++]
- enable stack probes
- /Ge compiler option [C++]
- stack, stack probes
- stack probes
- stack checking calls
- Ge compiler option [C++]
ms.assetid: 4b54deae-4e3c-4bfa-95f3-ba23590f7258
ms.openlocfilehash: a785ec041370e0bcbb2ce8b698bfba89235a0a0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292190"
---
# <a name="ge-enable-stack-probes"></a>/Ge (Habilitar comprobaciones de la pila)

Activa las comprobaciones de pila para cada llamada de función que requiere el almacenamiento para las variables locales.

## <a name="syntax"></a>Sintaxis

```
/Ge
```

## <a name="remarks"></a>Comentarios

Este mecanismo es útil para volver a escribir la funcionalidad de la comprobación de la pila. Se recomienda que utilice [/Gh (habilitar _penter la función de enlace)](gh-enable-penter-hook-function.md) en lugar de volver a escribir la comprobación de la pila.

[/GS (llamadas de comprobación de pila de control)](gs-control-stack-checking-calls.md) tiene el mismo efecto.

**/GE** está desusado; a partir de Visual Studio 2005, el compilador genera automáticamente la comprobación de pila. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](compiler-options-listed-by-category.md).

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
