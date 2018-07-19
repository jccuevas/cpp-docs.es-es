---
title: Información de tipo de tiempo de ejecución | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 14eafc1ebb50faaffb4c0a95e0cc929c89fb7c0b
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2018
ms.locfileid: "37938920"
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
  
     Utilizado para almacenar la información de tipo devuelta por la **typeid** operador.  
  
## <a name="see-also"></a>Vea también  
 [Conversión](../cpp/casting.md)