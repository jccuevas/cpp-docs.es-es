---
title: Error del compilador C3201 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3201
dev_langs:
- C++
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c398d3251c63a763af0fdf965e4c7f2e8c5bb3c4
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3201"></a>Error del compilador C3201
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
