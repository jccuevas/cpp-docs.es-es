---
title: Compilador advertencia (nivel 1) C4075 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4075
dev_langs:
- C++
helpviewer_keywords:
- C4075
ms.assetid: 19a700b6-f210-4b9d-a2f2-76cfe39ab178
caps.latest.revision: 7
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
ms.openlocfilehash: f7785f080f6ef86010a99df77c28bd806783f921
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4075"></a>Advertencia del compilador (nivel 1) C4075
inicializadores situados en un área de inicialización no reconocida  
  
 Un [#pragma init_seg](../../preprocessor/init-seg.md) utiliza un nombre de sección desconocido. El compilador omite el comando **pragma** .  
  
 El ejemplo siguiente genera la advertencia C4075:  
  
```  
// C4075.cpp  
// compile with: /W1  
#pragma init_seg("mysegg")   // C4075  
  
// try..  
// #pragma init_seg(user)  
  
int main() {  
}  
```
