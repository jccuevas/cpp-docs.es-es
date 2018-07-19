---
title: Compilador advertencia (niveles 2 y 3) C4008 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4cdc88f222f9e5ce3829a63c131c955ce2abdd7d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294263"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Advertencia del compilador (niveles 2 y 3) C4008
'identificador': atributo ' atributo ' omitido  
  
 El compilador omitió el atributo `__fastcall`, **estatic**o **inline** para una función (advertencia de nivel 3) o datos (advertencia de nivel 2).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  El atributo`__fastcall` con datos.  
  
2.  Los atributos**static** o **inline** con la función **main** .