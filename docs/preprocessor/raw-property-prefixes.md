---
title: raw_property_prefixes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_property_prefixes
dev_langs: C++
helpviewer_keywords: raw_property_prefixes attribute
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 190a7ce7fbca4fea477771b5c125c96ecc187216
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="rawpropertyprefixes"></a>raw_property_prefixes
**Específicos de C++**  
  
 Especifica los prefijos alternativos para tres métodos de propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### <a name="parameters"></a>Parámetros  
 `GetPrefix`  
 Prefijo que se usará para la **propget** métodos.  
  
 `PutPrefix`  
 Prefijo que se usará para la **propput** métodos.  
  
 `PutRefPrefix`  
 Prefijo que se usará para la **propputref** métodos.  
  
## <a name="remarks"></a>Comentarios  
 De forma predeterminada, bajo nivel **propget**, **propput**, y **propputref** métodos expuestos por funciones miembro denominadas con los prefijos de **get_**, **put_**, y **putref_** respectivamente. Estos prefijos son compatibles con los nombres que se usan en los archivos de encabezado generados por MIDL.  
  
 **FIN de específicos de C++**  
  
## <a name="see-also"></a>Vea también  
 [atributos #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import (directiva)](../preprocessor/hash-import-directive-cpp.md)