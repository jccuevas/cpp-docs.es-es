---
title: . Archivos obj como entrada del vinculador | Documentos de Microsoft
ms.custom: 
ms.date: 12/29/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9a2896822e97bdbb5ffdf8f869e67beadc1675b7
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="obj-files-as-linker-input"></a>Archivos .obj como entrada del vinculador

La herramienta del vinculador (LINK. (EXE) acepta archivos .obj que están en formato de archivo de objeto común (COFF).

## <a name="remarks"></a>Comentarios

Microsoft proporciona una descripción completa del formato common object file format. Para obtener más información, consulte [formato PE](https://msdn.microsoft.com/library/windows/desktop/ms680547).

## <a name="unicode-support"></a>Compatibilidad con Unicode

A partir de Visual Studio 2005, el compilador de Microsoft Visual C++ admite caracteres Unicode en los identificadores de acuerdo con los estándares de C++ y C ISO/IEC. Las versiones anteriores del compilador admiten únicamente caracteres ASCII en identificadores. Para admitir Unicode en los nombres de funciones, clases y datos estáticos, el compilador y el vinculador utilizan la codificación Unicode UTF-8 para los símbolos COFF en los archivos .obj. La codificación UTF-8 es ser compatible con la codificación ASCII usada en las versiones anteriores de Visual Studio.

Para obtener más información sobre el compilador y el vinculador, vea [compatibilidad con Unicode en el compilador y el vinculador](../../build/reference/unicode-support-in-the-compiler-and-linker.md). Para obtener más información sobre el estándar Unicode, vea el [Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123) organización.

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](../../build/reference/link-input-files.md)  
[Opciones del vinculador](../../build/reference/linker-options.md)  
[Compatibilidad con Unicode](../../text/support-for-unicode.md)  
[Compatibilidad con Unicode en el compilador y el vinculador](../../build/reference/unicode-support-in-the-compiler-and-linker.md)  
[Estándar Unicode](http://go.microsoft.com/fwlink/p/?linkid=37123)  
[Formato PE](https://msdn.microsoft.com/library/windows/desktop/ms680547)  
