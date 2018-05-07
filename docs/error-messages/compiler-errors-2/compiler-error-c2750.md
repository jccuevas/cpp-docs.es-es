---
title: C2750 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2750
dev_langs:
- C++
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06731b0b386b200b74697592137aac10a48a8e82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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