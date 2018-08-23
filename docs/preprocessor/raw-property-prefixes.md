---
title: raw_property_prefixes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- raw_property_prefixes
dev_langs:
- C++
helpviewer_keywords:
- raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 423a66b698f4e421ff29e6ac3dfddd11fa11c58f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42538900"
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**Específicos de C++**  
  
Especifica los prefijos alternativos para tres métodos de propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>Parámetros  
*GetPrefix*  
Prefijo que se usará para el `propget` métodos.  
  
*PutPrefix*  
Prefijo que se usará para el `propput` métodos.  
  
*PutRefPrefix*  
Prefijo que se usará para el `propputref` métodos.  
  
## <a name="remarks"></a>Comentarios  
 
De forma predeterminada, de bajo nivel `propget`, `propput`, y `propputref` métodos expuestos por funciones miembro denominadas con prefijos de **get_**, **put_**, y **putref_** respectivamente. Estos prefijos son compatibles con los nombres que se usan en los archivos de encabezado generados por MIDL.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
[directiva #import](../preprocessor/hash-import-directive-cpp.md)