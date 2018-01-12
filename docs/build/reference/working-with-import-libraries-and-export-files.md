---
title: "Trabajar con bibliotecas de importación y exportación de archivos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e0d60eed00abc60c09e03838a113c424d8f173a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-import-libraries-and-export-files"></a>Trabajar con bibliotecas de importación y archivos de exportación
Puede utilizar LIB con la opción/DEF para crear una biblioteca de importación y un archivo de exportación. LINK usa la exportación de archivos para compilar un programa que contiene exportaciones (normalmente una biblioteca de vínculos dinámicos (DLL)) y utiliza la biblioteca de importación para resolver referencias a dichas exportaciones en otros programas.  
  
 Tenga en cuenta que si crea la biblioteca de importación en un paso preliminar, antes de crear el archivo .dll, debe pasar el mismo conjunto de archivos de objeto al crear el archivo .dll, tal y como se haya pasado al crear la biblioteca de importación.  
  
 En la mayoría de los casos, no es necesario utilizar LIB para crear la biblioteca de importación. Al vincular un programa (un archivo ejecutable o un archivo DLL) que contiene exportaciones, LINK crea automáticamente una biblioteca de importación que describe las exportaciones. Más adelante, cuando se vincula un programa que hace referencia a las exportaciones, especifique la biblioteca de importación.  
  
 Sin embargo, cuando un archivo DLL exporta a un programa que también se importa desde, si directa o indirectamente, deberá utilizar LIB para crear una de las bibliotecas de importación. Cuando LIB crea una biblioteca de importación, también crea un archivo de exportación. Debe usar el archivo de exportación al vincular uno de los archivos DLL.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de LIB](../../build/reference/lib-reference.md)