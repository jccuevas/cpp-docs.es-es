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
ms.openlocfilehash: 8de7de7a4164916b9662e3a78fe00dd0a40cecc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542910"
---
# <a name="y--ignore-precompiled-header-options"></a>/Y- (Omitir opciones de encabezado precompilado)

Hace que todos los demás `/Y` compilador va a omitir las opciones (y no se puede reemplazar).

## <a name="syntax"></a>Sintaxis

```
/Y-
```

## <a name="remarks"></a>Comentarios

Para obtener más información sobre los encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](../../build/reference/y-precompiled-headers.md)

- [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)

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