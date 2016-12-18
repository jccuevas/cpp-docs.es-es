---
title: "Error del compilador C2665 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2665"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2665"
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2665
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : ninguna de las sobrecargas número1 puede convertir el parámetro número2 del tipo 'tipo'  
  
 No se puede convertir un parámetro de la función sobrecargada al tipo requerido.  Posible solución:  
  
-   Proporcione un operador de conversión.  
  
-   Utilice una conversión explícita.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2665.  
  
```  
// C2665.cpp  
void func(short, char*){}  
void func(char*, char*){}  
  
int main() {  
   func(0, 1);   // C2665  
   func((short)0, (char*)1);   // OK  
}  
```