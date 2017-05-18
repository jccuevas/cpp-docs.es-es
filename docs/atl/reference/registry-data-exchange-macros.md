---
title: Macros de intercambio de datos de registro | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: ee3c1d639ee4a6c6bd6cf26a8c59bb1a37a4fa02
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="registry-data-exchange-macros"></a>Macros de intercambio de datos de registro
Estas macros realizan operaciones de intercambio de datos de registro.  
  
|||  
|-|-|  
|[BEGIN_RDX_MAP](#begin_rdx_map)|Marca el comienzo de la asignación de intercambio de datos de registro.|  
|[END_RDX_MAP](#end_rdx_map)|Marca el final de la asignación de intercambio de datos de registro.|  
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo BYTE.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo CString.|  
|[RDX_DWORD](#rdx_dword)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo DWORD.|  
|[RDX_TEXT](#rdx_text)|Asocia la entrada del registro especificada con una variable de miembro especificado del tipo TCHAR.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlplus.h  
   
##  <a name="begin_rdx_map"></a>BEGIN_RDX_MAP  
 Marca el comienzo de la asignación de intercambio de datos de registro.  
  
```
BEGIN_RDX_MAP
```  
  
### <a name="remarks"></a>Comentarios  
 Las macros siguientes se utilizan dentro del mapa de intercambio de datos del registro para leer y escribir entradas del registro del sistema:  
  
|Macro|Descripción|  
|-----------|-----------------|  
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo BYTE.|  
|[RDX_DWORD](#rdx_dword)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo DWORD.|  
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada del registro especificada con una variable de miembro especificado de tipo CString.|  
|[RDX_TEXT](#rdx_text)|Asocia la entrada del registro especificada con una variable de miembro especificado del tipo TCHAR.|  
  
 La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, debe utilizarse siempre que el código necesita intercambiar datos entre el registro del sistema y las variables especificadas en la asignación RDX.  
  
##  <a name="end_rdx_map"></a>END_RDX_MAP  
 Marca el final de la asignación de intercambio de datos de registro.  
  
```
END_RDX_MAP
```  
  
##  <a name="rdx_binary"></a>RDX_BINARY  
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
 La clave raíz del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable miembro para asociar con la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se utiliza junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.  
  
##  <a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT  
 Asocia la entrada del registro especificada con una variable de miembro especificado de tipo CString.  
  
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
 La clave raíz del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable miembro para asociar con la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se utiliza junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.  
  
##  <a name="rdx_dword"></a>RDX_DWORD  
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
 La clave raíz del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable miembro para asociar con la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se utiliza junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.  
  
##  <a name="rdx_text"></a>RDX_TEXT  
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
 La clave raíz del registro.  
  
 `subkey`  
 La subclave del registro.  
  
 `valuename`  
 La clave del registro.  
  
 `member`  
 La variable miembro para asociar con la entrada del registro especificada.  
  
 `member_size`  
 El tamaño, en bytes, de la variable miembro.  
  
### <a name="remarks"></a>Comentarios  
 Esta macro se utiliza junto con el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por el `BEGIN_RDX_MAP` y `END_RDX_MAP` macros, se debe usar para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.  
  
## <a name="see-also"></a>Vea también  
 [Macros](../../atl/reference/atl-macros.md)   
 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)








