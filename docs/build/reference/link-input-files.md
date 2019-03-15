---
title: Archivos de entrada de LINK
ms.date: 11/04/2016
f1_keywords:
- link
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
ms.openlocfilehash: 48ad9423ae35c22a97a873fe6a2a0479c12ab33b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817795"
---
# <a name="link-input-files"></a>Archivos de entrada de LINK

Proporcione al enlazador con archivos que contienen objetos, importar y bibliotecas estándar, los recursos, las definiciones de módulo y entradas de comandos. VÍNCULO no usa extensiones de archivo para realizar suposiciones sobre el contenido de un archivo. En su lugar, el vínculo examina cada archivo de entrada para determinar qué tipo de archivo es.

Archivos de objeto en la línea de comandos se procesan en el orden en que aparecen en la línea de comandos. Las bibliotecas se buscan en orden de la línea de comandos, con la advertencia siguiente: Los símbolos que están sin resolver al reunir en un archivo de objeto de una biblioteca se buscan en esa biblioteca en primer lugar y, a continuación, en las siguientes bibliotecas desde la línea de comandos y [DEFAULTLIB (especificar la biblioteca predeterminada)](defaultlib-specify-default-library.md) directivas y, a continuación, a las bibliotecas al principio de la línea de comandos.

> [!NOTE]
>  VÍNCULO ya no acepta un punto y coma (o cualquier otro carácter) como el inicio de un comentario en los archivos de respuesta y los archivos de pedido. Punto y coma se reconoce solo como el inicio de los comentarios en los archivos de definición de módulo (.def).

VÍNCULO utiliza los siguientes tipos de archivos de entrada:

- [archivos .obj](dot-obj-files-as-linker-input.md)

- [.netmodule files](netmodule-files-as-linker-input.md)

- [archivos .lib](dot-lib-files-as-linker-input.md)

- [archivos .exp](dot-exp-files-as-linker-input.md)

- [archivos .def](dot-def-files-as-linker-input.md)

- [.pdb files](dot-pdb-files-as-linker-input.md)

- [archivos .res](dot-res-files-as-linker-input.md)

- [archivos .exe](dot-exe-files-as-linker-input.md)

- [archivos .txt](dot-txt-files-as-linker-input.md)

- [.ilk (archivos)](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
