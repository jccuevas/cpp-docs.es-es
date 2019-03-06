---
title: /STUB (Nombre del archivo de código auxiliar de MS-DOS)
ms.date: 11/04/2016
f1_keywords:
- /stub
- VC.Project.VCLinkerTool.DosStub
helpviewer_keywords:
- Win32 [C++], attaching MS-DOS stub program
- STUB linker option
- MS-DOS stub file name linker option
- /STUB linker option
- Windows API [C++], attaching MS-DOS stub program
- -STUB linker option
ms.assetid: 65221ffe-4f9a-4a14-ac69-3cfb79b40b5f
ms.openlocfilehash: d349151654d9699bcf00aa3848798acb5104ba53
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421550"
---
# <a name="stub-ms-dos-stub-file-name"></a>/STUB (Nombre del archivo de código auxiliar de MS-DOS)

```
/STUB:filename
```

## <a name="arguments"></a>Argumentos

*filename*<br/>
Una aplicación de MS-DOS.

## <a name="remarks"></a>Comentarios

La opción /STUB asocia un programa de código auxiliar de MS-DOS a un programa Win32.

Un programa de código auxiliar se invoca si se ejecuta el archivo en MS-DOS. Normalmente se muestra un mensaje adecuado. Sin embargo, cualquier aplicación MS-DOS válido puede ser un programa de código auxiliar.

Especifique un *filename* el programa de código auxiliar después de dos puntos (:) en la línea de comandos. Las comprobaciones del vinculador *filename* y emite un mensaje de error si el archivo no es un archivo ejecutable. El programa debe ser un archivo .exe; un archivo .com no es válido para un programa de código auxiliar.

Si no se utiliza esta opción, el vinculador asocia un programa de código auxiliar predeterminado que emite el mensaje siguiente:

```
This program cannot be run in MS-DOS mode.
```

Al generar un controlador de dispositivo virtual, *filename* permite al usuario especificar un nombre de archivo que contiene una estructura IMAGE_DOS_HEADER (definida en WINNT. (H) que se usará en el VXD, en lugar del encabezado predeterminado.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en la página de propiedades **Línea de comandos** .

1. Escriba la opción en el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
