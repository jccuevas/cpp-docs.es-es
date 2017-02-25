---
title: "Tipos incompletos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C], tipos incompletos"
  - "tipos incompletos"
  - "estructuras, incompleto"
  - "tipos [C], incompleto"
  - "uniones, incompleto"
  - "void (palabra clave) [C]"
  - "void (palabra clave) [C], incompleto"
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Tipos incompletos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un tipo incompleto es un tipo que describe un identificador pero carece de la información necesaria para determinar el tamaño del mismo.  Un "tipo incompleto" puede ser:  
  
-   Un tipo de estructura cuyos miembros todavía no se han especificado.  
  
-   Un tipo de unión cuyos miembros todavía no se han especificado.  
  
-   Un tipo de matriz cuya dimensión todavía no se ha especificado.  
  
 El tipo void es un tipo incompleto que no se puede completar.  Para completar un tipo incompleto, especifique la información que falta.  Los ejemplos siguientes muestran cómo crear y completar los tipos incompletos.  
  
-   Para crear un tipo de estructura incompleto, declare un tipo de estructura sin especificar sus miembros.  En este ejemplo, el puntero `ps` señala a un tipo de estructura incompleto denominado `student`.  
  
    ```  
    struct student *ps;  
    ```  
  
-   Para completar un tipo de estructura incompleto, declare el mismo tipo de estructura más adelante, en el mismo ámbito, con sus miembros especificados, como en:  
  
    ```  
    struct student  
    {  
        int num;  
    }                   /* student structure now completed */  
    ```  
  
-   Para crear un tipo de matriz incompleto, declare un tipo de matriz sin especificar su recuento de repetición.  Por ejemplo:  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   Para completar un tipo de matriz incompleto, declare el mismo nombre más adelante, en el mismo ámbito, con su recuento de repetición especificado, como en:  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)