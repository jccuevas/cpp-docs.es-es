---
title: Archivos de entrada de LINK
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: 25d8e20903a97186e2c32a079fd74ece3626b7fa
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439343"
---
# <a name="link-input-files"></a>Archivos de entrada de LINK

Proporcione al enlazador archivos que contengan objetos, bibliotecas de importación y estándar, recursos, definiciones de módulo y entradas de comandos. LINK no utiliza las extensiones de archivo para hacer suposiciones sobre el contenido de un archivo. En su lugar, LINK examina cada archivo de entrada para determinar qué tipo de archivo es.

Los archivos objeto de la línea de comandos se procesan en el orden en que aparecen en la línea de comandos. Las bibliotecas se buscan también en el orden de la línea de comandos, con la siguiente salvedad: los símbolos que no se resuelven al traer un archivo objeto de una biblioteca se buscan primero en esa biblioteca, después en las siguientes bibliotecas desde la línea de comandos y las directivas [/DEFAULTLIB (especificar biblioteca predeterminada)](defaultlib-specify-default-library.md) y, a continuación, a las bibliotecas que se encuentran al principio de la línea de comandos.

> [!NOTE]
>  LINK ya no acepta un punto y coma (o cualquier otro carácter) como inicio de un Comentario en archivos de respuesta y archivos de orden. Los signos de punto y coma solo se reconocen como el inicio de los comentarios en los archivos de definición de módulo (. def).

LINK usa los siguientes tipos de archivos de entrada:

- [. obj (archivos)](dot-obj-files-as-linker-input.md)

- [. netmodule (archivos)](netmodule-files-as-linker-input.md)

- [. lib (archivos)](dot-lib-files-as-linker-input.md)

- [. exp (archivos)](dot-exp-files-as-linker-input.md)

- [. def (archivos)](dot-def-files-as-linker-input.md)

- [. pdb (archivos)](dot-pdb-files-as-linker-input.md)

- [. res (archivos)](dot-res-files-as-linker-input.md)

- [archivos. exe](dot-exe-files-as-linker-input.md)

- [. txt (archivos)](dot-txt-files-as-linker-input.md)

- [. İlk (archivos)](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
