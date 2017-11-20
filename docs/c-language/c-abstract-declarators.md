---
title: Declaraciones abstractas de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ae6f7ca131e30c179d556e225600243500ae9379
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-abstract-declarators"></a>Declaraciones abstractas de C
Un declarador abstracto es un declarador sin identificador, que consta de uno o más modificadores de puntero, matriz o función. El modificador de puntero (**\***) precede siempre al identificador en un declarador; los modificadores de matriz (**[ ]**) y los modificadores de función ( **( )** ) van detrás del identificador. Teniendo esto en cuenta, puede determinar dónde aparecería el identificador en un declarador abstracto e interpretar el declarador en consecuencia. Vea [Interpretación de declaradores más complejos](../c-language/interpreting-more-complex-declarators.md) para obtener información adicional y ejemplos de declaradores complejos. Normalmente, puede usarse `typedef` para simplificar los declaradores. Vea [Declaraciones typedef](../c-language/typedef-declarations.md).  
  
 Los declaradores abstractos pueden ser complejos. Los paréntesis en un declarador abstracto complejo especifican una interpretación concreta, del mismo modo que en los declaradores complejos de las declaraciones.  
  
 En estos ejemplos se muestran declaradores abstractos:  
  
```  
int *         // The type name for a pointer to type int:  
  
int *[3]      // An array of three pointers to int  
  
int (*) [5]   // A pointer to an array of five int  
  
int *()       // A function with no parameter specification  
              // returning a pointer to int  
  
// A pointer to a function taking no arguments and   
// returning an int  
  
int (*) ( void )    
  
// An array of an unspecified number of constant pointers to   
// functions each with one parameter that has type unsigned int   
// and an unspecified number of other parameters returning an int   
  
int (*const []) ( unsigned int, ... )  
```  
  
> [!NOTE]
>  El declarador abstracto que consta de un conjunto de paréntesis vacíos, **( )**, no se permite porque es ambiguo. No se puede determinar si el identificador implícito va dentro de los paréntesis (en cuyo caso será un tipo sin modificar) o delante de los paréntesis (en cuyo caso será un tipo de función).  
  
## <a name="see-also"></a>Vea también  
 [Declaradores y declaraciones de variables](../c-language/declarators-and-variable-declarations.md)