---
title: CBookmark (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.CBookmark
- ATL::CBookmark<nSize>
- CBookmark
- ATL.CBookmark<nSize>
- ATL::CBookmark
- CBookmark<0>.CBookmark<0>
- CBookmark::CBookmark
- ATL.CBookmark.CBookmark
- CBookmark.CBookmark
- CBookmark
- ATL::CBookmark<0>::CBookmark<0>
- ATL.CBookmark<0>.CBookmark<0>
- CBookmark<0>::CBookmark<0>
- ATL::CBookmark::CBookmark
- ATL.CBookmark<0>.GetBuffer
- ATL.CBookmark.GetBuffer
- ATL::CBookmark<0>::GetBuffer
- ATL::CBookmark::GetBuffer
- CBookmark.GetBuffer
- ATL::CBookmark<nSize>::GetBuffer
- ATL.CBookmark<nSize>.GetBuffer
- CBookmark<0>.GetBuffer
- CBookmark<nSize>::GetBuffer
- CBookmark<0>::GetBuffer
- CBookmark<nSize>.GetBuffer
- CBookmark::GetBuffer
- CBookmark::GetSize
- ATL.CBookmark<nSize>.GetSize
- CBookmark<nSize>.GetSize
- CBookmark.GetSize
- ATL::CBookmark::GetSize
- CBookmark<0>::GetSize
- ATL::CBookmark<nSize>::GetSize
- ATL.CBookmark<0>.GetSize
- ATL::CBookmark<0>::GetSize
- ATL.CBookmark.GetSize
- CBookmark<0>.GetSize
- CBookmark<nSize>::GetSize
- CBookmark<0>::SetBookmark
- ATL.CBookmark<0>.SetBookmark
- CBookmark<0>.SetBookmark
- SetBookmark
- ATL::CBookmark::SetBookmark
- ATL::CBookmark<0>::SetBookmark
- CBookmark.SetBookmark
- ATL.CBookmark.SetBookmark
- CBookmark::SetBookmark
- CBookmark<0>::operator=
- CBookmark<0>.operator=
- ATL.CBookmark.operator=
- CBookmark::operator=
- ATL.CBookmark<0>.operator=
- ATL::CBookmark<0>::operator=
- CBookmark.operator=
- ATL::CBookmark::operator=
helpviewer_keywords:
- CBookmark class
- CBookmark class, constructor
- GetBuffer method
- GetSize method
- SetBookmark method
- = operator, with OLE DB templates
- operator =, bookmarks
- operator=, bookmarks
ms.assetid: bc942f95-6f93-41d9-bb6e-bcdae4ae0b7a
ms.openlocfilehash: 669a0c8da54e8a2523df644c29bbb26051c024da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50577470"
---
# <a name="cbookmark-class"></a>CBookmark (Clase)

Contiene un valor de marcador en su búfer.

## <a name="syntax"></a>Sintaxis

```cpp
template < DBLENGTH nSize = 0 >
class CBookmark : public CBookmarkBase

template <>
class CBookmark< 0 > : public CBookmarkBase
```

### <a name="parameters"></a>Parámetros

*nSize*<br/>
El tamaño del búfer del marcador en bytes. Cuando *nSize* es cero, el búfer de marcador se crearán dinámicamente en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CBookmark](#cbookmark)|El constructor|
|[GetBuffer](#getbuffer)|Recupera el puntero al búfer.|
|[GetSize](#getsize)|Recupera el tamaño del búfer en bytes.|
|[SetBookmark](#setbookmark)|Establece el valor de marcador.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#operator)|Asigna un valor `CBookmark` clase a otra.|

## <a name="remarks"></a>Comentarios

`CBookmark<0>` es una especialización de plantilla de `CBookmark`; su búfer se crea dinámicamente en tiempo de ejecución.

## <a name="cbookmark"></a> CBookmark:: CBookmark

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
CBookmark();
 
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Parámetros

*nSize*<br/>
[in] Tamaño del búfer del marcador en bytes.

### <a name="remarks"></a>Comentarios

La primera función establece el búfer en NULL y el tamaño del búfer en 0. La segunda función establece el tamaño de búfer en *nSize*y el búfer en una matriz de bytes de *nSize* bytes.

> [!NOTE]
>  Esta función sólo está disponible en `CBookmark<0>`.

## <a name="getbuffer"></a> CBookmark:: GetBuffer

Recupera el puntero al búfer del marcador.

### <a name="syntax"></a>Sintaxis

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al búfer de marcador.

## <a name="getsize"></a> CBookmark:: GetSize

Recupera el tamaño del búfer del marcador.

### <a name="syntax"></a>Sintaxis

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Valor devuelto

El tamaño del búfer en bytes.

## <a name="setbookmark"></a> CBookmark:: SetBookmark

Copia el valor de marcador al que hace referencia *pBuffer* a la `CBookmark` búfer y se establece el tamaño de búfer en *nSize*.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Parámetros

*nSize*<br/>
[in] El tamaño del búfer del marcador.

*pBuffer*<br/>
[in] Un puntero a la matriz de bytes que contiene el valor de marcador.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Esta función sólo está disponible en `CBookmark<0>`.

## <a name="operator"></a> CBookmark:: operator =

Asigna un `CBookmark` objeto a otro.

### <a name="syntax"></a>Sintaxis

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Comentarios

Este operador es necesaria sólo en `CBookmark<0>`.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)