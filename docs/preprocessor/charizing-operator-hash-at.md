---
title: "Operador de caracterización (#@) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#@'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a6521322e7a71d8e76b657fb8580157c036e881b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="charizing-operator-"></a>Operador de conversión a caracteres (#@)
**Específicos de Microsoft**  
  
 El operador charizing solo puede utilizarse con argumentos de macros. Si  **#@**  precede un parámetro formal en la definición de la macro, el argumento real es entre comillas simples y se interpreta como un carácter cuando se expande la macro. Por ejemplo:  
  
```  
#define makechar(x)  #@x  
```  
  
 hace que la instrucción  
  
```  
a = makechar(b);  
```  
  
 se expanda a  
  
```  
a = 'b';  
```  
  
 El carácter de comilla simple no se puede utilizar con el operador charizing.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)