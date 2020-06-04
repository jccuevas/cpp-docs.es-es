---
title: Compatibilidad con Unicode en el compilador y el vinculador
ms.date: 12/15/2017
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
helpviewer_keywords:
- Unicode, Visual C++
ms.openlocfilehash: 420b01263320cf86df3f99da4523cc2b8bb4d4b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168842"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Compatibilidad con Unicode en el compilador y el vinculador

La mayoría C++ de las herramientas de compilación visual admiten entradas y salidas Unicode.

## <a name="filenames"></a>Nombres de archivo

Los nombres de archivo especificados en la línea de comandos o en las directivas de compilador (como `#include`) pueden contener caracteres Unicode.

## <a name="source-code-files"></a>Archivos de código fuente

Los caracteres Unicode se admiten en los identificadores, macros, literales de cadena y caracteres, y en los comentarios.  También se admiten nombres de carácter universal.

Unicode se puede escribir en un archivo de código fuente en las siguientes codificaciones:

- UTF-16 little endian con o sin marca de orden de bytes (BOM)

- UTF-16 big endian con o sin BOM

- UTF-8 with BOM

## <a name="output"></a>Output

Durante la compilación, el compilador genera diagnósticos en la consola en UTF-16.  Los caracteres que se pueden mostrar en la consola dependen de las propiedades de la ventana de la consola.  La salida del compilador redirigida a un archivo está en la página de códigos de la consola ANSI actual.

## <a name="linker-response-files-and-def-files"></a>Archivos de respuesta del vinculador y. DEF (archivos)

Los archivos de respuesta y los archivos DEF pueden ser UTF-16 con una marca BOM o ANSI.

## <a name="asm-and-cod-dumps"></a>volcados de memoria. asm y. COD

los volcados de memoria. asm y. COD están en ANSI de forma predeterminada por compatibilidad con MASM. Use [/FAu](fa-fa-listing-file.md) para generar UTF-8. Tenga en cuenta que si especifica **/FAS**, el origen entremezclado se imprimirá directamente y puede parecer ilegible, por ejemplo, si el código fuente es UTF-8 y no especificó **/FAsu**.

## <a name="see-also"></a>Consulte también

[Uso del conjunto de herramientas MSVC desde la línea de comandos](../building-on-the-command-line.md)
