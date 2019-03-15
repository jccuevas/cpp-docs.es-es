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
ms.openlocfilehash: 71458ab345670c0a5715576a7da80c4e6ff2955b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807534"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Compatibilidad con Unicode en el compilador y el vinculador

Mayoría de las herramientas de compilación de Visual C++ admite Unicode entradas y salidas.

## <a name="filenames"></a>Nombres de archivo

Los nombres de archivo especificado en la línea de comandos o en las directivas de compilador (como `#include`) puede contener caracteres Unicode.

## <a name="source-code-files"></a>Archivos de código fuente

Se admiten caracteres Unicode en identificadores, macros, literales de cadena y carácter y en los comentarios.  También se admiten nombres de carácter universal.

Unicode se puede especificar en un archivo de código fuente con las codificaciones siguientes:

- UTF-16 little endian con o sin marca de orden de bytes (BOM)

- UTF-16 big endian con o sin marca BOM

- UTF-8 con BOM

## <a name="output"></a>Salida

Durante la compilación, el compilador genera diagnósticos en la consola en UTF-16.  Los caracteres que se pueden mostrar en la consola dependen de las propiedades de la ventana de consola.  Resultados del compilador redirigidos a un archivo está en la página de códigos de consola actual de ANSI.

## <a name="linker-response-files-and-def-files"></a>Archivos de respuesta del vinculador y. DEF (archivos)

DEF (archivos) y los archivos de respuesta pueden ser UTF-16 con una marca BOM o ANSI.

## <a name="asm-and-cod-dumps"></a>volcados de memoria .asm y .cod

volcados de memoria .asm y .cod están en ANSI de manera predeterminada para la compatibilidad con MASM. Use [/FAu](fa-fa-listing-file.md) para generar UTF-8. Tenga en cuenta que si especifica **/FAS**, la fuente entremezclada se imprimirá directamente y podrá aparecer confusa, por ejemplo, si el código fuente es UTF-8 y no se especificó **/FAsu**.

## <a name="see-also"></a>Vea también

[Usar el conjunto de herramientas MSVC desde la línea de comandos](../building-on-the-command-line.md)