---
title: Las herramientas del vinculador LNK1140 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc0d59589a1882aca4ef2deb419e1e4f1081e52b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1140"></a>Error de las herramientas del vinculador LNK1140
Hay demasiados módulos para la base de datos de programa; vincule con/PDB: ninguno  
  
 El proyecto contiene más de 4096 módulos.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Vuelva a vincular con [/PDB: NONE](../../build/reference/pdb-use-program-database.md).  
  
2.  Compile algunos módulos sin información de depuración.  
  
3.  Reduzca el número de módulos.