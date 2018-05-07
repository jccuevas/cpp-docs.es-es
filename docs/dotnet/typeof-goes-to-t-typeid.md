---
title: typeid reemplaza typeof | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0ae9f772a68735555748e6edbeb6196f1a73d2c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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