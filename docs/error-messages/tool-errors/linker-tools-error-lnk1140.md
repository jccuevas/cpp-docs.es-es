---
title: Las herramientas del vinculador LNK1140 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1140
dev_langs: C++
helpviewer_keywords: LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5a7bce157359d547f91ba2b560cf258e231b4a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1140"></a>Error de las herramientas del vinculador LNK1140
Hay demasiados módulos para la base de datos de programa; vincule con/PDB: ninguno  
  
 El proyecto contiene más de 4096 módulos.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo  
  
1.  Vuelva a vincular con [/PDB: NONE](../../build/reference/pdb-use-program-database.md).  
  
2.  Compile algunos módulos sin información de depuración.  
  
3.  Reduzca el número de módulos.