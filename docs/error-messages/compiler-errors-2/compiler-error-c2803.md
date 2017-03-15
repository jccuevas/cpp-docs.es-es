---
title: "Error del compilador C2803 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2803"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2803"
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2803
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operador' debe tener al menos un parámetro formal de tipo de clase  
  
 Al operador sobrecargado le falta un parámetro de tipo de clase.  
  
 Necesita pasar por lo menos un parámetro por referencia \(no mediante punteros, pero referencias\) o por valor para poder escribir “ \< a b” \(a y b que son del tipo de clase A\).  
  
 Si ambos parámetros son punteros, se tratará de una simple comparación de direcciones de puntero y no se utilizará la conversión definida por el usuario.  
  
 El código siguiente genera el error C2803:  
  
```  
// C2803.cpp  
// compile with: /c  
class A{};  
bool operator< (const A *left, const A *right);   // C2803  
// try the following line instead  
// bool operator< (const A& left, const A& right);  
```