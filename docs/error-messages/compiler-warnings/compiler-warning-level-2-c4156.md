---
title: "Advertencia del compilador (nivel 2) C4156 | Microsoft Docs"
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
  - "C4156"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4156"
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4156
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

eliminación de expresión de matriz sin utilizar el formato de matriz de 'delete'; formato de matriz sustituido  
  
 El formato de **delete** que no es de matriz no puede eliminar una matriz.  El compilador convirtió **delete** a la forma de matriz.  
  
 Esta advertencia se produce sólo con las extensiones de Microsoft \(\/Ze\).  
  
## Ejemplo  
  
```  
// C4156.cpp  
// compile with: /W2  
int main()  
{  
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];  
   delete array; // C4156, changed by compiler to "delete [] array;"  
}  
```