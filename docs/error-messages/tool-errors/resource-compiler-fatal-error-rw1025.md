---
title: Error irrecuperable del compilador de recursos RW1025 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW1025
dev_langs:
- C++
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ba216e63cb0cae92b4541800493a2fb6195553a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320019"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Error irrecuperable del compilador de recursos RW1025
Memoria de montón far insuficiente  
  
 Comprobar si hay software residente en memoria que podría estar ocupando demasiado espacio. Utilice el programa CHKDSK para averiguar cuánta memoria disponible.  
  
 Si está creando un archivo de recursos grande, divida el script de recursos en dos archivos. Después de crear dos archivos, use la línea de comandos de MS-DOS para combinarlas:  
  
```  
copy first.res /b + second.res /b full.res  
```