---
title: typeid reemplaza typeof | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 09ec4aef4c8bc68f8a808193b30d86b8519ba881
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="typeof-goes-to-ttypeid"></a>T::typeid reemplaza typeof
El `typeof` operador que se utiliza en extensiones administradas para C++ ha suplantado por el `typeid` palabra clave en Visual C++.  
  
 En extensiones administradas, el `__typeof()` operador devuelve asociado `Type*` objeto cuando se pasa el nombre de un tipo administrado. Por ejemplo:  
  
```  
// Creates and initializes a new Array instance.  
Array* myIntArray =   
   Array::CreateInstance( __typeof(Int32), 5 );  
```  
  
 En la nueva sintaxis, `__typeof` se ha reemplazado por un método adicional de `typeid` que devuelve un `Type^` cuando se especifica un tipo administrado.  
  
```  
// Creates and initializes a new Array instance.  
Array^ myIntArray =   
   Array::CreateInstance( Int32::typeid, 5 );  
```  
  
## <a name="see-also"></a>Vea también  
 [Cambios del lenguaje general (C++ / CLI)](../dotnet/general-language-changes-cpp-cli.md)   
 [typeid](../windows/typeid-cpp-component-extensions.md)