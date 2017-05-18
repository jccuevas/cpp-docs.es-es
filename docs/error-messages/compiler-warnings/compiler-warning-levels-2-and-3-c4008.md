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
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 0539a36dddf5bed1d7474f6456eb710bb0506ae4
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Advertencia del compilador (niveles 2 y 3) C4008
'identificador': atributo ' atributo ' omitido  
  
 El compilador omitió el atributo `__fastcall`, **estatic**o **inline** para una función (advertencia de nivel 3) o datos (advertencia de nivel 2).  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  `__fastcall`atributo con datos.  
  
2.  Los atributos**static** o **inline** con la función **main** .
