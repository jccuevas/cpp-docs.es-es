---
title: "terminate (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "terminate"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "terminate"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "control de excepciones, terminación"
  - "terminate (función)"
ms.assetid: 90e67402-08e9-4b2a-962c-66a8afd3ccb4
caps.latest.revision: 12
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# terminate (CRT)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Llamadas `abort` o una función especificada mediante `set_terminate`.  
  
## Sintaxis  
  
```  
void terminate( void );  
```  
  
## Comentarios  
 La función de `terminate` se utiliza con el control de excepciones de C\+\+ y se denomina en los casos siguientes:  
  
-   Un controlador coincidente de captura no se encuentra para una excepción de C\+\+.  
  
-   Una excepción se produce por una función destructora durante pila desenredo.  
  
-   El montón está dañado después de que se produzca una excepción.  
  
 llamadas `abort` de`terminate` de forma predeterminada.  Puede cambiar este valor predeterminado escribiendo dispone de la función de finalización y llamando `set_terminate` con el nombre de la función como argumento.  `terminate` llama a la función última especificada como argumento a `set_terminate`.  Para obtener más información, vea [Excepciones de C\+\+ no controlados](../../cpp/unhandled-cpp-exceptions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`terminate`|\<eh.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_terminate.cpp  
// compile with: /EHsc  
#include <eh.h>  
#include <process.h>  
#include <iostream>  
using namespace std;  
  
void term_func();  
  
int main()  
{  
    int i = 10, j = 0, result;  
    set_terminate( term_func );  
    try  
    {  
        if( j == 0 )  
            throw "Divide by zero!";  
        else  
            result = i/j;  
    }  
    catch( int )  
    {  
        cout << "Caught some integer exception.\n";  
    }  
    cout << "This should never print.\n";  
}  
  
void term_func()  
{  
    cout << "term_func() was called by terminate().\n";  
  
    // ... cleanup tasks performed here  
  
    // If this function does not exit, abort is called.  
  
    exit(-1);  
}  
```  
  
  **term\_func\(\) se llama terminate\(\).**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Rutinas para el control de excepciones](../../c-runtime-library/exception-handling-routines.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md)   
 [set\_terminate](../../c-runtime-library/reference/set-terminate-crt.md)   
 [set\_unexpected](../../c-runtime-library/reference/set-unexpected-crt.md)   
 [unexpected](../../c-runtime-library/reference/unexpected-crt.md)