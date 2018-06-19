---
title: high_property_prefixes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- high_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- high_property_prefixes attribute
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7269301fed3892fbf4b7cf6427bacb82d9712ef7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33849394"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**Específicos de C++**  
  
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