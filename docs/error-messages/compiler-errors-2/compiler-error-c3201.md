---
title: Error del compilador C3201 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3201
dev_langs:
- C++
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51ebf253a1d1e5963ff05aa343295e133a0641c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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