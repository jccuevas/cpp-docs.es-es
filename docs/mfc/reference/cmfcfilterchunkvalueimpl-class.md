---
title: Clase CMFCFilterChunkValueImpl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCFilterChunkValueImpl
- afxwin/CMFCFilterChunkValueImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCFilterChunkValueImpl class
ms.assetid: 3c833f23-5b88-4d08-9e09-ca6a8aec88bf
caps.latest.revision: 25
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 8de3cba19a60b8022df96a9edafd13677fa3fecb
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcfilterchunkvalueimpl-class"></a>Clase CMFCFilterChunkValueImpl
Se trata de una clase que simplifica la lógica de par de valor de fragmento y propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMFCFilterChunkValueImpl : public ATL::IFilterChunkValue;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl](#_dtorcmfcfilterchunkvalueimpl)|El objeto se destruye.|  
|[CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl](#cmfcfilterchunkvalueimpl)|Construye el objeto.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::Clear](#clear)|Borra la ChunkValue.|  
|[CMFCFilterChunkValueImpl::CopyChunk](#copychunk)|Este fragmento se copia a una estructura que describe las características de un fragmento.|  
|[CMFCFilterChunkValueImpl::CopyFrom](#copyfrom)|Inicializa este valor de fragmento desde el otro valor.|  
|[CMFCFilterChunkValueImpl::GetChunkGUID](#getchunkguid)|Recupera el GUID del fragmento.|  
|[CMFCFilterChunkValueImpl::GetChunkPID](#getchunkpid)|Recupera el fragmento PID (identificador de propiedad).|  
|[CMFCFilterChunkValueImpl::GetChunkType](#getchunktype)|Obtiene fragmentos de tipo.|  
|[CMFCFilterChunkValueImpl::GetString](#getstring)|Recupera el valor de cadena.|  
|[CMFCFilterChunkValueImpl::GetValue](#getvalue)|Recupera el valor como un propvariant asignado.|  
|[CMFCFilterChunkValueImpl::GetValueNoAlloc](#getvaluenoalloc)|Valor devuelve sin asignar (valor interno).|  
|[CMFCFilterChunkValueImpl::IsValid](#isvalid)|Comprueba si el valor de esta propiedad es válida o no.|  
|[CMFCFilterChunkValueImpl::SetBoolValue](#setboolvalue)|Sobrecargado. Establece la propiedad clave a un valor booleano.|  
|[CMFCFilterChunkValueImpl::SetDwordValue](#setdwordvalue)|Establece la propiedad clave para un valor DWORD.|  
|[CMFCFilterChunkValueImpl::SetFileTimeValue](#setfiletimevalue)|Establece la propiedad clave de filetime.|  
|[CMFCFilterChunkValueImpl::SetInt64Value](#setint64value)|Establece la propiedad clave en int64.|  
|[CMFCFilterChunkValueImpl::SetIntValue](#setintvalue)|Establece la propiedad clave a un int.|  
|[CMFCFilterChunkValueImpl::SetLongValue](#setlongvalue)|Establece la propiedad clave en un valor largo.|  
|[CMFCFilterChunkValueImpl::SetSystemTimeValue](#setsystemtimevalue)|Establece la propiedad clave para un objeto SystemTime.|  
|[CMFCFilterChunkValueImpl::SetTextValue](#settextvalue)|Establece la propiedad de clave en una cadena Unicode.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMFCFilterChunkValueImpl::SetChunk](#setchunk)|Una función auxiliar que establece las propiedades comunes del fragmento.|  
  
## <a name="remarks"></a>Comentarios  
 Para utilizar, simplemente cree una clase CMFCFilterChunkValueImpl del tipo correcto  
  
 Ejemplo:  
  
 Fragmento de CMFCFilterChunkValueImpl;  
  
 HR = fragmento. SetBoolValue(PKEY_IsAttachment, true);  
  
 o  
  
 HR = fragmento. SetFileTimeValue (PKEY_ItemDate, ftLastModified);  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ATL::IFilterChunkValue`  
  
 [CMFCFilterChunkValueImpl](../../mfc/reference/cmfcfilterchunkvalueimpl-class.md)  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecleara--cmfcfilterchunkvalueimplclear"></a><a name="clear"></a>CMFCFilterChunkValueImpl::Clear  
 Borra la ChunkValue.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecmfcfilterchunkvalueimpla--cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="cmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl::CMFCFilterChunkValueImpl  
 Construye el objeto.  
  
```  
CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namedtorcmfcfilterchunkvalueimpla--cmfcfilterchunkvalueimplcmfcfilterchunkvalueimpl"></a><a name="_dtorcmfcfilterchunkvalueimpl"></a>CMFCFilterChunkValueImpl:: ~ CMFCFilterChunkValueImpl  
 El objeto se destruye.  
  
```  
virtual ~CMFCFilterChunkValueImpl();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecopychunka--cmfcfilterchunkvalueimplcopychunk"></a><a name="copychunk"></a>CMFCFilterChunkValueImpl::CopyChunk  
 Este fragmento se copia a una estructura que describe las características de un fragmento.  
  
```  
HRESULT CopyChunk(STAT_CHUNK* pStatChunk);
```  
  
### <a name="parameters"></a>Parámetros  
 `pStatChunk`  
 Un puntero al valor de destino que describen las características del fragmento.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namecopyfroma--cmfcfilterchunkvalueimplcopyfrom"></a><a name="copyfrom"></a>CMFCFilterChunkValueImpl::CopyFrom  
 Inicializa este valor de fragmento desde el otro valor.  
  
```  
void CopyFrom (IFilterChunkValue* pValue);
```  
  
### <a name="parameters"></a>Parámetros  
 `pValue`  
 Especifica el valor de origen que lo copien.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetchunkguida--cmfcfilterchunkvalueimplgetchunkguid"></a><a name="getchunkguid"></a>CMFCFilterChunkValueImpl::GetChunkGUID  
 Recupera el GUID del fragmento.  
  
```  
REFGUID GetChunkGUID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a un GUID que identifica el fragmento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetchunkpida--cmfcfilterchunkvalueimplgetchunkpid"></a><a name="getchunkpid"></a>CMFCFilterChunkValueImpl::GetChunkPID  
 Recupera el fragmento PID (identificador de propiedad).  
  
```  
DWORD GetChunkPID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor DWORD que contiene el identificador de propiedad.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetchunktypea--cmfcfilterchunkvalueimplgetchunktype"></a><a name="getchunktype"></a>CMFCFilterChunkValueImpl::GetChunkType  
 Recupera el tipo de fragmento.  
  
```  
CHUNKSTATE GetChunkType() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor enumerado de CHUNKSTATE, que especifica si el fragmento actual es una propiedad de tipo de texto o una propiedad de tipo de valor.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetstringa--cmfcfilterchunkvalueimplgetstring"></a><a name="getstring"></a>CMFCFilterChunkValueImpl::GetString  
 Recupera el valor de cadena.  
  
```  
CString &GetString();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una cadena que contiene el valor de fragmento.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetvaluea--cmfcfilterchunkvalueimplgetvalue"></a><a name="getvalue"></a>CMFCFilterChunkValueImpl::GetValue  
 Recupera el valor como un propvariant asignado.  
  
```  
HRESULT GetValue(PROPVARIANT** ppPropVariant);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppPropVariant`  
 Cuando la función vuelve, este parámetro contiene el valor de fragmento.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si PROPVARIANT se asignó correctamente y el valor de fragmento se copió correctamente en `ppPropVariant`; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namegetvaluenoalloca--cmfcfilterchunkvalueimplgetvaluenoalloc"></a><a name="getvaluenoalloc"></a>CMFCFilterChunkValueImpl::GetValueNoAlloc  
 Devuelve el valor de sin asignar (valor interno).  
  
```  
PROPVARIANT GetValueNoAlloc ();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor del campo actual.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameisvalida--cmfcfilterchunkvalueimplisvalid"></a><a name="isvalid"></a>CMFCFilterChunkValueImpl::IsValid  
 Comprueba si el valor de esta propiedad es válida o no.  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si el valor actual de fragmento es válido; de lo contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetboolvaluea--cmfcfilterchunkvalueimplsetboolvalue"></a><a name="setboolvalue"></a>CMFCFilterChunkValueImpl::SetBoolValue  
 Sobrecargado. Establece la propiedad clave a un valor booleano.  
  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `bVal`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetchunka--cmfcfilterchunkvalueimplsetchunk"></a><a name="setchunk"></a>CMFCFilterChunkValueImpl::SetChunk  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; código de error en caso contrario.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetdwordvaluea--cmfcfilterchunkvalueimplsetdwordvalue"></a><a name="setdwordvalue"></a>CMFCFilterChunkValueImpl::SetDwordValue  
 Establezca la propiedad clave a un valor DWORD.  
  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `dwVal`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetfiletimevaluea--cmfcfilterchunkvalueimplsetfiletimevalue"></a><a name="setfiletimevalue"></a>CMFCFilterChunkValueImpl::SetFileTimeValue  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `dtVal`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetint64valuea--cmfcfilterchunkvalueimplsetint64value"></a><a name="setint64value"></a>CMFCFilterChunkValueImpl::SetInt64Value  
 Establezca la propiedad clave en int64.  
  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `nVal`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetintvaluea--cmfcfilterchunkvalueimplsetintvalue"></a><a name="setintvalue"></a>CMFCFilterChunkValueImpl::SetIntValue  
 Establecer la propiedad clave a un int.  
  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `nVal`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetlongvaluea--cmfcfilterchunkvalueimplsetlongvalue"></a><a name="setlongvalue"></a>CMFCFilterChunkValueImpl::SetLongValue  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `lVal`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesetsystemtimevaluea--cmfcfilterchunkvalueimplsetsystemtimevalue"></a><a name="setsystemtimevalue"></a>CMFCFilterChunkValueImpl::SetSystemTimeValue  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `systemTime`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-namesettextvaluea--cmfcfilterchunkvalueimplsettextvalue"></a><a name="settextvalue"></a>CMFCFilterChunkValueImpl::SetTextValue  
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
 `pkey`  
 Especifica una clave de propiedad.  
  
 `pszValue`  
 Especifica el valor de fragmento para establecer.  
  
 `chunkType`  
 Marcas indican si este campo contiene un tipo de texto o una propiedad de tipo de valor. Valores de indicador se toman de la enumeración CHUNKSTATE.  
  
 `locale`  
 El idioma y subidioma asociado a un fragmento de texto. Configuración regional del fragmento se utiliza indizadores de documento para realizar correcto de las palabras importantes de texto. Si el fragmento no es de tipo texto ni un tipo de valor con tipo de datos VT_LPWSTR, VT_LPSTR o VT_BSTR, se omite este campo.  
  
 `cwcLenSource`  
 La longitud en caracteres del texto de origen que se deriva del campo actual. Un valor de cero significa carácter por carácter correspondencia entre el texto de origen y el texto derivado. Un valor distinto de cero significa que no exista ninguna correspondencia de directa.  
  
 `cwcStartSource`  
 El desplazamiento desde el que comienza el texto de origen para un fragmento derivado en el fragmento de código fuente.  
  
 `chunkBreakType`  
 El tipo de salto que separa el fragmento anterior desde el fragmento actual. Los valores son de la enumeración CHUNK_BREAKTYPE.  
  
### <a name="return-value"></a>Valor devuelto  
 S_OK si es correcto; de lo contrario, un código de error.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)

