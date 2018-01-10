---
title: Tipos incompletos | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e14c2811debfe01f7eb5ae7fc36bebfe0580017
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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