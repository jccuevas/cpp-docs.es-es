---
title: /vmb, /vmg (Método de representación)
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: 25d24d7f92537f16e36213b8a8fd7b945fda7f5a
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504306"
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (Método de representación)

Seleccione el método que el compilador usa para representar los punteros a miembros de clase.

Use **/vmb** si siempre se define una clase antes de declarar un puntero a un miembro de la clase.

Use **/vmg** para declarar un puntero a un miembro de una clase antes de definir la clase. Esto puede ser necesario si define los miembros de dos clases diferentes que hacen referencia entre sí. Para estas clases de referencia mutuamente, una clase debe hacer referencia antes de definirla.

## <a name="syntax"></a>Sintaxis

```
/vmb
/vmg
```

## <a name="remarks"></a>Comentarios

También puede usar [pointers_to_members](../../preprocessor/pointers-to-members.md) o [palabras clave de herencia](../../cpp/inheritance-keywords.md) en el código para especificar una representación de puntero.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
