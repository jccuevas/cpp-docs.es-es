---
title: Las herramientas del vinculador LNK4099 advertencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 22764705b35b2e882c5a03e819c9812d084dc118
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4099"></a>Advertencia de las herramientas del vinculador LNK4099
No se encontró PDB 'nombredearchivo' con 'object/library' o 'path'; se vinculará el objeto sin información de depuración  
  
 El vinculador no pudo encontrar el archivo PDB. Copiar en el directorio que contiene `object/library`.  
  
 Para buscar el nombre del archivo .pdb asociado al archivo objeto:  
  
1.  Extraer un archivo de objeto de la biblioteca con [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.  
  
2.  Compruebe la ruta de acceso al archivo .pdb con **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.  
  
 También puede compilar con [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), por lo que el archivo pdb no tiene que usarse o quite el [/DEBUG](../../build/reference/debug-generate-debug-info.md) del vinculador si no tiene archivos .pdb para los objetos que se están estableciendo vínculos.