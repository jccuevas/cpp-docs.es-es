---
title: C2657 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2657
dev_langs:
- C++
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2e0e06104458961297a4d0a3de8b7cda756d16ab
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2657"></a>C2657 de Error del compilador
' clase:: *' se encuentra al principio de una instrucción (¿olvidó especificar un tipo?)  
  
 La línea comenzaba con un identificador de puntero a miembro.  
  
 Este error puede deberse a un falta el especificador de tipo en la declaración de un puntero a un miembro.  
  
 El ejemplo siguiente genera C2657:  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```
