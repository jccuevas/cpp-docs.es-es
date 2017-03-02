---
title: Compilador advertencia (nivel 4) C4057 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4057
dev_langs:
- C++
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
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
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: ad1013a90b2b3d6ad1f7148ea62c05ae505348d4
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-4-c4057"></a>Advertencia del compilador (nivel 4) C4057
'operador': direccionamiento indirecto de 'identificador1' a tipos base ligeramente distintos de 'identificador2'.  
  
 Dos expresiones de puntero hacen referencia a diferentes tipos base. Las expresiones se usan sin conversión.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:  
  
1.  Combinación de tipos con signo y sin signo.  
  
2.  Combinación de tipos **short** y **long** .
