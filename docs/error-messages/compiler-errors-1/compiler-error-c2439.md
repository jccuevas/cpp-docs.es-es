---
title: Error del compilador C2439 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 79b6ef4b6182a525bb8c8fc5e7e9fc7bd541f870
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2439"></a>Error del compilador C2439
'identificador': no se pudo inicializar el miembro  
  
 No se puede inicializar una clase, estructura o miembro de unión.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Intentando inicializar una estructura o clase base indirecta.  
  
2.  Intentando inicializar a un miembro heredado de una clase o estructura. El constructor de la clase o estructura debe inicializar un miembro heredado.