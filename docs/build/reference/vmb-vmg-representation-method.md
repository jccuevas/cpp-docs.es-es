---
title: / vmb, - vmg (método de representación)
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
ms.openlocfilehash: 30d15105b9fe502e89f77b19e530d6cc762975a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505500"
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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)