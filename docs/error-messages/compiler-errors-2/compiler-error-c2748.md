---
title: Error de compilador Error C2748 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2748
dev_langs:
- C++
helpviewer_keywords:
- C2748
ms.assetid: b63ac78b-a200-499c-afea-15af1a1e819e
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: f0eaee593630a40a6bffb126e9eab8ed17668e02
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2748"></a>Error C2748 de Error del compilador
la creación de matrices administradas o WinRT debe disponer de un tamaño de matriz o un inicializador de matriz  
  
 Una matriz administrada o WinRT estaba mal formada. Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera el error C2748 y muestra cómo corregirlo:  
  
```  
// C2748.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>();   // C2748  
   // try the following line instead  
   array<int> ^p2 = new array<int>(2);  
}  
```
