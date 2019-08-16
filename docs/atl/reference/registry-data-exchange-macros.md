---
title: Macros de intercambio de datos del registro
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: 69b823cbcd85ebaaeb05979283ea4f8fea80f4b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197489"
---
# <a name="registry-data-exchange-macros"></a>Macros de intercambio de datos del registro

Estas macros realizan operaciones de intercambio de datos del registro.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Marca el principio de la asignación de intercambio de datos del registro.|
|[END_RDX_MAP](#end_rdx_map)|Marca el final de la asignación de intercambio de datos del registro.|
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del registro especificada a una variable de miembro especificado de tipo BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada del registro especificado con una variable de miembro especificado del tipo CString.|
|[RDX_DWORD](#rdx_dword)|Asocia la entrada del registro especificado con una variable de miembro especificado del tipo DWORD.|
|[RDX_TEXT](#rdx_text)|Asocia la entrada del registro especificado con una variable de miembro especificado del tipo TCHAR.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlplus.h

##  <a name="begin_rdx_map"></a>  BEGIN_RDX_MAP

Marca el principio de la asignación de intercambio de datos del registro.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Comentarios

Las macros siguientes se usan dentro de la asignación de intercambio de datos del registro para leer y escribir entradas del registro del sistema:

|Macro|Descripción|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del registro especificada a una variable de miembro especificado de tipo BYTE.|
|[RDX_DWORD](#rdx_dword)|Asocia la entrada del registro especificado con una variable de miembro especificado del tipo DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada del registro especificado con una variable de miembro especificado del tipo CString.|
|[RDX_TEXT](#rdx_text)|Asocia la entrada del registro especificado con una variable de miembro especificado del tipo TCHAR.|

La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o se debe usar la función de miembro del mismo nombre creado por las macros BEGIN_RDX_MAP y END_RDX_MAP, siempre que el código necesita intercambiar datos entre el registro del sistema y la variables especificadas en el mapa RDX.

##  <a name="end_rdx_map"></a>  END_RDX_MAP

Marca el final de la asignación de intercambio de datos del registro.

```
END_RDX_MAP
```

##  <a name="rdx_binary"></a>  RDX_BINARY

Asocia la entrada del registro especificada a una variable de miembro especificado de tipo BYTE.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parámetros

*rootkey*<br/>
La raíz de la clave del registro.

*subkey*<br/>
La subclave del registro.

*valuename*<br/>
La clave del registro.

*member*<br/>
La variable miembro para asociar a la entrada del registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable de miembro.

### <a name="remarks"></a>Comentarios

Esta macro se usa junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por las macros BEGIN_RDX_MAP y END_RDX_MAP, debe usarse para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.

##  <a name="rdx_cstring_text"></a>  RDX_CSTRING_TEXT

Asocia la entrada del registro especificado con una variable de miembro especificado del tipo CString.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parámetros

*rootkey*<br/>
La raíz de la clave del registro.

*subkey*<br/>
La subclave del registro.

*valuename*<br/>
La clave del registro.

*member*<br/>
La variable miembro para asociar a la entrada del registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable de miembro.

### <a name="remarks"></a>Comentarios

Esta macro se usa junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por las macros BEGIN_RDX_MAP y END_RDX_MAP, debe usarse para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.

##  <a name="rdx_dword"></a>  RDX_DWORD

Asocia la entrada del registro especificado con una variable de miembro especificado del tipo DWORD.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parámetros

*rootkey*<br/>
La raíz de la clave del registro.

*subkey*<br/>
La subclave del registro.

*valuename*<br/>
La clave del registro.

*member*<br/>
La variable miembro para asociar a la entrada del registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable de miembro.

### <a name="remarks"></a>Comentarios

Esta macro se usa junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por las macros BEGIN_RDX_MAP y END_RDX_MAP, debe usarse para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.

##  <a name="rdx_text"></a>  RDX_TEXT

Asocia la entrada del registro especificado con una variable de miembro especificado del tipo TCHAR.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>Parámetros

*rootkey*<br/>
La raíz de la clave del registro.

*subkey*<br/>
La subclave del registro.

*valuename*<br/>
La clave del registro.

*member*<br/>
La variable miembro para asociar a la entrada del registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable de miembro.

### <a name="remarks"></a>Comentarios

Esta macro se usa junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada del Registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función de miembro del mismo nombre creado por las macros BEGIN_RDX_MAP y END_RDX_MAP, debe usarse para realizar el intercambio de datos entre el registro del sistema y las variables de miembro en el mapa RDX.

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
