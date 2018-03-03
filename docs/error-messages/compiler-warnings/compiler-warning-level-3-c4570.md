---
title: Compilador advertencia (nivel 3) C4570 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4570
dev_langs:
- C++
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ecd1794de0ad36c5116d5db9f051ed9ddc9cf12e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4570"></a>Advertencia del compilador (nivel 3) C4570
'type': no se ha declarado explícitamente como abstracto pero tiene funciones abstractas  
  
 Un tipo que contenga [abstracta](../../windows/abstract-cpp-component-extensions.md) funciones deben estar marcadas como abstracto.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4570.  
  
```  
// C4570.cpp  
// compile with: /clr /W3 /c  
ref struct X {   // C4570  
// try the following line instead  
// ref class X abstract {  
   virtual void f() abstract;  
};  
```