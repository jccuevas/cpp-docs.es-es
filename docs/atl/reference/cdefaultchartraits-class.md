---
title: Clase CDefaultCharTraits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits
- ATLCOLL/ATL::CDefaultCharTraits::CharToLower
- ATLCOLL/ATL::CDefaultCharTraits::CharToUpper
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCharTraits class
ms.assetid: f94a3934-597f-401d-8513-ed6924ae069a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 24aa01ec29f063c1fa65ebe24c707deb1ea58556
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cdefaultchartraits-class"></a>Clase CDefaultCharTraits
Esta clase proporciona dos funciones estáticas para convertir los caracteres entre mayúsculas y minúsculas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CDefaultCharTraits
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDefaultCharTraits::CharToLower](#chartolower)|(Estático) Llame a esta función para convertir un carácter a mayúsculas.|  
|[CDefaultCharTraits::CharToUpper](#chartoupper)|(Estático) Llame a esta función para convertir un carácter a minúsculas.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones que se utilizan por la clase [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="chartolower"></a>  CDefaultCharTraits::CharToLower  
 Llame a esta función para convertir un carácter a minúsculas.  
  
```
static wchar_t CharToLower(wchar_t x);  
static char CharToLower(char x);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Carácter que se va a convertir en minúsculas.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#132](../../atl/codesnippet/cpp/cdefaultchartraits-class_1.cpp)]  
  
##  <a name="chartoupper"></a>  CDefaultCharTraits::CharToUpper  
 Llame a esta función para convertir un carácter a mayúsculas.  
  
```
static wchar_t CharToUpper(wchar_t x);  
static char CharToUpper(char x);
```  
  
### <a name="parameters"></a>Parámetros  
 *x*  
 Carácter que se va a convertir en mayúsculas.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)
