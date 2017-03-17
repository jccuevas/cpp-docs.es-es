---
title: Clase CAtlException | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 30c9235f16581c86ab5612522909dc366b1ce17e
ms.lasthandoff: 02/24/2017

---
# <a name="catlexception-class"></a>Clase CAtlException
Esta clase define una excepción de ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlException
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlException::CAtlException](#catlexception)|El constructor.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlException::operator HRESULT](#operator_hresult)|Convierte el objeto actual con un valor HRESULT.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlException::m_hr](#m_hr)|La variable de tipo HRESULT creado por el objeto y se utiliza para almacenar la condición de error.|  
  
## <a name="remarks"></a>Comentarios  
 Un `CAtlException` objeto representa una condición de excepción relacionada con una operación de ATL. La `CAtlException` clase incluye un miembro de datos públicos que almacena el código de estado que indica el motivo de la excepción y un operador de conversión que permite tratar la excepción como si fuese un HRESULT.  
  
 En general, llamará `AtlThrow` en lugar de crear un `CAtlException` objeto directamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlexcept.h  
  
##  <a name="catlexception"></a>CAtlException::CAtlException  
 El constructor.  
  
```
CAtlException(HRESULT hr) throw();
CAtlException() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hr`  
 La `HRESULT` código de error.  
  
##  <a name="operator_hresult"></a>CAtlException::operator HRESULT 
 Convierte el objeto actual con un valor HRESULT.  
  
```  
operator HRESULT() const throw ();
```  
  
##  <a name="m_hr"></a>CAtlException::m_hr  
 El `HRESULT` miembro de datos.  
  
```
HRESULT m_hr;
```  
  
### <a name="remarks"></a>Comentarios  
 El miembro de datos que almacena la condición de error. El constructor establece el valor HRESULT [CAtlException::CAtlException](#catlexception).  
  
## <a name="see-also"></a>Vea también  
 [AtlThrow](http://msdn.microsoft.com/library/2bd111da-8170-488d-914a-c9bf6b6765f7)   
 [Información general de la clase](../../atl/atl-class-overview.md)

