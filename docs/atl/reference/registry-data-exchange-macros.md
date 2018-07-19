---
title: Macros de intercambio de datos de registro | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 62a26e8d602010ce637114464a844d2f95e635c9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32363063"
---
# <a name="registry-data-exchange-macros"></a>Macros de intercambio de datos del registro
Estas macros realizan operaciones de intercambio de datos del registro.  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|Marca el principio de la asignación de intercambio de datos del registro.|  
|[END_RDX_MAP](#end_rdx_map)|Marca el final de la asignación de intercambio de datos del registro.|  
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo BYTE.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada del registro especificada con una variable de miembro especificado del tipo CString.|  
|[RDX_DWORD](#rdx_dword)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo DWORD.|  
|[RDX_TEXT](#rdx_text)|Asocia la entrada del registro especificada con una variable de miembro especificado del tipo TCHAR.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlplus.h  
   
##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP  
 Marca el principio de la asignación de intercambio de datos del registro.  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>Comentarios  
 Las macros siguientes se utilizan dentro de la asignación de intercambio de datos del registro para leer y escribir entradas en el registro del sistema:  
  
|Macro|Descripción|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo BYTE.|  
|[RDX_DWORD](#rdx_dword)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo DWORD.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada del registro especificada con una variable de miembro especificado del tipo CString.|  
|[RDX_TEXT](#rdx_text)|Asocia la entrada del registro especificada con una variable de miembro especificado del tipo TCHAR.|  
  
 La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, debe utilizarse siempre que el código necesita intercambiar datos entre el registro del sistema y la variables especificadas en la asignación RDX.  
  
##  <a name="end_rdx_map"></a>  END_RDX_MAP  
 Marca el final de la asignación de intercambio de datos del registro.  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>  RDX_BINARY  
 Asocia la entrada del registro especificada con una variable de miembro especificado de tipo BYTE.  
  
```
RDX_BINARY(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parámetros  
 `rootkey`  
 La raíz de la clave del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable de miembro para asociar a la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable de miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se usa junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable de miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y el miembro variables en el mapa RDX.  
  
##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT  
 Asocia la entrada del registro especificada con una variable de miembro especificado del tipo CString.  
  
```
RDX_CSTRING_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parámetros  
 `rootkey`  
 La raíz de la clave del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable de miembro para asociar a la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable de miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se usa junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable de miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y el miembro variables en el mapa RDX.  
  
##  <a name="rdx_dword"></a>  RDX_DWORD  
 Asocia la entrada del registro especificada con una variable de miembro especificado de tipo DWORD.  
  
```
RDX_DWORD(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parámetros  
 `rootkey`  
 La raíz de la clave del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable de miembro para asociar a la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable de miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se usa junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable de miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y el miembro variables en el mapa RDX.  
  
##  <a name="rdx_text"></a>  RDX_TEXT  
 Asocia la entrada del registro especificada con una variable de miembro especificado del tipo TCHAR.  
  
```
RDX_TEXT(
    rootkey, 
    subkey, 
    valuename, 
    member, 
    member_size )
```  
  
### <a name="parameters"></a>Parámetros  
 `rootkey`  
 La raíz de la clave del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable de miembro para asociar a la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable de miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se usa junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable de miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y el miembro variables en el mapa RDX.  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)







