---
title: Tipos incompletos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 2dd7ab170717cb0e20d71ad4e62e2cbc03483fbf
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="incomplete-types"></a>Tipos incompletos
Un tipo incompleto es un tipo que describe un identificador pero carece de la información necesaria para determinar el tamaño del mismo. Un "tipo incompleto" puede ser:  
  
-   Un tipo de estructura cuyos miembros todavía no se han especificado.  
  
-   Un tipo de unión cuyos miembros todavía no se han especificado.  
  
-   Un tipo de matriz cuya dimensión todavía no se ha especificado.  
  
 El tipo void es un tipo incompleto que no se puede completar. Para completar un tipo incompleto, especifique la información que falta. Los ejemplos siguientes muestran cómo crear y completar los tipos incompletos.  
  
-   Para crear un tipo de estructura incompleto, declare un tipo de estructura sin especificar sus miembros. En este ejemplo, el puntero `ps` señala a un tipo de estructura incompleto denominado `student`.  
  
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
  
-   Para crear un tipo de matriz incompleto, declare un tipo de matriz sin especificar su recuento de repetición. Por ejemplo:  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   Para completar un tipo de matriz incompleto, declare el mismo nombre más adelante, en el mismo ámbito, con su recuento de repetición especificado, como en:  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)
