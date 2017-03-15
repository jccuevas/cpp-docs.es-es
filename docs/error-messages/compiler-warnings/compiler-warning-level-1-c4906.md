---
title: "Advertencia del compilador (nivel 1) C4906 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4906"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4906"
ms.assetid: 05318e74-799b-412a-9dce-f02b8161d762
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 1) C4906
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

conversión de literal de cadena a 'LPWSTR'  
  
 El compilador detectó una conversión no segura.  La conversión tuvo lugar, pero es necesario utilizar una rutina de conversión.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Ejemplo  
 El código siguiente genera el error C4906:  
  
```  
// C4906.cpp  
// compile with: /W1  
#pragma warning(default : 4906)  
#include <windows.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main()  
{  
    LPWSTR x = (LPWSTR)"1234";   // C4906  
  
    // try the following lines instead  
    // char y[128];  
    // size_t numberOfCharConverted = 0;  
    // errcode err = 0;  
    // err = wcstombs_s(&numberOfCharConverted , &y[0], 128,  
    //                  L"12345", 4);  
    // if (err != 0)  
    // {  
    //     printf_s("wcstombs_s failed!");  
    //     return -1;  
    // }  
    // printf_s("%s\n", y);  
  
    return 0;  
}  
```