---
title: Funciones de &lt;system_error&gt; | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: 78e39c11d58fddc6bc15d6c18257b43aa427b892
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ltsystemerrorgt-functions"></a>Funciones de &lt;system_error&gt;
||||  
|-|-|-|  
|[generic_category](#generic_category)|[make_error_code](#make_error_code)|[make_error_condition](#make_error_condition)|  
|[system_category](#system_category)|  
  
##  <a name="generic_category"></a>  generic_category  
 Representa la categoría de errores genéricos.  
  
```
extern const error_category& generic_category();
```  
  
### <a name="remarks"></a>Comentarios  
 El `generic_category` objeto es una implementación de [error_category](../standard-library/error-category-class.md).  
  
##  <a name="make_error_code"></a>  make_error_code  
 Crea un objeto de código de error.  
  
```
error_code make_error_code(generic_errno _Errno);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Errno`|El valor de enumeración que se va a almacenar en el objeto de código de error.|  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="make_error_condition"></a>  make_error_condition  
 Crea un objeto de la condición de error.  
  
```
error_condition make_error_condition(generic_errno _Errno);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Errno`|El valor de enumeración que se va a almacenar en el objeto de la condición de error.|  
  
### <a name="return-value"></a>Valor devuelto  
 El objeto de la condición de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="system_category"></a>  system_category  
 Representa la categoría de los errores causados por desbordamientos del sistema de bajo nivel.  
  
```
extern const error_category& system_category();
```  
  
### <a name="remarks"></a>Comentarios  
 El `system_category` objeto es una implementación de [error_category](../standard-library/error-category-class.md).  
  
## <a name="see-also"></a>Vea también  
 [<system_error>](../standard-library/system-error.md)



