---
title: "__func__ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__func__"
  - "__func___cpp"
dev_langs: 
  - "C++"
ms.assetid: a5299b8d-f0ee-4af2-91dd-8fb165e68798
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __func__
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**\(C\+\+11\)** La \_\_func\_\_ de identificador predefinido se define implícitamente como una cadena que contiene el nombre no completo y sin adornar de la función de inclusión.  El estándar de C\+\+ exige el uso de \_\_func\_\_, que no es una extensión de Microsoft.  
  
## Sintaxis  
  
```vb  
__func__  
```  
  
## Valor devuelto  
 Devuelve una matriz const char terminada en null de caracteres que contiene el nombre de función.  
  
## Ejemplo  
  
```  
  
#include <string>  
#include <iostream>  
  
namespace Test  
{  
    struct Foo  
    {  
        static void DoSomething(int i, std::string s)  
        {  
           std::cout << __func__ << std::endl; // Output: DoSomething  
        }  
    };  
}  
int main()  
{  
    Test::Foo::DoSomething(42, "Hello");  
  
    return 0;  
}  
  
```  
  
## Requisitos  
 C\+\+11