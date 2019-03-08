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
ms.openlocfilehash: b883d442342dd9fbbd074d9f8fcab76f81ef9864
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264448"
---
# <a name="cmfcfilterchunkvalueimpl-class"></a>Clase CMFCFilterChunkValueImpl

Se trata de una clase que simplifica la lógica de par de valor de fragmento y propiedad.

## <a name="syntax"></a>Sintaxis

```
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|Se destruye el objeto.|
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Construye el objeto.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::Clear](#clear)|Borra la ChunkValue.|
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Este fragmento se copia a una estructura que describe las características de un fragmento.|
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicializa este valor fragmentos desde el otro valor.|
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Recupera el GUID del fragmento.|
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Recupera el fragmento PID (Id. de propiedad).|
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Obtiene fragmentos de tipo.|
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Recupera el valor de cadena.|
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Recupera el valor como un propvariant asignado.|
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Valor devuelve sin asignar (valor interno).|
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Comprueba si el valor de esta propiedad es válido o no.|
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Sobrecargado. Establece la propiedad de clave en un valor booleano.|
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Establece la propiedad de clave en un valor DWORD.|
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Establece la propiedad clave de filetime.|
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Establece la propiedad de clave en un int64.|
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Establece la propiedad de clave a int.|
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Establece la propiedad de clave en un valor largo.|
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Establece la propiedad clave para un objeto SystemTime.|
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Establece la propiedad de clave en una cadena Unicode.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Una función auxiliar que establece las propiedades comunes del fragmento.|

## <a name="remarks"></a>Comentarios

Para usar, simplemente crear una clase CMFCFilterChunkValueImpl del tipo correcto

Ejemplo:

CMFCFilterChunkValueImpl chunk;

hr = chunk.SetBoolValue(PKEY_IsAttachment, true);

o

hr = chunk.SetFileTimeValue(PKEY_ItemDate, ftLastModified);

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ATL::IFilterChunkValue`

[CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="clear"></a>  CMFCFilterChunkValueImpl::Clear

Borra la ChunkValue.

```
void Clear();
```

### <a name="remarks"></a>Comentarios

##  <a name="cmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl

Construye el objeto.

```
CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Comentarios

##  <a name="_dtorcmfcfilterchunkvalueimpl"></a>  CMFCFilterChunkValueImpl::~CMFCFilterChunkValueImpl

Se destruye el objeto.

```
virtual ~CMFCFilterChunkValueImpl();
```

### <a name="remarks"></a>Comentarios

##  <a name="copychunk"></a>  CMFCFilterChunkValueImpl::CopyChunk

Este fragmento se copia a una estructura que describe las características de un fragmento.

```
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```

### <a name="parameters"></a>Parámetros

*pStatChunk*<br/>
Un puntero al valor de destino donde se describen las características del fragmento.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="copyfrom"></a>  CMFCFilterChunkValueImpl::CopyFrom

Inicializa este valor fragmentos desde el otro valor.

```
void CopyFrom (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>Parámetros

*pValue*<br/>
Especifica el valor de origen para copiarlos.

### <a name="remarks"></a>Comentarios

##  <a name="getchunkguid"></a>  CMFCFilterChunkValueImpl::GetChunkGUID

Recupera el GUID del fragmento.

```
REFGUID GetChunkGUID() const;
```

### <a name="return-value"></a>Valor devuelto

Una referencia a un GUID que identifica el fragmento.

### <a name="remarks"></a>Comentarios

##  <a name="getchunkpid"></a>  CMFCFilterChunkValueImpl::GetChunkPID

Recupera el fragmento PID (Id. de propiedad).

```
DWORD GetChunkPID() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor DWORD que contiene el identificador de propiedad.

### <a name="remarks"></a>Comentarios

##  <a name="getchunktype"></a>  CMFCFilterChunkValueImpl::GetChunkType

Recupera el tipo de fragmento.

```
CHUNKSTATE GetChunkType() const;
```

### <a name="return-value"></a>Valor devuelto

Un valor CHUNKSTATE enumerado, que especifica si el fragmento actual es una propiedad de tipo de texto o una propiedad de tipo de valor.

### <a name="remarks"></a>Comentarios

##  <a name="getstring"></a>  CMFCFilterChunkValueImpl::GetString

Recupera el valor de cadena.

```
CString &GetString();
```

### <a name="return-value"></a>Valor devuelto

Una cadena que contiene el valor de fragmento.

### <a name="remarks"></a>Comentarios

##  <a name="getvalue"></a>  CMFCFilterChunkValueImpl::GetValue

Recupera el valor como un propvariant asignado.

```
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```

### <a name="parameters"></a>Parámetros

*ppPropVariant*<br/>
La función que devuelve este parámetro contiene el valor de fragmento.

### <a name="return-value"></a>Valor devuelto

S_OK si PROPVARIANT se asignó correctamente y el valor de fragmento se copió correctamente en *ppPropVariant*; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="getvaluenoalloc"></a>  CMFCFilterChunkValueImpl::GetValueNoAlloc

Devuelve el valor sin asignar (valor interno).

```
PROPVARIANT GetValueNoAlloc ();
```

### <a name="return-value"></a>Valor devuelto

Devuelve el valor actual de fragmentos.

### <a name="remarks"></a>Comentarios

##  <a name="isvalid"></a>  CMFCFilterChunkValueImpl::IsValid

Comprueba si el valor de esta propiedad es válido o no.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el valor actual de fragmentos es válido; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="setboolvalue"></a>  CMFCFilterChunkValueImpl::SetBoolValue

Sobrecargado. Establece la propiedad de clave en un valor booleano.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="setchunk"></a>  CMFCFilterChunkValueImpl::SetChunk

Una función auxiliar que establece las propiedades comunes del fragmento.

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
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; código de error en caso contrario.

### <a name="remarks"></a>Comentarios

##  <a name="setdwordvalue"></a>  CMFCFilterChunkValueImpl::SetDwordValue

Establezca la propiedad clave en un valor DWORD.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="setfiletimevalue"></a>  CMFCFilterChunkValueImpl::SetFileTimeValue

Establezca la propiedad clave de filetime.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="setint64value"></a>  CMFCFilterChunkValueImpl::SetInt64Value

Establezca la propiedad clave en un int64.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="setintvalue"></a>  CMFCFilterChunkValueImpl::SetIntValue

Establezca la propiedad clave a int.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="setlongvalue"></a>  CMFCFilterChunkValueImpl::SetLongValue

Establezca la propiedad clave en un valor largo.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="setsystemtimevalue"></a>  CMFCFilterChunkValueImpl::SetSystemTimeValue

Establece la propiedad clave para un objeto SystemTime.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

##  <a name="settextvalue"></a>  CMFCFilterChunkValueImpl::SetTextValue

Establece la propiedad de clave en una cadena Unicode.

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
Especifica el valor de fragmento para establecer.

*chunkType*<br/>
Marcas indican si este fragmento contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.

*locale*<br/>
El idioma y subidioma asociado con un fragmento de texto. Configuración regional de fragmento está usando los indexadores de documentos para realizar la división de texto de palabras adecuada. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_BSTR, VT_LPSTR o VT_LPWSTR, se omite este campo.

*cwcLenSource*<br/>
La longitud en caracteres del texto de origen que se deriva el fragmento actual. Un valor cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no hay tal correspondencia directa existe.

*cwcStartSource*<br/>
El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.

*chunkBreakType*<br/>
El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.

### <a name="return-value"></a>Valor devuelto

S_OK si se realiza correctamente; en caso contrario, un código de error.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Clases](../../mfc/reference/mfc-classes.md)
