---
title: Error de compilador C3202 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3202
dev_langs:
- C++
helpviewer_keywords:
- C3202
ms.assetid: 23528a0c-5493-4804-9789-cd3c38e49fb9
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: a8a7e280b7e1b6a7e53088df9d1cfd283cc4d93e
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3202"></a>Error de compilador C3202
'nombre argumento' : argumento predeterminado no válido para el parámetro de plantilla 'parámetro'; se esperaba una plantilla de clase.  
  
 Se pasó un argumento predeterminado no válido para un parámetro de plantilla.  
  
 El ejemplo siguiente genera la advertencia C3202:  
  
```  
// C3202.cpp  
template<typename T>  
class X  
{  
};  
  
class Z  
{  
};  
  
template<template<typename U> class T1 = Z, typename T2> // C3202  
class Y  
{  
};  
```
