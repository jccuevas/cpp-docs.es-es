---
title: /GR (Habilitar la información de tipo en tiempo de ejecución)
ms.date: 11/04/2016
f1_keywords:
- /gr
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: 15ad453b10fd31de97bbc25f8062e628129076f5
ms.sourcegitcommit: faa42c8a051e746d99dcebe70fd4bbaf3b023ace
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2019
ms.locfileid: "57820635"
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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **lenguaje** página de propiedades.

1. Modificar el **habilitar información de tipo de tiempo de ejecución** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
