---
title: . Archivos obj como entrada del vinculador | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ffbc1d7fc7f74121c37c9e80a538ec60f2265701
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219567"
---
# <a name="obj-files-as-linker-input"></a>Archivos .obj como entrada del vinculador

La herramienta del vinculador (vínculo). (EXE) acepta archivos .obj que están en formato de archivo de objeto común (COFF).

## <a name="remarks"></a>Comentarios

Microsoft proporciona una descripción completa de formato common object file format. Para obtener más información, consulte [formato PE](/windows/desktop/Debug/pe-format).

## <a name="unicode-support"></a>Compatibilidad con Unicode

A partir de Visual Studio 2005, el compilador de Microsoft Visual C++ admite caracteres Unicode en identificadores como se define por los estándares de C++ y C ISO/IEC. Las versiones anteriores del compilador admiten únicamente caracteres ASCII en los identificadores. Para admitir Unicode en los nombres de funciones, clases y variables estáticas, el compilador y vinculador utilizan la codificación Unicode UTF-8 para los símbolos COFF en los archivos .obj. La codificación UTF-8 es ser compatible con la codificación ASCII utilizados por las versiones anteriores de Visual Studio.

Para obtener más información sobre el compilador y vinculador, vea [compatibilidad con Unicode en el compilador y vinculador](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Para obtener más información sobre el estándar Unicode, vea el [Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123) organización.

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](../../build/reference/link-input-files.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
[Compatibilidad con Unicode](../../text/support-for-unicode.md)  
[Compatibilidad con Unicode en el compilador y el vinculador](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Estándar Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[Formato PE](/windows/desktop/Debug/pe-format)  
