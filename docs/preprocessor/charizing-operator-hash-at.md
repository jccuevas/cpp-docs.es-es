---
title: Operador de caracterización (#@) | Microsoft Docs
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
ms.openlocfilehash: c6aa18936497f0415da331697aceb26f26345500
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538714"
---
# <a name="charizing-operator-"></a>Operador de conversión a caracteres (#@)
**Específicos de Microsoft**  
  
El operador charizing solo puede utilizarse con argumentos de macros. Si `#@` precede a un parámetro formal en la definición de la macro, el argumento real está entre comillas simples y se tratan como un carácter cuando se expande la macro. Por ejemplo:  
  
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