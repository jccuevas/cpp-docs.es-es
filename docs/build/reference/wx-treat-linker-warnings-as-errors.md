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
ms.openlocfilehash: b4b29ed364d39c5f105dded703b8530c08db35e6
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57822098"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Tratar advertencias del vinculador como errores)

```
/WX[:NO]
```

## <a name="remarks"></a>Comentarios

/WX hace que ningún archivo de salida si el vinculador genera una advertencia.

Esto es similar a **/WX** para el compilador (consulte [/w, / W0, / W1, / W2, / w3, / W4, / W1, / W2, / w3, / W4, / Wall, / WD, / we, / WO, / wv, /WX (nivel de advertencia)](compiler-option-warning-level.md) para obtener más información). Sin embargo, la especificación **/WX** para la compilación no implica que **/WX** también estará en vigor para la fase de vinculación; debe especificar explícitamente **/WX** para cada herramienta.

De forma predeterminada, **/WX** no está en vigor. Para tratar las advertencias del vinculador como errores, especifique **/WX**. **/WX:no** es el mismo que si no se especifica **/WX**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
