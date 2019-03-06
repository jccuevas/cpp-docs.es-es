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
ms.openlocfilehash: 170adfe54b34d14f84b54c717bc9f75fe0b7ab37
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57418482"
---
# <a name="exp-files-as-linker-input"></a>Archivos .Exp como entrada del vinculador

Archivos de exportación (.exp) contienen información sobre los elementos de las funciones y los datos exportados. Cuando LIB crea una biblioteca de importación, también crea un archivo .exp. Use el archivo .exp cuando vincule un programa que tanto de exportación e importación desde otro programa, directa o indirectamente. Si crea un vínculo con un archivo .exp, LINK no produce una biblioteca de importación, ya que supone que LIB ya ha creado uno. Para obtener más información acerca de los archivos .exp y las bibliotecas de importación, consulte [trabajar con bibliotecas de importación y exportación de archivos](../../build/reference/working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Vea también

[Archivos de entrada de LINK](../../build/reference/link-input-files.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)
