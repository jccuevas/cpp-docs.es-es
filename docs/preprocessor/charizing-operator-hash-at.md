---
title: "Operador de caracterización (#@) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: '#@'
dev_langs: C++
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 933e97732462b61919d9e5a1e73f2a72d26ea01b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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