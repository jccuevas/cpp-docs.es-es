---
title: Compilador advertencia (nivel 1) C4052 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4052
dev_langs:
- C++
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
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
ms.openlocfilehash: d893ae8ca212c04fd11e0d86c1bd8fc3d6912e22
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4052"></a>Advertencia del compilador (nivel 1) C4052
las declaraciones de función son distintas; una de ellas contiene argumentos de variable  
  
 Una declaración de la función no contiene argumentos de variable. Se omite.  
  
 El ejemplo siguiente genera la advertencia C4052:  
  
```  
// C4052.c  
// compile with: /W4 /c  
int f();  
int f(int i, ...);   // C4052  
```
