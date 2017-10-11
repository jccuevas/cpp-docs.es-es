---
title: Error del compilador C3539 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3539
dev_langs:
- C++
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 03283217be6aabbf216e2e60ad47abfc01a961d6
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3539"></a>Error del compilador C3539
'type': un argumento de plantilla no puede ser un tipo que contiene 'auto'  
  
 El tipo de argumento de plantilla indicado no puede contener un uso de la `auto` (palabra clave).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  No se especifica el argumento de plantilla con el `auto` palabra clave.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera C3539.  
  
```  
// C3539.cpp  
// Compile with /Zc:auto  
template<class T> class C{};  
int main()  
{  
   C<auto> c;   // C3539  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)
