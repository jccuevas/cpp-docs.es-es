---
title: Compilador advertencia (nivel 3) C4023 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4023
dev_langs:
- C++
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 420dc18e62a4b40124ef49171c2c76a66ed0cb64
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4023"></a>Advertencia del compilador (nivel 3) C4023
'símbolo': el puntero con base se pasó a la función sin prototipo: número de parámetro  
  
 Si se pasa un puntero con base a una función sin prototipo, el puntero se normaliza, con resultados imprevisibles.  
  
 Para resolver esta advertencia, use funciones prototipo a las que se pasan punteros con base.
