---
title: CEnumeratorAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
- CEnumeratorAccessor.m_bIsParent
- ATL::CEnumeratorAccessor::m_bIsParent
- m_bIsParent
- ATL.CEnumeratorAccessor.m_bIsParent
- CEnumeratorAccessor::m_bIsParent
- ATL::CEnumeratorAccessor::m_nType
- CEnumeratorAccessor.m_nType
- CEnumeratorAccessor::m_nType
- ATL.CEnumeratorAccessor.m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- ATL::CEnumeratorAccessor::m_szName
- CEnumeratorAccessor.m_szName
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
ms.openlocfilehash: d85f630a01ab7e2a07035a8a304a56be91eca8a9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545634"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor (Clase)

Usado por [CEnumerator](../../data/oledb/cenumerator-class.md) para tener acceso a los datos del conjunto de filas del enumerador.

## <a name="syntax"></a>Sintaxis

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bIsParent](#bisparent)|Variable que indica si el enumerador es un enumerador primario, si la fila es un enumerador.|
|[m_nType](#ntype)|Variable que indica si la fila describe un origen de datos o un enumerador.|
|[m_szDescription](#szdescription)|La descripción del origen de datos o enumerador.|
|[m_szName](#szname)|Nombre del origen de datos o enumerador.|
|[m_szParseName](#szparsename)|Cadena que se va a pasar a [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) para obtener un moniker para el origen de datos o el enumerador.|

## <a name="remarks"></a>Observaciones

Este conjunto de filas consta de los orígenes de datos y los enumeradores visibles en el enumerador actual.

## <a name="cenumeratoraccessorm_bisparent"></a><a name="bisparent"></a>CEnumeratorAccessor:: m_bIsParent

Variable que indica si el enumerador es un enumerador primario, si la fila es un enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>Observaciones

Vea [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

## <a name="cenumeratoraccessorm_ntype"></a><a name="ntype"></a>CEnumeratorAccessor:: m_nType

Variable que indica si la fila describe un origen de datos o un enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>Observaciones

Vea [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

## <a name="cenumeratoraccessorm_szdescription"></a><a name="szdescription"></a>CEnumeratorAccessor:: m_szDescription

La descripción del origen de datos o enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>Observaciones

Vea [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

## <a name="cenumeratoraccessorm_szname"></a><a name="szname"></a>CEnumeratorAccessor:: m_szName

Nombre del origen de datos o enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>Observaciones

Vea [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

## <a name="cenumeratoraccessorm_szparsename"></a><a name="szparsename"></a>CEnumeratorAccessor:: m_szParseName

Cadena que se va a pasar a [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) para obtener un moniker para el origen de datos o el enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>Observaciones

Vea [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)