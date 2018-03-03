---
title: Error irrecuperable del compilador de recursos RW1025 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 487968f8a1242dd4c36e4bbd9b4ede08a5ab4d95
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Error irrecuperable del compilador de recursos RW1025
Memoria de montón far insuficiente  
  
 Comprobar si hay software residente en memoria que podría estar ocupando demasiado espacio. Utilice el programa CHKDSK para averiguar cuánta memoria disponible.  
  
 Si está creando un archivo de recursos grande, divida el script de recursos en dos archivos. Después de crear dos archivos, use la línea de comandos de MS-DOS para combinarlas:  
  
```  
copy first.res /b + second.res /b full.res  
```