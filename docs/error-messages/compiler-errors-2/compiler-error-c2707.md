---
title: C2707 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2707
dev_langs: C++
helpviewer_keywords: C2707
ms.assetid: 3deaf45c-74da-4c9d-acc6-b82412720b74
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 46ca756cf6491506cefc38e34992fa5e3fb67429
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2707"></a>C2707 de Error del compilador
'identifier': contexto incorrecto para la función intrínseca  
  
 Funciones intrínsecas de control de excepciones estructurados no son válidas en algunos contextos:  
  
-   `_exception_code()`fuera de un filtro de excepción o `__except` bloque  
  
-   `_exception_info()`fuera de un filtro de excepción  
  
-   `_abnormal_termination()`fuera de un `__finally` bloque  
  
 Para resolver el error, asegúrese de que las funciones intrínsecas de control de excepciones se colocan en el contexto adecuado.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2707.  
  
```  
// C2707.cpp  
#include <windows.h>  
#include <stdio.h>  
  
LONG MyFilter(LONG excode)   
{  
    return (excode == EXCEPTION_ACCESS_VIOLATION ?  
        EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);   // OK  
}  
  
LONG func(void)   
{  
    int x, y;  
    return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ?  // C2707  
             EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);  
  
    __try   
    {  
        y = 0;  
        x = 4 / y;  
        return 0;  
     }  
  
    __except(MyFilter(GetExceptionCode()))   
    {  
        return(GetExceptionCode() == EXCEPTION_ACCESS_VIOLATION ? // ok  
               EXCEPTION_EXECUTE_HANDLER : EXCEPTION_CONTINUE_SEARCH);  
    }  
}  
  
int main()   
{  
    __try   
    {  
        func();  
    } __except(EXCEPTION_EXECUTE_HANDLER)  
    {  
        printf_s("Caught exception\n");  
    }  
}  
```