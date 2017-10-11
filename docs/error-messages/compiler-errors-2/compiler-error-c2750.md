---
title: C2750 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2750
dev_langs:
- C++
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: fbe3ee423183bb841e3e6777db94e4645b94355d
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2750"></a>C2750 de Error del compilador
'type': no se puede utilizar 'new' en el tipo de referencia; Utilice 'gcnew' en su lugar  
  
 Para crear una instancia de un tipo CLR, lo que hace que la instancia se coloque en el montón de recolección, debe usar [gcnew](../../windows/ref-new-gcnew-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C2750:  
  
```  
// C2750.cpp  
// compile with: /clr  
ref struct Y1 {};  
  
int main() {  
   Y1 ^ x = new Y1;   // C2750  
  
   // try the following line instead  
   Y1 ^ x2 = gcnew Y1;  
}  
```
