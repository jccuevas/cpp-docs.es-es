---
title: Compilador advertencia (nivel 1) C4810 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4810
dev_langs:
- C++
helpviewer_keywords:
- C4810
ms.assetid: 39e2cae0-9c1c-4ac1-aaa0-5f661d06085b
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
ms.openlocfilehash: ef9e0f9dd437a6e2c57f2faccf958ccd7c37843f
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4810"></a>Advertencia del compilador (nivel 1) C4810
valor de pragma pack(show) == n  
  
 Esta advertencia se emite cuando se utiliza la **mostrar** opción de la [pack](../../preprocessor/pack.md) pragma. *n* es el valor actual de pack.  
  
 Por ejemplo, el código siguiente muestra cómo funciona la advertencia C4810 con pragma pack:  
  
```  
// C4810.cpp  
// compile with: /W1 /LD  
// C4810 expected  
#pragma pack(show)  
#pragma pack(4)  
#pragma pack(show)  
```
