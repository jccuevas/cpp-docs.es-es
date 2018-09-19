---
title: -GR (habilitar la información de tipo en tiempo de ejecución) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
dev_langs:
- C++
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24ef844c716d64e609440d41bf55db20308c02f1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712249"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Habilitar la información de tipo en tiempo de ejecución)

Agrega código para comprobar los tipos de objeto en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
/GR[-]
```

## <a name="remarks"></a>Comentarios

Cuando **/GR** está activado, el compilador define el `_CPPRTTI` macro de preprocesador. De forma predeterminada, **/GR** está activado. **/GR-** deshabilita la información de tipo en tiempo de ejecución.

Use **/GR** si el compilador no puede resolver estáticamente un tipo de objeto en el código. Normalmente es necesario el **/GR** cuando el código utiliza la opción [dynamic_cast (operador)](../../cpp/dynamic-cast-operator.md) o [typeid](../../cpp/typeid-operator.md). Sin embargo, **/GR** aumenta el tamaño de las secciones .rdata de su imagen. Si no usa el código **dynamic_cast** o **typeid**, **/GR-** puede producir una imagen más pequeña.

Para obtener más información acerca de la comprobación de tipos en tiempo de ejecución, consulte [información de tipo de tiempo de ejecución](../../cpp/run-time-type-information.md) en el *referencia del lenguaje C++*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **lenguaje** página de propiedades.

1. Modificar el **habilitar información de tipo de tiempo de ejecución** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)