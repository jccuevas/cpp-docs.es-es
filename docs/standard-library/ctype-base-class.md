---
title: "ctype_base (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "locale/std::ctype_base"
  - "std.ctype_base"
  - "ctype_base"
  - "std::ctype_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype_base (clase)"
ms.assetid: ccffe891-d7ab-4d22-baf8-8eb6d438a96d
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype_base (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase actúa como clase base para las facetas de la clase de plantilla [C](../standard-library/ctype-class.md).  Una clase base para la clase ctype que se utiliza para definir los tipos de enumeración utilizados para ordenar o probar los caracteres individualmente o dentro de los intervalos completos.  
  
## Sintaxis  
  
```  
struct ctype_base : public locale::facet  
{  
    enum  
    {  
        alnum, alpha, cntrl, digit, graph,  
        lower, print, punct, space, upper,  
        xdigit  
    };  
    typedef short mask;  
    ctype_base(  
        size_t _Refs = 0  
    );  
    ~ctype_base();  
};  
```  
  
## Comentarios  
 Define una máscara de enumeración.  Cada constante de enumeración caracteriza una forma diferente de ordenar los caracteres, como se define en las funciones con nombres similares declarados en el encabezado \<ctype.h.\>  Las constantes son:  
  
-   **space** \(función [isspace](../Topic/isspace.md)\)  
  
-   **print** \(función [isprint](../Topic/isprint.md)\)  
  
-   **cntrl** \(función [iscntrl](../Topic/iscntrl.md)\)  
  
-   **upper** \(función [isupper](../Topic/isupper.md)\)  
  
-   **lower** \(función [islower](../Topic/islower.md)\)  
  
-   **digit** \(función [isdigit](../Topic/isdigit.md)\)  
  
-   **punct** \(función [ispunct](../Topic/ispunct.md)\)  
  
-   **xdigit** \(función [isxdigit](../Topic/isxdigit.md)\)  
  
-   **alpha** \(función [isalpha](../Topic/isalpha.md)\)  
  
-   **alnum** \(función [isalnum](../Topic/isalnum.md)\)  
  
-   **graph** \(función [isgraph](../Topic/isgraph.md)\)  
  
 Puede caracterizar una combinación de clasificaciones por ORing estas constantes.  En particular, siempre es true que \=\= de **alnum** \(**alpha** ``&#124; **digit**\) y \=\= de **graph** \(**alnum**``&#124; **punct**\).  
  
## Requisitos  
 Configuración regional \<de**Header:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)