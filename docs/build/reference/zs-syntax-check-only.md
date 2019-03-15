---
title: /Zs (Solamente comprobación de sintaxis)
ms.date: 11/04/2016
f1_keywords:
- /zs
helpviewer_keywords:
- -Zs compiler option [C++]
- Syntax Check Only compiler option
- Zs compiler option
- /Zs compiler option [C++]
ms.assetid: b4b41e6a-3f41-4d09-9cb6-fde5aa2cfecf
ms.openlocfilehash: e3713312b71c4cd539d40e09a3eaa821a2e5caed
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822088"
---
# <a name="zs-syntax-check-only"></a>/Zs (Solamente comprobación de sintaxis)

Indica al compilador para comprobar solo la sintaxis de los archivos de origen en la línea de comandos.

## <a name="syntax"></a>Sintaxis

```
/Zs
```

## <a name="remarks"></a>Comentarios

Cuando se usa esta opción, se crea ningún archivo de salida y mensajes de error se escriben en la salida estándar.

El **/Zs** opción proporciona una forma rápida de encontrar y corregir errores de sintaxis antes de compilar y vincular un archivo de origen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
