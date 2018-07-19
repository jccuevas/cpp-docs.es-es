---
title: Error del compilador C2004 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2004
dev_langs:
- C++
helpviewer_keywords:
- C2004
ms.assetid: d81526dd-3a00-4593-87b0-d910d3d29bca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d4030ea3c82c1a893ebf35903d3fbc362c594282
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33164743"
---
# <a name="compiler-error-c2004"></a>Error del compilador C2004
se esperaba 'defined(id)'  
  
 Debe aparecer un identificador en los paréntesis que siguen a la palabra clave del preprocesador.  
  
 Este error también puede generarse como resultado del trabajo de conformidad del compilador efectuado para Visual Studio. NET 2003: faltan paréntesis en la directiva del preprocesador. Si no existe paréntesis de cierre de una directiva de preprocesador, el compilador generará un error.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2004:  
  
```  
// C2004.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG   // C2004  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Posible resolución:  
  
```  
// C2004b.cpp  
// compile with: /DDEBUG  
#include <stdio.h>  
  
int main()   
{  
    #if defined(DEBUG)  
        printf_s("DEBUG defined\n");  
    #endif  
}  
```