---
title: CEnumerator (Clase)
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: 23467caf46d38175a74dab061f60e11009f1f481
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030185"
---
# <a name="cenumerator-class"></a>CEnumerator (Clase)

Usa un objeto de enumerador OLE DB que expone el [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) interfaz para devolver un conjunto de filas que describe todos los orígenes de datos y enumeradores.

## <a name="syntax"></a>Sintaxis

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Find](#find)|Búsquedas a través de proveedores disponibles (orígenes de datos) busca uno con el nombre especificado.|
|[GetMoniker](#getmoniker)|Recupera el `IMoniker` interfaz para el registro actual.|
|[Abrir](#open)|Se abre el enumerador.|

## <a name="remarks"></a>Comentarios

Puede recuperar el `ISourcesRowset` datos indirectamente de esta clase.

## <a name="find"></a> CEnumerator::Find

Busca un nombre especificado entre los proveedores disponibles.

### <a name="syntax"></a>Sintaxis

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Parámetros

*szSearchName*<br/>
[in] El nombre que se buscará.

### <a name="return-value"></a>Valor devuelto

**True** si se encontró el nombre. En caso contrario, **false**.

### <a name="remarks"></a>Comentarios

Este nombre se asigna a la `SOURCES_NAME` miembro de la [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) interfaz.

## <a name="getmoniker"></a> CEnumerator::GetMoniker

Analiza el nombre para mostrar para extraer el componente de la cadena que se puede convertir en un moniker.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Parámetros

*ppMoniker*<br/>
[out] Analiza el moniker del nombre para mostrar ([cenumeratoraccessor:: M_szparsename](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) de la fila actual.

*lpszDisplayName*<br/>
[in] El nombre para mostrar para analizar.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="open"></a> CEnumerator:: Open

Enlaza el moniker del enumerador, si uno se especifica, recupera el conjunto de filas del enumerador mediante una llamada a [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Parámetros

*pMoniker*<br/>
[in] Un puntero a un moniker para un enumerador.

*pClsid*<br/>
[in] Un puntero a la `CLSID` del enumerador.

*enumerator*<br/>
[in] Una referencia a un enumerador.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="see-also"></a>Vea también

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)