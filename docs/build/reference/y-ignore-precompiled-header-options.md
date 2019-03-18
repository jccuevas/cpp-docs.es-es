---
title: /Y- (Omitir opciones de encabezado precompilado)
ms.date: 11/04/2016
f1_keywords:
- /y-
helpviewer_keywords:
- Y- compiler option [C++]
- -Y- compiler option [C++]
- /Y- compiler option [C++]
ms.assetid: cfaecb36-58db-46b8-b04d-cca6072b1b7a
ms.openlocfilehash: c56c25d587d84e599718d2e1a74d469def3501f7
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812361"
---
# <a name="y--ignore-precompiled-header-options"></a>/Y- (Omitir opciones de encabezado precompilado)

Hace que todos los demás `/Y` compilador va a omitir las opciones (y no se puede reemplazar).

## <a name="syntax"></a>Sintaxis

```
/Y-
```

## <a name="remarks"></a>Comentarios

Para obtener más información sobre los encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](y-precompiled-headers.md)

- [Archivos de encabezado precompilados](../creating-precompiled-header-files.md)

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
