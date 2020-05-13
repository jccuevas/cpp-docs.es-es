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
ms.openlocfilehash: d0fa5f381dba4f67934007d59dbdaf4450bcfb60
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211801"
---
# <a name="cenumerator-class"></a>CEnumerator (Clase)

Utiliza un objeto de enumerador de OLE DB, que expone la interfaz [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) para devolver un conjunto de filas que describe todos los orígenes de datos y enumeradores.

## <a name="syntax"></a>Sintaxis

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Buscar](#find)|Busca en los proveedores disponibles (orígenes de datos) y busca uno con el nombre especificado.|
|[GetMoniker](#getmoniker)|Recupera la interfaz de `IMoniker` del registro actual.|
|[Abrir](#open)|Abre el enumerador.|

## <a name="remarks"></a>Observaciones

Puede recuperar los datos de `ISourcesRowset` indirectamente de esta clase.

## <a name="cenumeratorfind"></a><a name="find"></a>CEnumerator:: Find

Busca un nombre especificado entre los proveedores disponibles.

### <a name="syntax"></a>Sintaxis

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>Parámetros

*szSearchName*<br/>
de Nombre que se va a buscar.

### <a name="return-value"></a>Valor devuelto

**true** si se encontró el nombre. De lo contrario, se devuelve el valor **False**.

### <a name="remarks"></a>Observaciones

Este nombre se asigna al miembro `SOURCES_NAME` de la interfaz [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) .

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a>CEnumerator:: GetMoniker

Analiza el nombre para mostrar para extraer el componente de la cadena que se puede convertir en un moniker.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>Parámetros

*ppMoniker*<br/>
enuncia Moniker analizado a partir del nombre para mostrar ([CEnumeratorAccessor:: m_szParseName](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) de la fila actual.

*lpszDisplayName*<br/>
de Nombre para mostrar que se va a analizar.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cenumeratoropen"></a><a name="open"></a>CEnumerator:: Open

Enlaza el moniker del enumerador, si se especifica uno, recupera el conjunto de filas para el enumerador mediante una llamada a [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>Parámetros

*pMoniker*<br/>
de Un puntero a un moniker para un enumerador.

*pClsid*<br/>
de Puntero a la `CLSID` de un enumerador.

*enumerator*<br/>
de Referencia a un enumerador.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="see-also"></a>Consulte también

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
