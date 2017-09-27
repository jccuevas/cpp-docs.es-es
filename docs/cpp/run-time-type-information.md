---
title: "Información de tipo de tiempo de ejecución | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: 6
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
ms.openlocfilehash: ec36acfdba274a0eaf36c099da11f4462f2aad70
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="run-time-type-information"></a>Información de tipos en tiempo de ejecución
La información de tipo en tiempo de ejecución (RTTI) es un mecanismo que permite determinar el tipo de un objeto durante la ejecución del programa. RTTI se agregó al lenguaje C++ porque muchos proveedores de bibliotecas de clases implementaban esta funcionalidad por sí mismos. Esto produjo incompatibilidades entre las bibliotecas. Por tanto, se hizo obvio que se necesitaba compatibilidad para información de tipo en tiempo de ejecución en el nivel de lenguaje.  
  
 Por razones de claridad, esta discusión de RTTI se limita casi totalmente a punteros. Sin embargo, los conceptos discutidos también se aplican a referencias.  
  
 Hay tres elementos principales del lenguaje C++ para la información en tiempo de ejecución:  
  
-   El [dynamic_cast](../cpp/dynamic-cast-operator.md) operador.  
  
     Se usa para la conversión de tipos polimórficos.  
  
-   El [typeid](../cpp/typeid-operator.md) operador.  
  
     Se utiliza para identificar el tipo exacto de un objeto.  
  
-   El [type_info](../cpp/type-info-class.md) clase.  
  
     Se usa para contener la información de tipo devuelta por el operador `typeid`.  
  
## <a name="see-also"></a>Vea también  
 [Conversión](../cpp/casting.md)
