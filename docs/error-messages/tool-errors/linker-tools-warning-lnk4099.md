---
title: Las herramientas del vinculador LNK4099 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4099
dev_langs: C++
helpviewer_keywords: LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c9407ba96c899c6b88585f6c3894fea8f12947d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4099"></a>Advertencia de las herramientas del vinculador LNK4099
No se encontró PDB 'nombredearchivo' con 'object/library' o 'path'; se vinculará el objeto sin información de depuración  
  
 El vinculador no pudo encontrar el archivo PDB. Copiar en el directorio que contiene `object/library`.  
  
 Para buscar el nombre del archivo .pdb asociado al archivo objeto:  
  
1.  Extraer un archivo de objeto de la biblioteca con [lib](../../build/reference/lib-reference.md) **/extract:**`objectname`**.obj** `xyz` **.lib**.  
  
2.  Compruebe la ruta de acceso al archivo .pdb con **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.  
  
 También puede compilar con [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), por lo que el archivo pdb no tiene que usarse o quite el [/DEBUG](../../build/reference/debug-generate-debug-info.md) del vinculador si no tiene archivos .pdb para los objetos que se están estableciendo vínculos.