---
title: Identificadores en expresiones primarias | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e507c2b7c05f9ea818f55b10d222592fe0172cc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="identifiers-in-primary-expressions"></a>Identificadores en expresiones primarias
Los identificadores pueden ser de tipo entero, **float**, `enum`, `struct`, **union**, matriz, puntero o función. Un identificador es una expresión primaria siempre que se haya declarado como designación de un objeto (en cuyo caso es un valor L) o como una función (en cuyo caso es un designador de función). Vea [Expresiones de valor L y de valor R](../c-language/l-value-and-r-value-expressions.md) para ver una definición de valor L.  
  
 El valor de puntero representado por un identificador de matriz no es una variable, por lo que un identificador de matriz no puede formar el operando izquierdo de una operación de asignación y, por lo tanto, no es un valor L modificable.  
  
 Un identificador declarado como una función representa un puntero cuyo valor es la dirección de la función. El puntero se dirige a una función que devuelve un valor de un tipo especificado. Así, los identificadores de función tampoco pueden ser valores L en operaciones de asignación. Para obtener más información, vea [Identificadores](../c-language/c-identifiers.md).  
  
## <a name="see-also"></a>Vea también  
 [Expresiones primarias de C](../c-language/c-primary-expressions.md)