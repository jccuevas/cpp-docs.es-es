---
title: "Error del compilador C3030 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3030"
ms.assetid: de92fd7e-29ba-46e8-b43b-f4b985cd74de
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': la variable de la cláusula o directiva 'reduction' no puede tener tipo de referencia  
  
 Solo puede pasar parámetros de valor a algunas cláusulas, como la cláusula de reducción.  
  
 El ejemplo siguiente genera la advertencia C3030:  
  
```  
// C3030.cpp // compile with: /openmp /link vcomps.lib #include "omp.h" void test(int &r) { #pragma omp parallel reduction(+ : r)   // C3030 ; } void test2(int r) { #pragma omp parallel reduction(+ : r)   // OK ; } int main(int argc, char** argv) { int& r = *((int*)argv); int s = *((int*)argv); #pragma omp parallel reduction(+ : r)   // C3030 ; #pragma omp parallel reduction(+ : s)   // OK ; }  
```