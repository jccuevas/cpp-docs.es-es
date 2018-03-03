---
title: BOOL (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
dev_langs:
- C++
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 564d2f4849d1725d46d92562e2ce75b2ea2e2d44
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="bool-c"></a>bool (C++)
Esta palabra clave es un tipo integrado. Una variable de este tipo puede tener valores [true](../cpp/true-cpp.md) y [false](../cpp/false-cpp.md). Las expresiones condicionales tienen el tipo `bool` y, por lo tanto, tienen valores de tipo `bool`. Por ejemplo, `i!=0` tiene ahora **true** o **false** dependiendo del valor de `i`.  

**Visual Studio 2017 15,3 y versiones posteriores** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): el operando de un prefijo o postfijo de incremento o decremento operador no puede ser de tipo `bool`. 
  
 Los valores **true** y **false** tienen la relación siguiente:  
  
```  
!false == true  
!true == false  
```  
  
 En la instrucción siguiente:  
  
```  
if (condexpr1) statement1;   
```  
  
 Si `condexpr1` es **true**, `statement1` siempre se ejecuta; si `condexpr1` es **false**, `statement1` nunca se ejecuta.  
  
 Cuando un prefijo o postfijo `++` operador se aplica a una variable de tipo `bool`, la variable se establece en **true**. 
**Visual Studio 2017 15,3 y versiones posteriores**: operador ++ para el tipo bool se ha quitado del lenguaje y ya no se admite.

El operador `--` de prefijo o de postfijo no se puede aplicar a una variable de este tipo.  
  
 El tipo `bool` participa en promociones enteras. Un valor r de tipo `bool` puede convertirse a un valor r de tipo `int`, con **false** como cero y **true** como uno. Como un tipo distinto, `bool` participa en la resolución de sobrecarga.  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Tipos fundamentales](../cpp/fundamental-types-cpp.md)