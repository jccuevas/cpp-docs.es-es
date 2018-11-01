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
ms.openlocfilehash: 485a6a479f4d0d6c9e5eb745eda894a01f356e8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50448937"
---
# <a name="ge-enable-stack-probes"></a>/Ge (Habilitar comprobaciones de la pila)

Activa las comprobaciones de pila para cada llamada de función que requiere el almacenamiento para las variables locales.

## <a name="syntax"></a>Sintaxis

```
/Ge
```

## <a name="remarks"></a>Comentarios

Este mecanismo es útil para volver a escribir la funcionalidad de la comprobación de la pila. Se recomienda que utilice [/Gh (habilitar _penter la función de enlace)](../../build/reference/gh-enable-penter-hook-function.md) en lugar de volver a escribir la comprobación de la pila.

[/GS (llamadas de comprobación de pila de control)](../../build/reference/gs-control-stack-checking-calls.md) tiene el mismo efecto.

**/GE** está desusado; a partir de Visual Studio 2005, el compilador genera automáticamente la comprobación de pila. Para obtener una lista de opciones del compilador en desuso, consulte **en desuso y opciones del compilador quitó** en [Compiler Options Listed por categoría](../../build/reference/compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)