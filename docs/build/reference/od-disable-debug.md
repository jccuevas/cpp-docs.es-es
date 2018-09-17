---
title: -Od (deshabilitar (depurar)) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /od
dev_langs:
- C++
helpviewer_keywords:
- no optimizations
- fast compiling
- /Od compiler option [C++]
- disable optimizations
- Od compiler option [C++]
- -Od compiler option [C++]
- disable (debug) compiler option [C++]
ms.assetid: b1ac31b7-e086-4eeb-be5e-488f7513f5f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adfa2e2feaf44f5f29c1a16b8e68642e438095fe
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703331"
---
# <a name="od-disable-debug"></a>/Od (Deshabilitar (Depurar))

Desactiva todas las optimizaciones en el programa y acelera la compilación.

## <a name="syntax"></a>Sintaxis

```
/Od
```

## <a name="remarks"></a>Comentarios

Esta opción es el valor predeterminado. Dado que **/Od** suprime el movimiento del código, simplifica el proceso de depuración. Para obtener más información acerca de las opciones del compilador para la depuración, vea [/Z7, / Zi, /ZI (formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **optimización** página de propiedades.

1. Modificar el **optimización** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Vea también

[Opciones /O (optimizar código)](../../build/reference/o-options-optimize-code.md)
[opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/Z7, /Zi, /ZI (Formato de la información de depuración)](../../build/reference/z7-zi-zi-debug-information-format.md)