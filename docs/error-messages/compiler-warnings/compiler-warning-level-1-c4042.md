---
title: "Advertencia del compilador (nivel 1) C4042 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4042"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4042"
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (nivel 1) C4042
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : tiene una clase de almacenamiento incorrecta  
  
 La clase de almacenamiento especificada no se puede utilizar con este identificador en el contexto actual.  El compilador utiliza en su lugar la clase de almacenamiento predeterminada.  
  
-   `extern`, si *identificador* es una función.  
  
-   **auto**, si *identificador* es un parámetro formal o variable local.  
  
-   Ninguna clase de almacenamiento, si *identificador* es una variable global.  
  
 Esta advertencia puede producirse cuando se especifica una clase de almacenamiento distinta de **register** en una declaración de parámetro.  
  
 El ejemplo siguiente genera C4042:  
  
```  
// C4042.cpp  
// compile with: /W1 /LD  
int func2( __declspec( thread ) int tls_i )    // C4042  
// try the following line instead  
// int func2( int tls_i )  
{  
   return tls_i;  
}  
```