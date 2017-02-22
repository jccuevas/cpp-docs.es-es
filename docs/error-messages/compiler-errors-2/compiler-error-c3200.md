---
title: "Error del compilador C3200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3200"
ms.assetid: 44bb5e77-f0ec-421c-a732-b9ee7c0a3529
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'plantilla' : argumento de plantilla no válido para el parámetro de plantilla 'parámetro'; se esperaba una plantilla de clase  
  
 Se pasó un argumento no válido a una plantilla de clase.  La plantilla de clase espera una plantilla como parámetro.  En el siguiente ejemplo, al llamar a `Y<int, int> aY`, se generará el error C3200.  El primer parámetro tiene que ser una plantilla como, por ejemplo, `Y<X, int> aY`.  
  
```  
// C3200.cpp  
template<typename T>  
class X  
{  
};  
  
template<template<typename U> class T1, typename T2>  
class Y  
{  
};  
  
int main()  
{  
   Y<int, int> y;   // C3200  
}  
```