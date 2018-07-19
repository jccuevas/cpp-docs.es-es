---
title: Clase CAtlException | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlException
- ATLEXCEPT/ATL::CAtlException
- ATLEXCEPT/ATL::CAtlException::CAtlException
- ATLEXCEPT/ATL::CAtlException::m_hr
dev_langs:
- C++
helpviewer_keywords:
- CAtlException class
ms.assetid: 3fd7b041-f70d-4292-b947-0d70781d95a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aaafdf42d218e2c3bca1e8ee28c27898f80bcf40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357875"
---
# <a name="catlexception-class"></a>Clase CAtlException
Esta clase define una excepción de ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlException
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlException::CAtlException](#catlexception)|El constructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlException::operator HRESULT](#operator_hresult)|Convierte el objeto actual con un valor HRESULT.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|La variable de tipo HRESULT creado por el objeto y se usa para almacenar la condición de error.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CAtlException` objeto representa una condición de excepción relacionada con una operación de ATL. La `CAtlException` clase incluye un miembro de datos públicos que almacena el código de estado que indica el motivo de la excepción y un operador de conversión que permite tratar la excepción como si fuera un valor HRESULT.  
  
 En general, llamará `AtlThrow` en lugar de crear un `CAtlException` objeto directamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlexcept.h  
  
##  <a name="catlexception"></a>  CAtlException::CAtlException  
 El constructor.  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hr`  
 La `HRESULT` código de error.  
  
##  <a name="operator_hresult"></a>  CAtlException::operator HRESULT 
 Convierte el objeto actual con un valor HRESULT.  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>  CAtlException::m_hr  
 El `HRESULT` miembro de datos.  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>Comentarios  
 El miembro de datos que almacena la condición de error. El valor HRESULT se establece mediante el constructor, [CAtlException::CAtlException](#catlexception).  
  
## <a name="see-also"></a>Vea también  
 [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)   
 [Información general de clases](../../atl/atl-class-overview.md)
