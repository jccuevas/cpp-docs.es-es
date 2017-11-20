---
title: Error del compilador C2389 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2389
dev_langs: C++
helpviewer_keywords: C2389
ms.assetid: 6122dc81-4ee3-49a5-a67d-d867808c9bac
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e171a857247963e0278f7a167b70612b8234b323
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2389"></a>Error del compilador C2389
'operador': operando no válido 'nullptr'  
  
 `nullptr` no puede ser un operando.  
  
 El ejemplo siguiente genera la advertencia C2389:  
  
```  
// C2389.cpp  
// compile with: /clr  
int main() {  
   throw nullptr;   // C2389  
}  
```