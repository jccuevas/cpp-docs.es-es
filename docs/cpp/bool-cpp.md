---
title: BOOL (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-language
ms.tgt_pltfrm: ''
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
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d5a8a86cfcc64b70e4910079461513c34fc7d0d
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/08/2018
---
# <a name="bool-c"></a>bool (C++)

Esta palabra clave es un tipo integrado. Una variable de este tipo puede tener valores [true](../cpp/true-cpp.md) y [false](../cpp/false-cpp.md). Las expresiones condicionales tienen el tipo `bool` y, por lo tanto, tienen valores de tipo `bool`. Por ejemplo, `i!=0` tiene ahora **true** o **false** dependiendo del valor de `i`.  

**Visual Studio 2017 15,3 y versiones posteriores** (disponible con [/std:c ++ 17](../build/reference/std-specify-language-standard-version.md)): el operando de un prefijo o postfijo de incremento o decremento operador no puede ser de tipo **bool**. En otras palabras, dada una variable **b** de tipo **bool**, ya no se permiten estas expresiones:

```cpp
    b++;
    ++b;
    b--;
    --b;
```
  
Los valores **true** y **false** tienen la relación siguiente:  
  
```cpp  
!false == true  
!true == false  
```  
  
En la instrucción siguiente:  
  
```cpp  
if (condexpr1) statement1;   
```  
  
Si `condexpr1` es **true**, `statement1` siempre se ejecuta; si `condexpr1` es **false**, `statement1` nunca se ejecuta.  
  
Cuando un prefijo o postfijo **++** operador se aplica a una variable de tipo **bool**, la variable se establece en **true**. 
**Visual Studio 2017 15,3 y versiones posteriores**: operador ++ para **bool** se ha quitado del lenguaje y ya no se admite.

El prefijo o postfijo **--** operador no se puede aplicar a una variable de este tipo.  
  
 El **bool** tipo participa en promociones enteras. Un valor r de tipo **bool** puede convertirse a un valor r de tipo **int**, con **false** como cero y **true** como uno. Como un tipo distinto, **bool** participa en la resolución de sobrecarga.  
  
## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Tipos fundamentales](../cpp/fundamental-types-cpp.md)<br/>
