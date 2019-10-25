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
ms.openlocfilehash: 3e02ccc09ae8c9c2f3df88bc1767ff0188baa1f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492941"
---
# <a name="obj-files-as-linker-input"></a>Archivos .obj como entrada del vinculador

La herramienta del vinculador (LINK. EXE) acepta archivos. obj que se encuentran en formato de archivo de objeto común (COFF).

## <a name="remarks"></a>Comentarios

Microsoft proporciona una descripción completa del formato de archivo de objeto común. Para obtener más información, consulte [formato PE](/windows/win32/Debug/pe-format).

## <a name="unicode-support"></a>Compatibilidad con Unicode

A partir de Visual Studio 2005, el compilador de Microsoft MSVC admite caracteres Unicode en identificadores tal y como se define C++ en los estándares y C ISO/IEC. Las versiones anteriores del compilador solo admitían caracteres ASCII en identificadores. Para admitir Unicode en los nombres de funciones, clases y estáticas, el compilador y el vinculador usan la codificación Unicode UTF-8 para los símbolos COFF en los archivos. obj. La codificación UTF-8 es compatible con la codificación ASCII utilizada en versiones anteriores de Visual Studio.

Para obtener más información sobre el compilador y el vinculador, vea [compatibilidad con Unicode en el compilador y el vinculador](unicode-support-in-the-compiler-and-linker.md). Para obtener más información sobre el estándar Unicode, consulte la organización [Unicode](https://www.unicode.org/) .

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](link-input-files.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[Compatibilidad con Unicode](../../text/support-for-unicode.md)<br/>
[Compatibilidad con Unicode en el compilador y el vinculador](unicode-support-in-the-compiler-and-linker.md)<br/>
[Estándar Unicode](https://www.unicode.org/)<br/>
[Formato PE](/windows/win32/Debug/pe-format)
