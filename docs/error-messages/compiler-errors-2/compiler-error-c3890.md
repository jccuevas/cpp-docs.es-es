---
title: Error del compilador C3890 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3890
dev_langs: C++
helpviewer_keywords: C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3f98846bc8a361bd03d453f2115e2063f37423f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3890"></a>Error del compilador C3890
'var': no se puede adquirir la dirección de un miembro de datos literal  
  
 Existe un miembro de datos literal en el montón de recolección.  Puede mover un objeto en el montón de recolección, por lo que no es útil tomar la dirección.  
  
 El ejemplo siguiente genera C3890:  
  
```  
// C3890.cpp  
// compile with: /clr  
ref struct Y1 {  
   literal int staticConst = 9;  
};  
  
int main() {  
   int p = &Y1::staticConst;   // C3890  
   int p2 = Y1::staticConst;   // OK  
}  
```