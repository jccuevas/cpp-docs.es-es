---
title: C2007 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2007
dev_langs:
- C++
helpviewer_keywords:
- C2007
ms.assetid: ecd09d99-5036-408b-9e46-bc15488f049e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7b4cb49426125df28793e7d2b7800198a129db3d
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2007"></a>C2007 de Error del compilador
\#definir la sintaxis  
  
 No aparece ningún identificador después un `#define`. Para resolver el error, use un identificador.  
  
 El ejemplo siguiente genera C2007:  
  
```  
// C2007.cpp  
#define   // C2007  
```  
  
 Posible solución:  
  
```  
// C2007b.cpp  
// compile with: /c  
#define true 1  
```
