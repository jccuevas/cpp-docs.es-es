---
title: Compilador advertencia (niveles 2 y 3) C4008 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: afd45078ac75ec9da8343baa2c203e75b324fb6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Advertencia del compilador (niveles 2 y 3) C4008
'identificador': atributo ' atributo ' omitido  
  
 El compilador omitió el atributo `__fastcall`, **estatic**o **inline** para una función (advertencia de nivel 3) o datos (advertencia de nivel 2).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El atributo`__fastcall` con datos.  
  
2.  Los atributos**static** o **inline** con la función **main** .