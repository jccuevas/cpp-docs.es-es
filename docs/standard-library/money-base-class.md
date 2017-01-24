---
title: "money_base (Clase) | Microsoft Docs"
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
  - "locale/std::money_base"
  - "money_base"
  - "std::money_base"
  - "std.money_base"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_base (clase)"
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: 19
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# money_base (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase describe una enumeración y un común de estructura a todas las especializaciones de la clase de plantilla [moneypunct](../standard-library/moneypunct-class.md).  
  
## Sintaxis  
  
```  
struct money_base : public locale::facet  
{  
    enum  
    {  
        symbol = '$',  
        sign = '+',  
        space = ' ',  
        value = 'v',  
        none = 'x'  
    };  
    typedef int part;  
    struct pattern  
    {  
        char field[_PATTERN_FIELD_SIZE];  
    };  
    money_base(  
        size_t _Refs = 0  
    );  
    ~money_base();  
};  
```  
  
## Comentarios  
 La enumeración **part** describe los posibles valores de los elementos del campo de matriz en el modelo de la estructura.  Los valores de **part** son:  
  
-   **none** para buscar coincidencias con cero o más espacio o no generar nada.  
  
-   **sign** a coincidir o generar un signo positivo o negativo.  
  
-   **space** para buscar coincidencias con cero o más espacio o generar un espacio.  
  
-   **símbolo** a coincidir o generar un símbolo de moneda.  
  
-   **Valor** a coincidir o generar un valor monetario.  
  
## Requisitos  
 Configuración regional \<de**Header:** \>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)