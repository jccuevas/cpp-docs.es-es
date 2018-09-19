---
title: Compatibilidad con Unicode en el compilador y el vinculador | Documentos de Microsoft
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.UseUnicodeResponseFiles
- VC.Project.VCLibrarianTool.UseUnicodeResponseFiles
- VC.Project.VCCLCompilerTool.UseUnicodeResponseFiles
- VC.Project.VCXDCMakeTool.UseUnicodeResponseFiles
dev_langs:
- C++
helpviewer_keywords:
- Unicode, Visual C++
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec0b84cd62f3fcca378ab55de16006925e685b37
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376197"
---
# <a name="unicode-support-in-the-compiler-and-linker"></a>Compatibilidad con Unicode en el compilador y el vinculador

La mayoría herramientas de compilación de Visual C++ admiten Unicode entradas y salidas.

## <a name="filenames"></a>Nombres de archivo

Los nombres de archivo especificado en la línea de comandos o en las directivas de compilador (como `#include`) puede contener caracteres Unicode.

## <a name="source-code-files"></a>Archivos de código fuente

Se admiten caracteres Unicode en identificadores, macros, literales de cadena y carácter y en comentarios.  También se admiten nombres de carácter universal.

Unicode se puede especificar en un archivo de código fuente en las codificaciones siguientes:

- UTF-16 little endian con o sin marca de orden de bytes (BOM)

- UTF-16 big endian con o sin marca BOM

- UTF-8 con BOM

## <a name="output"></a>Salida

Durante la compilación, el compilador genera diagnósticos en la consola en UTF-16.  Los caracteres que se pueden mostrar en la consola dependen de las propiedades de la ventana de consola.  Resultados del compilador redirigidos a un archivo está en la página de códigos de consola actual de ANSI.

## <a name="linker-response-files-and-def-files"></a>Archivos de respuesta del vinculador y. DEF (archivos)

Archivos de respuesta y DEF (archivos) pueden ser UTF-16 con una lista de materiales o ANSI.

## <a name="asm-and-cod-dumps"></a>ASM y volcados de .cod

ASM y volcados de .cod están en ANSI predeterminada por compatibilidad con MASM. Use [/FAu](../../build/reference/fa-fa-listing-file.md) para generar UTF-8. Tenga en cuenta que si especifica **/FAs**, el origen entremezclados siguiendo solo se imprimirán directamente y puede ser confusa, por ejemplo, si el código fuente es UTF-8 y no se especifica **/FAsu**.

## <a name="see-also"></a>Vea también

[Compilación de código de C o C++ en la línea de comandos](../../build/building-on-the-command-line.md)