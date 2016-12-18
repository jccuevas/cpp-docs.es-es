---
title: "Advertencia del compilador (nivel 1) C4788 | Microsoft Docs"
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
  - "C4788"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4788"
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4788
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': el identificador se ha truncado a 'número' caracteres  
  
 El compilador limita la longitud máxima permitida para un nombre de función.  Cuando el compilador genera funclets para código EH\/SEH, compone el nombre del funclet anteponiendo algún texto al nombre de la función, como por ejemplo, "\_\_catch", "\_\_unwind", u otra cadena.  
  
 El nombre del funclet resultante puede ser demasiado largo y el compilador lo truncará y generará la advertencia C4788.  
  
 Para resolver esta advertencia, acorte el nombre de función original.  Si la función es un método o una función de plantilla de C\+\+, utilice una definición de tipos para parte del nombre.  Por ejemplo:  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 se puede reemplazar por:  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 Esta advertencia solo aparece en el compilador de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].