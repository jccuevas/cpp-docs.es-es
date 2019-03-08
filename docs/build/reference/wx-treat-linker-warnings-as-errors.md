---
title: /WX (Tratar advertencias del vinculador como errores)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: fa7b651d2a884e25a9b0e6f1ba824d082c3c01bc
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412654"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Tratar advertencias del vinculador como errores)

```
/WX[:NO]
```

## <a name="remarks"></a>Comentarios

/WX hace que ningún archivo de salida si el vinculador genera una advertencia.

Esto es similar a **/WX** para el compilador (consulte [/w, / W0, / W1, / W2, / w3, / W4, / W1, / W2, / w3, / W4, / Wall, / WD, / we, / WO, / wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md) para obtener más información). Sin embargo, la especificación **/WX** para la compilación no implica que **/WX** también estará en vigor para la fase de vinculación; debe especificar explícitamente **/WX** para cada herramienta.

De forma predeterminada, **/WX** no está en vigor. Para tratar las advertencias del vinculador como errores, especifique **/WX**. **/WX:no** es el mismo que si no se especifica **/WX**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
