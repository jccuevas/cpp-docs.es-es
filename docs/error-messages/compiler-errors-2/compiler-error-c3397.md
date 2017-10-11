---
title: Error del compilador C3397 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3397
dev_langs:
- C++
helpviewer_keywords:
- C3397
ms.assetid: a8536e87-79c4-4ed7-bd96-42704d06391f
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 778e57e1071764b63a6293907403bd53a2989372
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3397"></a>Error del compilador C3397
No se permite la inicialización de agregado en argumentos predeterminados  
  
 Se ha declarado una matriz incorrectamente.  Vea [matrices](../../windows/arrays-cpp-component-extensions.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3397.  
  
```  
// C3397.cpp  
// compile with: /clr  
// /clr /c  
void Func(array<int> ^p = gcnew array<int> { 1, 2, 3 });   // C3397  
void Func2(array<int> ^p = gcnew array<int> (3));   // OK  
  
int main() {  
   array<int> ^p = gcnew array<int> { 1, 2, 3};   // OK  
}  
```
