---
title: Error de compilador Error C2767 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2767
dev_langs:
- C++
helpviewer_keywords:
- C2767
ms.assetid: e8f84178-a160-4d71-a236-07e4fcc11e96
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe74f9374a6fb74a514fd2655b2e1dbadf02639
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2767"></a>Error C2767 de Error del compilador
administrado o incoherencia de dimensión de WinRTarray: se esperaban N argumentos n - se proporcionaron M  
  
 Una declaración de matriz administrada o de WinRT estaba mal formada. Para obtener más información, vea [Matriz](../../windows/arrays-cpp-component-extensions.md).  
  
 El siguiente ejemplo genera el error C2767 y muestra cómo corregirlo:  
  
```  
// C2767.cpp  
// compile with: /clr  
int main() {  
   array<int> ^p1 = new array<int>(2,3); // C2767  
   array<int> ^p2 = new array<int>(2);   // OK  
}  
```