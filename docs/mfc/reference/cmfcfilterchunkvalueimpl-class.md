---
title: Clase CMFCFilterChunkValueImpl
ms.date: 11/04/2016
f1_keywords:
- CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl
- AFXWIN/CMFCFilterChunkValueImpl::Clear
- AFXWIN/CMFCFilterChunkValueImpl::CopyChunk
- AFXWIN/CMFCFilterChunkValueImpl::CopyFrom
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkGUID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkPID
- AFXWIN/CMFCFilterChunkValueImpl::GetChunkType
- AFXWIN/CMFCFilterChunkValueImpl::GetString
- AFXWIN/CMFCFilterChunkValueImpl::GetValue
- AFXWIN/CMFCFilterChunkValueImpl::GetValueNoAlloc
- AFXWIN/CMFCFilterChunkValueImpl::IsValid
- AFXWIN/CMFCFilterChunkValueImpl::SetBoolValue
- AFXWIN/CMFCFilterChunkValueImpl::SetDwordValue
- AFXWIN/CMFCFilterChunkValueImpl::SetFileTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetInt64Value
- AFXWIN/CMFCFilterChunkValueImpl::SetIntValue
- AFXWIN/CMFCFilterChunkValueImpl::SetLongValue
- AFXWIN/CMFCFilterChunkValueImpl::SetSystemTimeValue
- AFXWIN/CMFCFilterChunkValueImpl::SetTextValue
- AFXWIN/CMFCFilterChunkValueImpl::SetChunk
helpviewer_keywords:
- CMFCFilterChunkValueImpl [MFC], CMFCFilterChunkValueImpl
- CMFCFilterChunkValueImpl [MFC], Clear
- CMFCFilterChunkValueImpl [MFC], CopyChunk
- CMFCFilterChunkValueImpl [MFC], CopyFrom
- CMFCFilterChunkValueImpl [MFC], GetChunkGUID
- CMFCFilterChunkValueImpl [MFC], GetChunkPID
- CMFCFilterChunkValueImpl [MFC], GetChunkType
- CMFCFilterChunkValueImpl [MFC], GetString
- CMFCFilterChunkValueImpl [MFC], GetValue
- CMFCFilterChunkValueImpl [MFC], GetValueNoAlloc
- CMFCFilterChunkValueImpl [MFC], IsValid
- CMFCFilterChunkValueImpl [MFC], SetBoolValue
- CMFCFilterChunkValueImpl [MFC], SetDwordValue
- CMFCFilterChunkValueImpl [MFC], SetFileTimeValue
- CMFCFilterChunkValueImpl [MFC], SetInt64Value
- CMFCFilterChunkValueImpl [MFC], SetIntValue
- CMFCFilterChunkValueImpl [MFC], SetLongValue
- CMFCFilterChunkValueImpl [MFC], SetSystemTimeValue
- CMFCFilterChunkValueImpl [MFC], SetTextValue
- CMFCFilterChunkValueImpl [MFC], SetChunk
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
ms.openlocfilehash: 2c90a873033516710077d31c8bb8af5fb5172ca6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367509"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>Clase CMFCFilterChunkValueImpl

Se trata de una clase que simplifica la lógica de par de valores de propiedad y fragmentos.

## <a name="syntax"></a>Sintaxis

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::-CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Destruye el objeto.|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Construye el objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clear](#clear)|Borra el ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Copia este fragmento en una estructura que describe las características de un fragmento.|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicializa este valor de fragmento desde el otro valor.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Recupera el GUID del fragmento.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Recupera el fragmento PID (identificador de propiedad).|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Obtiene el tipo de fragmento.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Recupera el valor de cadena.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Recupera el valor como una propvariante asignada.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Devuelve el valor no asignado (valor interno).|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Comprueba si este valor de propiedad es válido o no.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Sobrecargado. Establece la propiedad por clave en un valor booleano.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Establece la propiedad por clave en un DWORD.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Establece la propiedad por clave en un archivotime.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Establece la propiedad por clave en un int64.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Establece la propiedad por clave en un int.|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Establece la propiedad por clave en LONG.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Establece la propiedad por clave en un SystemTime.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Establece la propiedad por clave en una cadena Unicode.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Función auxiliar que establece las propiedades comunes del fragmento.|

## <a name="remarks"></a>Observaciones

Para usar, simplemente cree una clase CMFCFilterChunkValueImpl del tipo correcto

Ejemplo:

CMFCFilterChunkValueImpl chunk;

hr á trozo. SetBoolValue(PKEY_IsAttachment, true);

or

hr á trozo. SetFileTimeValue(PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFCFilterChunkValueImpl::Clear

Borra el ChunkValue.

```
void Clear();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Construye el objeto.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::-CMFCFilterChunkValueImpl

Destruye el objeto.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk

Copia este fragmento en una estructura que describe las características de un fragmento.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Parámetros

*pStatChunk*<br/>
Puntero al valor de destino que describe las características del fragmento.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFCFilterChunkValueImpl::CopyFrom

Inicializa este valor de fragmento desde el otro valor.

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Especifica el valor de origen desde el que se va a copiar.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID

Recupera el GUID del fragmento.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia a un GUID que identifica el fragmento.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID

Recupera el fragmento PID (identificador de propiedad).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene el identificador de propiedad.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType

Recupera el tipo de fragmento.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor enumerado CHUNKSTATE, que especifica si el fragmento actual es una propiedad de tipo de texto o una propiedad de tipo de valor.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFCFilterChunkValueImpl::GetString

Recupera el valor de cadena.

```
CString &GetString();
```

### <a name="return-value"></a>Valor devuelto

Cadena que contiene el valor del fragmento.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue

Recupera el valor como una propvariante asignada.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Parámetros

*ppPropVariant*<br/>
Cuando se devuelve la función, este parámetro contiene el valor de fragmento.

### <a name="return-value"></a>Valor devuelto

S_OK si PROPVARIANT se asignó correctamente y el valor del fragmento se copió correctamente en *ppPropVariant*; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc

Devuelve el valor no asignado (valor interno).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor de fragmento actual.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid

Comprueba si este valor de propiedad es válido o no.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el valor de fragmento actual es válido; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue

Sobrecargado. Establece la propiedad por clave en un valor booleano.

```
HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);

HRESULT SetBoolValue(
    REFPROPERTYKEY pkey,
    VARIANT_BOOL bVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*bVal*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk

Función auxiliar que establece las propiedades comunes del fragmento.

```
HRESULT SetChunk(
    REFPROPERTYKEY pkey,
    CHUNKSTATE chunkType=CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue

Establezca la propiedad por clave en dWORD.

```
HRESULT SetDwordValue(
    REFPROPERTYKEY pkey,
    DWORD dwVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*dwVal*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue

Establezca la propiedad por clave en un archivotime.

```
HRESULT SetFileTimeValue(
    REFPROPERTYKEY pkey,
    FILETIME dtVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*dtVal*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value

Establezca la propiedad por clave en un int64.

```
HRESULT SetInt64Value(
    REFPROPERTYKEY pkey,
    __int64 nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*nVal*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue

Establezca la propiedad por clave en un int.

```
HRESULT SetIntValue(
    REFPROPERTYKEY pkey,
    int nVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*nVal*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue

Establezca la propiedad por clave en LONG.

```
HRESULT SetLongValue(
    REFPROPERTYKEY pkey,
    long lVal,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*lVal*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue

Establece la propiedad por clave en un SystemTime.

```
HRESULT SetSystemTimeValue(
    REFPROPERTYKEY pkey,
    const SYSTEMTIME& systemTime,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale=0,
    DWORD cwcLenSource=0,
    DWORD cwcStartSource=0,
    CHUNK_BREAKTYPE chunkBreakType=CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*systemTime*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue

Establece la propiedad por clave en una cadena Unicode.

```
HRESULT SetTextValue(
    REFPROPERTYKEY pkey,
    LPCTSTR pszValue,
    CHUNKSTATE chunkType = CHUNK_VALUE,
    LCID locale = 0,
    DWORD cwcLenSource = 0,
    DWORD cwcStartSource = 0,
    CHUNK_BREAKTYPE chunkBreakType = CHUNK_NO_BREAK);
```

### <a name="parameters"></a>Parámetros

*pkey*<br/>
Especifica una clave de propiedad.

*pszValue*<br/>
Especifica el valor de fragmento que se va a establecer.

*chunkType*<br/>
Los indicadores indican si este fragmento contiene una propiedad de tipo de texto o de tipo de valor. Los valores de marca se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y el subidioma asociados a un fragmento de texto. Los indexadores de documentos utilizan la configuración regional de fragmentos para realizar la separación de palabras adecuada del texto. Si el fragmento no es de tipo de texto ni de tipo de valor con el tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen del que se derivó el fragmento actual. Un valor cero significa la correspondencia carácter por carácter entre el texto fuente y el texto derivado. Un valor distinto de cero significa que no existe tal correspondencia directa.

*cwcStartSource*<br/>
Desplazamiento desde el que se inicia el texto de origen de un fragmento derivado en el fragmento de origen.

*chunkBreakType*<br/>
El tipo de rotura que separa el fragmento anterior del fragmento actual. Los valores proceden de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; de lo contrario, un código de error.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Clases](../../mfc/reference/mfc-classes.md)
