---
title: Crear una. SBR truncado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- SBR files
- BSCMAKE, input files
- .sbr files
- source browser files
- local symbols in browse information
- symbols
ms.assetid: bdb4b93c-a88a-441a-84fd-01087d03be25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d87b71daaf5d7b37e67c2c0e56e844bd5251a490
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-sbr-file"></a>Crear un archivo .Sbr
Los archivos de entrada para BSCMAKE son archivos. sbr. El compilador crea un archivo .sbr para cada archivo objeto (.obj) que compila. Al crear o actualizar el archivo de información de examen, todos los archivos .sbr para el proyecto deben estar disponibles en disco.  
  
 Para crear un archivo .sbr con toda la información posible, especifique [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).  
  
 Para crear un archivo .sbr que no contenga símbolos locales, especifique [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Si los archivos .sbr contienen símbolos locales, se puede omitir en el archivo .bsc mediante el uso de BSCMAKE [/ el: opción](../../build/reference/bscmake-options.md)`.`  
  
 Puede crear un archivo .sbr sin realizar una compilación completa. Por ejemplo, puede especificar la opción /Zs al compilador que debe realizar una comprobación de sintaxis y seguir generando un archivo .sbr si se especifica /FR o/el fr.  
  
 El proceso de compilación puede ser más eficaz si los archivos .sbr se empaquetan antes para quitar las definiciones sin referencia. El compilador empaqueta automáticamente los archivos .sbr.  
  
## <a name="see-also"></a>Vea también  
 [Crear un archivo .Bsc](../../build/reference/building-a-dot-bsc-file.md)