---
title: "Error del compilador C2390 | Microsoft Docs"
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
  - "C2390"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2390"
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2390
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : clase de almacenamiento 'especificador' incorrecta  
  
 La clase de almacenamiento no es válida para el identificador de ámbito global.  Se utiliza la clase de almacenamiento predeterminada en lugar de la clase no válida.  
  
 Posible solución:  
  
-   Si el identificador es una función, declárela con almacenamiento `extern`.  
  
-   Si el identificador es un parámetro formal o una variable local, declárelos con almacenamiento automático.  
  
-   Si el identificador es una variable global, declárela sin clase de almacenamiento \(almacenamiento automático\).  
  
## Ejemplo  
  
-   El código siguiente genera el error C2390:  
  
```  
// C2390.cpp  
register int i;   // C2390  
  
int main() {  
   register int j;   // OK  
}  
```