---
title: "El par&#225;metro &#39;ByRef&#39; &lt;nombreDePar&#225;metro&gt; no se puede usar en una expresi&#243;n de consulta | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36533"
  - "bc36533"
helpviewer_keywords: 
  - "BC36533"
ms.assetid: 8067ac87-dd6b-4869-87d0-8a4ce272de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# El par&#225;metro &#39;ByRef&#39; &lt;nombreDePar&#225;metro&gt; no se puede usar en una expresi&#243;n de consulta
Un parámetro que se incluye en una consulta LINQ es un tipo de puntero. Los parámetros usados en las expresiones de consulta no se puede pasar por referencia.  
  
 **Identificador de error:** BC36533  
  
### Para corregir este error  
  
1.  Declare una nueva variable y asigne su valor a una copia del valor pasado por referencia. Use la variable copiada en la consulta LINQ. A continuación se muestra un ejemplo:  
  
    ```vb#  
    Sub RunQuery(ByVal collection As List(Of Integer), _  
                 ByRef filterValue As Integer)  
        Dim fv = filterValue  
        Dim queryResult = From num In collection _  
                          Where num < fv  
    End Sub  
    ```  
  
### Para corregir este error  
  
1.  Reemplace la palabra clave `ByRef` por la palabra clave `ByVal` para el parámetro usado en la consulta.  
  
## Vea también  
 [Diferencias entre pasar un argumento por valor y por referencia](../Topic/Differences%20Between%20Passing%20an%20Argument%20By%20Value%20and%20By%20Reference%20\(Visual%20Basic\).md)   
 [Introducción a LINQ en Visual Basic](../Topic/Introduction%20to%20LINQ%20in%20Visual%20Basic.md)   
 [LINQ](../Topic/LINQ%20in%20Visual%20Basic.md)