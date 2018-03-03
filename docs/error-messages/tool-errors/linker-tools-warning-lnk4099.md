---
title: Las herramientas del vinculador LNK4099 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 364c2f9303707328ebf3bdf3284398e6d4f9f0d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4099"></a>Advertencia de las herramientas del vinculador LNK4099
No se encontró PDB 'nombredearchivo' con 'object/library' o 'path'; se vinculará el objeto sin información de depuración  
  
 El vinculador no pudo encontrar el archivo PDB. Copiar en el directorio que contiene `object/library`.  
  
 Para buscar el nombre del archivo .pdb asociado al archivo objeto:  
  
1.  Extraer un archivo de objeto de la biblioteca con [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.  
  
2.  Compruebe la ruta de acceso al archivo .pdb con **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.  
  
 También puede compilar con [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), por lo que el archivo pdb no tiene que usarse o quite el [/DEBUG](../../build/reference/debug-generate-debug-info.md) del vinculador si no tiene archivos .pdb para los objetos que se están estableciendo vínculos.