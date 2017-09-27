---
title: "Interpretación del operador de subíndice | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator, interpretation of
- arrays [C++], subscripting
- interpreting subscript operators
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1a83ff6aea4380688d3b6298b93e04caab1dbb7f
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="interpretation-of-subscript-operator"></a>Interpretación del operador de subíndice
Al igual que otros operadores, el operador de subíndice (**[]**) pueden volver a definirse por el usuario. El comportamiento predeterminado del operador de subíndice, si no está sobrecargado, consiste en combinar el nombre de la matriz y el subíndice usando el método siguiente:  
  
 \*((*nombre de la matriz*) + (*subíndice*))  
  
 Como en toda suma que implica tipos de puntero, el ajuste de escala se realiza automáticamente para que se produzca el ajuste correspondiente al tamaño del tipo. Por lo tanto, el valor resultante no es *subíndice* bytes desde el origen de *nombre de la matriz*; en su lugar, es el *subíndice*elemento de la matriz. (Para obtener más información sobre esta conversión, consulte [operadores de suma](../cpp/additive-operators-plus-and.md).)  
  
 De igual forma, para las matrices multidimensionales, la dirección se deriva usando el método siguiente:  
  
 **((**   
 ***nombre de la matriz* ) + ()**   
 ***subíndice* 1***max*2 * \* max*3*...max*n) ** + ** *subíndice*2 * \* max*3*...max*n).   . . *+**subíndice*n))  
  
## <a name="see-also"></a>Vea también  
 [Matrices](../cpp/arrays-cpp.md)
