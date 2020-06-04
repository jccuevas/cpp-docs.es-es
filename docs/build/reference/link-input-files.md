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
ms.openlocfilehash: aec71d4622821618f377953d36a9676e2233eefc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328203"
---
# <a name="link-input-files"></a>Archivos de entrada de LINK

Proporcione al vinculador archivos que contengan objetos, bibliotecas estándar y de importación, recursos, definiciones de módulos y entrada de comandos. LINK no utiliza extensiones de archivo para hacer suposiciones sobre el contenido de un archivo. En su lugar, LINK examina cada archivo de entrada para determinar qué tipo de archivo es.

Los archivos de objeto de la línea de comandos se procesan en el orden en que aparecen en la línea de comandos. Las bibliotecas también se buscan en orden de línea de comandos, con la siguiente advertencia: los símbolos que no se resuelven al incorporar un archivo de objeto de una biblioteca se buscan primero en esa biblioteca y, a continuación, las siguientes bibliotecas de la línea de comandos y las directivas [/DEFAULTLIB (Especificar biblioteca predeterminada)](defaultlib-specify-default-library.md) y, a continuación, a las bibliotecas al principio de la línea de comandos.

> [!NOTE]
> LINK ya no acepta un punto y coma (o cualquier otro carácter) como el inicio de un comentario en los archivos de respuesta y los archivos de pedido. Los puntos y comas solo se reconocen como el inicio de los comentarios en los archivos de definición de módulo (.def).

LINK utiliza los siguientes tipos de archivos de entrada:

- [.obj (archivos)](dot-obj-files-as-linker-input.md)

- [Archivos .netmodule](netmodule-files-as-linker-input.md)

- [.lib (archivos)](dot-lib-files-as-linker-input.md)

- [Archivos .exp](dot-exp-files-as-linker-input.md)

- [Archivos .def](dot-def-files-as-linker-input.md)

- [Archivos .pdb](dot-pdb-files-as-linker-input.md)

- [Archivos .res](dot-res-files-as-linker-input.md)

- [Archivos .exe](dot-exe-files-as-linker-input.md)

- [Archivos .txt](dot-txt-files-as-linker-input.md)

- [Archivos .ilk](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Consulte también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones de MSVC Linker](linker-options.md)
