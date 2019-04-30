---
title: Archivos .Exp como entrada del vinculador
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
ms.openlocfilehash: 0f2f5c22752d6d938700228fc208c21b8f32cc7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293672"
---
# <a name="exp-files-as-linker-input"></a>Archivos .Exp como entrada del vinculador

Archivos de exportación (.exp) contienen información sobre los elementos de las funciones y los datos exportados. Cuando LIB crea una biblioteca de importación, también crea un archivo .exp. Use el archivo .exp cuando vincule un programa que tanto de exportación e importación desde otro programa, directa o indirectamente. Si crea un vínculo con un archivo .exp, LINK no produce una biblioteca de importación, ya que supone que LIB ya ha creado uno. Para obtener más información acerca de los archivos .exp y las bibliotecas de importación, consulte [trabajar con bibliotecas de importación y exportación de archivos](working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](link-input-files.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
