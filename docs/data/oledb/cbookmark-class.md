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
ms.openlocfilehash: d3d82ea09b7ed2c1cbaf325906b4f9b480e1eb4e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359336"
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

*nTamaño*<br/>
El tamaño del búfer de marcadores en bytes. Cuando *nSize* es cero, el búfer de marcadorse se creará dinámicamente en tiempo de ejecución.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CBookmark](#cbookmark)|El constructor|
|[GetBuffer](#getbuffer)|Recupera el puntero al búfer.|
|[GetSize](#getsize)|Recupera el tamaño del búfer en bytes.|
|[SetBookmark](#setbookmark)|Establece el valor del marcador.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador a la operadora de la red](#operator)|Asigna una `CBookmark` clase a otra.|

## <a name="remarks"></a>Observaciones

`CBookmark<0>`es una especialización de plantilla de `CBookmark`; su búfer se crea dinámicamente en tiempo de ejecución.

## <a name="cbookmarkcbookmark"></a><a name="cbookmark"></a>CBookmark::CBookmark

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
CBookmark();
CBookmark(DBLENGTH nSize);
```

#### <a name="parameters"></a>Parámetros

*nTamaño*<br/>
[en] Tamaño del búfer de marcadores en bytes.

### <a name="remarks"></a>Observaciones

La primera función establece el búfer en NULL y el tamaño del búfer en 0. La segunda función establece el tamaño del búfer en *nSize*y el búfer en una matriz de bytes de *nSize* bytes.

> [!NOTE]
> Esta función solo `CBookmark<0>`está disponible en .

## <a name="cbookmarkgetbuffer"></a><a name="getbuffer"></a>CBookmark::GetBuffer

Recupera el puntero al búfer de marcadores.

### <a name="syntax"></a>Sintaxis

```cpp
virtual BYTE* GetBuffer() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un puntero al búfer de marcadores.

## <a name="cbookmarkgetsize"></a><a name="getsize"></a>CBookmark::GetSize

Recupera el tamaño del búfer de marcadores.

### <a name="syntax"></a>Sintaxis

```cpp
virtual DBLENGTH GetSize() const throw();
```

### <a name="return-value"></a>Valor devuelto

Tamaño del búfer en bytes.

## <a name="cbookmarksetbookmark"></a><a name="setbookmark"></a>CBookmark::SetBookmark

Copia el valor de marcador `CBookmark` al que hace referencia *pBuffer en* el búfer y establece el tamaño del búfer en *nSize*.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetBookmark(DBLENGTH nSize, BYTE* pBuffer) throw();
```

#### <a name="parameters"></a>Parámetros

*nTamaño*<br/>
[en] El tamaño del búfer de marcadores.

*pBuffer*<br/>
[en] Puntero a la matriz de bytes que contiene el valor del marcador.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Esta función solo `CBookmark<0>`está disponible en .

## <a name="cbookmarkoperator-"></a><a name="operator"></a>CBookmark::operador ?

Asigna un `CBookmark` objeto a otro.

### <a name="syntax"></a>Sintaxis

```cpp
CBookmark& operator =(const CBookmark& bookmark) throw();
```

### <a name="remarks"></a>Observaciones

Este operador solo `CBookmark<0>`es necesario en .

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
