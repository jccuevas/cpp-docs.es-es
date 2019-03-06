---
title: /Qimprecise_fwaits (Quitar comandos fwait en los bloques Try)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 3f2a0e6bc28fb812e087a689716be6119640ffca
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422148"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Quitar comandos fwait en los bloques Try)

Quita el `fwait` comandos internos de `try` bloquea cuando se use la [/fp: excepto](../../build/reference/fp-specify-floating-point-behavior.md) opción del compilador.

## <a name="syntax"></a>Sintaxis

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Comentarios

Esta opción no tiene ningún efecto si **/fp: excepto** también no se especifica. Si especifica la **/fp: excepto** opción, el compilador insertará un `fwait` comando alrededor de cada línea de código en un `try` bloque. De este modo, el compilador puede identificar la línea de código que genera una excepción específica. **/ Qimprecise_fwaits** quita interno `fwait` instrucciones, dejando solo las esperas en torno a la `try` bloque. Esto mejora el rendimiento, pero el compilador sólo podrá indicar qué `try` bloque produce una excepción, no la línea.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
