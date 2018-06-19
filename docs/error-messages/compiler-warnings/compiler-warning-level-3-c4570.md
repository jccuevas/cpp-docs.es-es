---
title: Compilador advertencia (nivel 3) C4570 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4570
dev_langs:
- C++
helpviewer_keywords:
- C4570
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a79b6afae4bc14e5fcd2dc4979ebd29c60c15b7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33289846"
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