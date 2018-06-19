---
title: Crear una. SBR truncado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdada1f4d07d02988da388e39e332c832f633adb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32371088"
---
# <a name="creating-an-sbr-file"></a>Crear un archivo .Sbr
Los archivos de entrada para BSCMAKE son archivos. sbr. El compilador crea un archivo .sbr para cada archivo objeto (.obj) que compila. Al crear o actualizar el archivo de información de examen, todos los archivos .sbr para el proyecto deben estar disponibles en disco.  
  
 Para crear un archivo .sbr con toda la información posible, especifique [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md).  
  
 Para crear un archivo .sbr que no contenga símbolos locales, especifique [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md). Si los archivos .sbr contienen símbolos locales, se puede omitir en el archivo .bsc mediante el uso de BSCMAKE [/ el: opción](../../build/reference/bscmake-options.md)`.`  
  
 Puede crear un archivo .sbr sin realizar una compilación completa. Por ejemplo, puede especificar la opción /Zs al compilador que debe realizar una comprobación de sintaxis y seguir generando un archivo .sbr si se especifica /FR o/el fr.  
  
 El proceso de compilación puede ser más eficaz si los archivos .sbr se empaquetan antes para quitar las definiciones sin referencia. El compilador empaqueta automáticamente los archivos .sbr.  
  
## <a name="see-also"></a>Vea también  
 [Crear un archivo .Bsc](../../build/reference/building-a-dot-bsc-file.md)