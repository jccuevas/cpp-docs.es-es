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
ms.openlocfilehash: a5aaf162a16b6989ac1abbcb6a574af1c31b543a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50550558"
---
# <a name="link-input-files"></a>Archivos de entrada de LINK

Proporcione al enlazador con archivos que contienen objetos, importar y bibliotecas estándar, los recursos, las definiciones de módulo y entradas de comandos. VÍNCULO no usa extensiones de archivo para realizar suposiciones sobre el contenido de un archivo. En su lugar, el vínculo examina cada archivo de entrada para determinar qué tipo de archivo es.

Archivos de objeto en la línea de comandos se procesan en el orden en que aparecen en la línea de comandos. Las bibliotecas se buscan en orden de la línea de comandos, con la siguiente advertencia: los símbolos que están sin resolver al reunir en un archivo de objeto de una biblioteca se buscan en esa biblioteca en primer lugar y, a continuación, en las siguientes bibliotecas desde la línea de comandos y [DEFAULTLIB (especificar la biblioteca predeterminada)](../../build/reference/defaultlib-specify-default-library.md) directivas y, a continuación, a las bibliotecas al principio de la línea de comandos.

> [!NOTE]
>  VÍNCULO ya no acepta un punto y coma (o cualquier otro carácter) como el inicio de un comentario en los archivos de respuesta y los archivos de pedido. Punto y coma se reconoce solo como el inicio de los comentarios en los archivos de definición de módulo (.def).

VÍNCULO utiliza los siguientes tipos de archivos de entrada:

- [archivos .obj](../../build/reference/dot-obj-files-as-linker-input.md)

- [archivos .netmodule](../../build/reference/netmodule-files-as-linker-input.md)

- [archivos .lib](../../build/reference/dot-lib-files-as-linker-input.md)

- [archivos .exp](../../build/reference/dot-exp-files-as-linker-input.md)

- [archivos .def](../../build/reference/dot-def-files-as-linker-input.md)

- [archivos .pdb](../../build/reference/dot-pdb-files-as-linker-input.md)

- [archivos .res](../../build/reference/dot-res-files-as-linker-input.md)

- [archivos .exe](../../build/reference/dot-exe-files-as-linker-input.md)

- [archivos .txt](../../build/reference/dot-txt-files-as-linker-input.md)

- [.ilk (archivos)](../../build/reference/dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)