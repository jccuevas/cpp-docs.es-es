---
title: "Error del compilador C3038 | Microsoft Docs"
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
  - "C3038"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3038"
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3038
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': la variable de la cláusula 'private' no puede ser una variable de reducción en el contexto envolvente  
  
 Las variables que aparecen en la cláusula [reduction](../../parallel/openmp/reference/reduction.md) de una directiva paralela no pueden especificarse en una cláusula [private](../../parallel/openmp/reference/private-openmp.md) en una directiva de uso compartido que se enlaza a la construcción paralela.  
  
 El ejemplo siguiente genera la advertencia C3038:  
  
```  
// C3038.cpp // compile with: /openmp /c int g_i, g_i2; int main() { int i; #pragma omp parallel reduction(+: g_i) { #pragma omp for private(g_i)   // C3038 // try the following line instead // #pragma omp for private(g_i2) for (i = 0; i < 10; ++i) g_i += i; } }  
```