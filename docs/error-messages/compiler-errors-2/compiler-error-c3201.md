---
title: "Error del compilador C3201 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3201"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3201"
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3201
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la lista de parámetros de plantilla de la plantilla de clase 'template' no coincide con la lista de parámetros de plantilla del parámetro de plantilla 'template'  
  
 Se pasó una plantilla de clase en el argumento a una plantilla de clase que no toma un parámetro de plantilla o se pasó un número de argumentos de plantilla para el argumento de plantilla predeterminado que no coinciden.  
  
```  
// C3201.cpp  
template<typename T1, typename T2>  
class X1  
{  
};  
  
template<template<typename T> class U = X1>   // C3201  
class X2  
{  
};  
  
template<template<typename T, typename V> class U = X1>   // OK  
class X3  
{  
};  
```