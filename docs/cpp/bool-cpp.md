---
title: BOOL (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2af648b2b93d2d01eaf66f5b642b6514063577d6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32410868"
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
