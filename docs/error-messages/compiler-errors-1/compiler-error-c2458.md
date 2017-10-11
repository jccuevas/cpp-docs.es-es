---
title: Error del compilador C2458 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2458
dev_langs:
- C++
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 511d6685ff6447793baa14468f6414fec99a3772
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2458"></a>Error del compilador C2458
'identificador': nueva definición dentro de la definición  
  
 Una clase, estructura, unión o enumeración se vuelve a definir en su propia declaración.  
  
 El ejemplo siguiente genera C2458:  
  
```  
// C2458.cpp  
class C {  
   enum i { C };   // C2458  
};  
```
