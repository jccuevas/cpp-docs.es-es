---
title: "Error irrecuperable C1004 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1004"
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable C1004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se esperaba el final de archivo encontrado  
  
 El compilador alcanzó el final de un archivo de código fuente sin resolver una construcción.  Puede que en el código falte alguno de los siguientes elementos:  
  
-   Una llave de cierre  
  
-   Un paréntesis de cierre  
  
-   Un marcador de comentario de cierre \(\*\/\)  
  
-   Un punto y coma  
  
 Para solucionar este error, realice una de las acciones siguientes:  
  
-   La unidad de disco predeterminada no tiene suficiente espacio para archivos temporales \(requieren unas dos veces más espacio que el archivo de código fuente\).  
  
-   Una directiva `#if` que da como resultado false carece de una directiva de cierre `#endif`.  
  
-   Un archivo de código fuente no termina con los caracteres retorno de carro y alimentación de línea.  
  
 El código siguiente genera el error C1004:  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 Posible solución:  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```