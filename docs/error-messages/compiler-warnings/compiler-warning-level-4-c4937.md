---
title: "Advertencia del compilador (nivel 4) C4937 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4937"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4937"
ms.assetid: 2bb9f0e7-bbd6-4697-84de-95955e32ae29
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4937
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'texto1' y 'texto2' no se pueden distinguir como argumentos para 'directiva'  
  
 Debido a la forma en que el compilador procesa argumentos para directivas, no es posible distinguir los nombres que tienen un significado para el compilador como, por ejemplo, palabras clave con varias representaciones de texto \(en formato de subrayado simple y doble\).  
  
 Algunos ejemplos de cadenas de este tipo son \_\_cdecl y \_\_forceinline.  Tenga en cuenta que con \/Za solo se habilita el formato de subrayado doble.  
  
 El ejemplo siguiente genera la advertencia C4937:  
  
```  
// C4937.cpp // compile with: /openmp /W4 #include "omp.h" int main() { #pragma omp critical ( __leave )   // C4937 ; // OK #pragma omp critical ( leave ) ; }  
```