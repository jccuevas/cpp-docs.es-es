---
title: /GR (Habilitar la información de tipo en tiempo de ejecución)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: ee1398b2f9ee78c62fb84aa591e77708cd0d9d83
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439588"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Habilitar la información de tipo en tiempo de ejecución)

Agrega código para comprobar los tipos de objeto en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
/GR[-]
```

## <a name="remarks"></a>Observaciones

Cuando **/gr** está activada, el compilador define la macro de preprocesador `_CPPRTTI`. De forma predeterminada, **/gr** está activada. **/Gr-** deshabilita la información de tipo en tiempo de ejecución.

Use **/gr** si el compilador no puede resolver estáticamente un tipo de objeto en el código. Normalmente, se necesita la opción **/gr** cuando el código usa [dynamic_cast operador](../../cpp/dynamic-cast-operator.md) o [typeid](../../cpp/typeid-operator.md). Sin embargo, **/gr** aumenta el tamaño de las secciones. rdata de la imagen. Si el código no usa **dynamic_cast** o **typeid**, **/gr-** puede generar una imagen más pequeña.

Para obtener más información sobre la comprobación de tipos en tiempo de ejecución, vea [información de tipo en tiempo de ejecución](../../cpp/run-time-type-information.md) en la referencia del  *C++ lenguaje*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **idioma** .

1. Modifique la propiedad **habilitar información de tipo en tiempo de ejecución** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
