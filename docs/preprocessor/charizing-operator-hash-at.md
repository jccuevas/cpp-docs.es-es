---
title: Operador de caracterización (#@) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9e0c0d140d937b7359ff3abf9c0eae145a89210
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33912737"
---
# <a name="charizing-operator-"></a>Operador de conversión a caracteres (#@)
**Específicos de Microsoft**  
  
 El operador charizing solo puede utilizarse con argumentos de macros. Si **#@** precede un parámetro formal en la definición de la macro, el argumento real es entre comillas simples y se interpreta como un carácter cuando se expande la macro. Por ejemplo:  
  
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