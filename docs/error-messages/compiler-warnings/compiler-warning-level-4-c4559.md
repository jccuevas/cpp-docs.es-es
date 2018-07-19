---
title: Compilador advertencia (nivel 4) C4559 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c853fa55482604d97c29653fadb06b0afdd44977
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295355"
---
# <a name="compiler-warning-level-4-c4559"></a>Advertencia del compilador (nivel 4) C4559
'función': nueva definición; la función gana __declspec (modificador)  
  
 Se vuelve a definir o se volvió a declarar una función y la segunda definición o declaración agregó un __**modificador declspec** modificador (***modificador***). La advertencia es informativa. Para corregir esta advertencia, elimine una de las definiciones.  
  
 El ejemplo siguiente genera C4559:  
  
```  
// C4559.cpp  
// compile with: /W4 /LD  
void f();  
__declspec(noalias) void f();   // C4559  
```