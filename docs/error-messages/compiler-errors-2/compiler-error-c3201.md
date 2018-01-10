---
title: Error del compilador C3201 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3201
dev_langs: C++
helpviewer_keywords: C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a2bcae07f4e66fec1ed6fb9eb95e87e83557e53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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