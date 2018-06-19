---
title: Error del compilador C3846 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3846
dev_langs:
- C++
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97d5650d1743ba379ce065d4051bfed807a1df71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268031"
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
