---
title: Compilador advertencia (nivel 1) C4369 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63445f0713b43ce7fde418ebd9d65403965c07ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276534"
---
# <a name="compiler-warning-level-1-c4369"></a>Advertencia del compilador (nivel 1) C4369
'enumerador': no se puede representar el valor del enumerador 'valor' como 'type', el valor es 'new_value'  
  
 Un enumerador se calculó para ser mayor que el valor máximo para el tipo subyacente especificado.  Esto produjo un desbordamiento y el compilador ajustó el valor del enumerador para el valor más bajo posible para el tipo.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4369.  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```