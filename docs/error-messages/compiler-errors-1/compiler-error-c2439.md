---
title: Error del compilador C2439 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2439
dev_langs:
- C++
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33bfe8ebf00850a54020b2a3f21159daf28b7224
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2439"></a>Error del compilador C2439
'identificador': no se pudo inicializar el miembro  
  
 No se puede inicializar una clase, estructura o miembro de unión.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Intentando inicializar una estructura o clase base indirecta.  
  
2.  Intentando inicializar a un miembro heredado de una clase o estructura. El constructor de la clase o estructura debe inicializar un miembro heredado.