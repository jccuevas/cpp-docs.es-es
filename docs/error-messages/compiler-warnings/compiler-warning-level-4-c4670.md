---
title: Compilador advertencia (nivel 4) C4670 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4670
dev_langs:
- C++
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9bec30fff715984073aa3061979fff11923f0bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315365"
---
# <a name="compiler-warning-level-4-c4670"></a>Advertencia del compilador (nivel 4) C4670
'identifier': no se puede obtener acceso a esta clase base  
  
 La clase base especificada de un objeto para que se produzca en un bloque **try** no es accesible. No se puede crear una instancia del objeto. Compruebe que la clase base se hereda con el especificador de acceso correcto.  
  
 El ejemplo siguiente genera la advertencia C4670:  
  
```  
// C4670.cpp  
// compile with: /EHsc /W4  
class A  
{  
};  
  
class B : /* public */ A  
{  
} b;   // inherits A with private access by default  
  
int main()  
{  
    try  
    {  
       throw b;   // C4670  
    }  
    catch( B )  
    {  
    }  
}  
```