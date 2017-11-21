---
title: Compilador advertencia (nivel 4) C4670 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4670
dev_langs: C++
helpviewer_keywords: C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 49c29f03b8b6f364cddd0c55672b4ab246f1e708
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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