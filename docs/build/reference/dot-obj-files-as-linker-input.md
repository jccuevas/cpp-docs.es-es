---
title: Archivos .obj como entrada del vinculador
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 36f41077fcba6b093865625d426b8009f6185e7b
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450582"
---
# <a name="obj-files-as-linker-input"></a>Archivos .obj como entrada del vinculador

La herramienta del vinculador (vínculo). (EXE) acepta archivos .obj que están en formato de archivo de objeto común (COFF).

## <a name="remarks"></a>Comentarios

Microsoft proporciona una descripción completa de formato common object file format. Para obtener más información, consulte [formato PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Compatibilidad con Unicode

A partir de Visual Studio 2005, el compilador de MSVC de Microsoft admite caracteres Unicode en identificadores como se define por los estándares de C++ y C ISO/IEC. Las versiones anteriores del compilador admiten únicamente caracteres ASCII en los identificadores. Para admitir Unicode en los nombres de funciones, clases y variables estáticas, el compilador y vinculador utilizan la codificación Unicode UTF-8 para los símbolos COFF en los archivos .obj. La codificación UTF-8 es ser compatible con la codificación ASCII utilizados por las versiones anteriores de Visual Studio.

Para obtener más información sobre el compilador y vinculador, vea [compatibilidad con Unicode en el compilador y vinculador](unicode-support-in-the-compiler-and-linker.md). Para obtener más información sobre el estándar Unicode, vea el [Unicode](https://www.unicode.org/) organización.

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](link-input-files.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[Compatibilidad con Unicode](../../text/support-for-unicode.md)<br/>
[Compatibilidad con Unicode en el compilador y el vinculador](unicode-support-in-the-compiler-and-linker.md)<br/>
[Estándar Unicode](https://www.unicode.org/)<br/>
[Formato PE](/windows/desktop/Debug/pe-format)
