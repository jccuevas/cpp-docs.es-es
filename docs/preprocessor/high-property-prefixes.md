---
title: high_property_prefixes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7df4ef6cded98c19ead86160aa772e349ebfd37
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**C++ Specific**  
  
 Especifica los prefijos alternativos para tres métodos de propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `GetPrefix`  
 Prefijo que se usará para la **propget** métodos.  
  
 `PutPrefix`  
 Prefijo que se usará para la **propput** métodos.  
  
 `PutRefPrefix`  
 Prefijo que se usará para la **propputref** métodos.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, control de errores de alto nivel **propget**, **propput**, y **propputref** métodos expuestos por funciones miembro denominadas con prefijos **obtener** , `Put`, y **PutRef**, respectivamente.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)