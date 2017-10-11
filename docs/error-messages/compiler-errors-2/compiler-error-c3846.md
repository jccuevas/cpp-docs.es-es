---
title: Error del compilador C3846 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 58ffd3f240505d173014f1f9b358b4957a41eaf5
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3846"></a>Error del compilador C3846
'símbolo': no se puede importar un símbolo desde 'ensamblado2': como 'símbolo' ya se ha importado desde otro ensamblado 'ensamblado1'  
  
 No se pudo importar un símbolo desde un ensamblado de referencia porque ya se había importado desde un ensamblado de referencia.  
  
## <a name="example"></a>Ejemplo
El ejemplo siguiente genera C3846:  
  
```  
// C3846a.cpp  
// compile with: /LD /clr  
public ref struct G  
{  
};  
```  
  
 Y, a continuación, compile esto:  
  
```  
// C3846b.cpp  
// compile with: /clr  
#using "c3846a.dll"  
#using "c3846a.obj"   // C3846  
  
int main()  
{  
}  
```  

