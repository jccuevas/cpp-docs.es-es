---
title: . EXP (archivos) como entrada del vinculador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9b5c118e81372bd57810a9472526909ed21f765
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="exp-files-as-linker-input"></a>Archivos .Exp como entrada del vinculador
Archivos de exportación (.exp) contienen información sobre los elementos de las funciones y los datos exportados. Cuando LIB crea una biblioteca de importación, también crea un archivo .exp. Utilice el archivo .exp al vincular un programa que tanto de exportación e importación desde otro programa, directa o indirectamente. Si crea un vínculo con un archivo .exp, LINK no produce una biblioteca de importación, porque se supone que LIB ya ha creado uno. Para obtener más información acerca de los archivos .exp y las bibliotecas de importación, consulte [trabajar con bibliotecas de importación y archivos de exportación](../../build/reference/working-with-import-libraries-and-export-files.md).  
  
## <a name="see-also"></a>Vea también  
 [Archivos de entrada de vínculo](../../build/reference/link-input-files.md)   
 [Opciones del vinculador](../../build/reference/linker-options.md)