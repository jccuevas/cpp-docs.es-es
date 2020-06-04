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
ms.openlocfilehash: a7d580e4907cec40f97c0cead616665fff7b8a01
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326067"
---
# <a name="registry-data-exchange-macros"></a>Macros de intercambio de datos del registro

Estas macros realizan operaciones de intercambio de datos del Registro.

|||
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|Marca el principio del mapa de intercambio de datos del Registro.|
|[END_RDX_MAP](#end_rdx_map)|Marca el final de la asignación de intercambio de datos del Registro.|
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del Registro especificada con una variable miembro especificada de tipo BYTE.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada de registro especificada con una variable miembro especificada de tipo CString.|
|[RDX_DWORD](#rdx_dword)|Asocia la entrada de registro especificada con una variable miembro especificada de tipo DWORD.|
|[RDX_TEXT](#rdx_text)|Asocia la entrada de registro especificada con una variable miembro especificada de tipo TCHAR.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlplus.h

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a>BEGIN_RDX_MAP

Marca el principio del mapa de intercambio de datos del Registro.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>Observaciones

Las siguientes macros se utilizan en la asignación de intercambio de datos del Registro para leer y escribir entradas en el registro del sistema:

|Macro|Descripción|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|Asocia la entrada del Registro especificada con una variable miembro especificada de tipo BYTE.|
|[RDX_DWORD](#rdx_dword)|Asocia la entrada de registro especificada con una variable miembro especificada de tipo DWORD.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|Asocia la entrada de registro especificada con una variable miembro especificada de tipo CString.|
|[RDX_TEXT](#rdx_text)|Asocia la entrada de registro especificada con una variable miembro especificada de tipo TCHAR.|

La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función miembro del mismo nombre creada por las macros BEGIN_RDX_MAP y END_RDX_MAP, se debe usar siempre que el código necesite intercambiar datos entre el registro del sistema y las variables especificadas en el mapa RDX.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a>END_RDX_MAP

Marca el final de la asignación de intercambio de datos del Registro.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a>RDX_BINARY

Asocia la entrada del Registro especificada con una variable miembro especificada de tipo BYTE.

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
La raíz de la clave del Registro.

*Subclave*<br/>
La subclave del Registro.

*nombrevalor*<br/>
La clave del Registro.

*Miembro*<br/>
La variable miembro que se va a asociar a la entrada del Registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable miembro.

### <a name="remarks"></a>Observaciones

Esta macro se utiliza junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada de registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función miembro del mismo nombre creada por las macros BEGIN_RDX_MAP y END_RDX_MAP, se debe utilizar para realizar el intercambio de datos entre el registro del sistema y las variables miembro en el mapa RDX.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a>RDX_CSTRING_TEXT

Asocia la entrada de registro especificada con una variable miembro especificada de tipo CString.

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
La raíz de la clave del Registro.

*Subclave*<br/>
La subclave del Registro.

*nombrevalor*<br/>
La clave del Registro.

*Miembro*<br/>
La variable miembro que se va a asociar a la entrada del Registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable miembro.

### <a name="remarks"></a>Observaciones

Esta macro se utiliza junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada de registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función miembro del mismo nombre creada por las macros BEGIN_RDX_MAP y END_RDX_MAP, se debe utilizar para realizar el intercambio de datos entre el registro del sistema y las variables miembro en el mapa RDX.

## <a name="rdx_dword"></a><a name="rdx_dword"></a>RDX_DWORD

Asocia la entrada de registro especificada con una variable miembro especificada de tipo DWORD.

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
La raíz de la clave del Registro.

*Subclave*<br/>
La subclave del Registro.

*nombrevalor*<br/>
La clave del Registro.

*Miembro*<br/>
La variable miembro que se va a asociar a la entrada del Registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable miembro.

### <a name="remarks"></a>Observaciones

Esta macro se utiliza junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada de registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función miembro del mismo nombre creada por las macros BEGIN_RDX_MAP y END_RDX_MAP, se debe utilizar para realizar el intercambio de datos entre el registro del sistema y las variables miembro en el mapa RDX.

## <a name="rdx_text"></a><a name="rdx_text"></a>RDX_TEXT

Asocia la entrada de registro especificada con una variable miembro especificada de tipo TCHAR.

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
La raíz de la clave del Registro.

*Subclave*<br/>
La subclave del Registro.

*nombrevalor*<br/>
La clave del Registro.

*Miembro*<br/>
La variable miembro que se va a asociar a la entrada del Registro especificada.

*member_size*<br/>
El tamaño, en bytes, de la variable miembro.

### <a name="remarks"></a>Observaciones

Esta macro se utiliza junto con las macros BEGIN_RDX_MAP y END_RDX_MAP para asociar una variable miembro a una entrada de registro determinada. La función global [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange), o la función miembro del mismo nombre creada por las macros BEGIN_RDX_MAP y END_RDX_MAP, se debe utilizar para realizar el intercambio de datos entre el registro del sistema y las variables miembro en el mapa RDX.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
