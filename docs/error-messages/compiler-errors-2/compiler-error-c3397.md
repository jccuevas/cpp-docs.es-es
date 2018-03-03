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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b0729f99b14b405e097366aa4d3562af918d8651
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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