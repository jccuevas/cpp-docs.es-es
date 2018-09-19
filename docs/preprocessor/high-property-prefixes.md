---
title: high_property_prefixes | Microsoft Docs
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
ms.openlocfilehash: 2ce21958dbb928a29debe21fb7cfaed4b9036141
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539102"
---
# <a name="highpropertyprefixes"></a>high_property_prefixes
**Específicos de C++**  
  
Especifica los prefijos alternativos para tres métodos de propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
### <a name="parameters"></a>Parámetros  
*GetPrefix*  
Prefijo que se usará para el `propget` métodos.  
  
*PutPrefix*  
Prefijo que se usará para el `propput` métodos.  
  
*PutRefPrefix*  
Prefijo que se usará para el `propputref` métodos.  
  
## <a name="remarks"></a>Comentarios  
 
De forma predeterminada, control de errores de alto nivel `propget`, `propput`, y `propputref` métodos expuestos por funciones miembro denominadas con prefijos `Get`, `Put`, y `PutRef`, respectivamente.  
  
**FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 
[atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
[directiva #import](../preprocessor/hash-import-directive-cpp.md)