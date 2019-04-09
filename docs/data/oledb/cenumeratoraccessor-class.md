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
- m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- m_szName
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
ms.openlocfilehash: e609b346bb4a0c2469c24e20540c646fa869ae26
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025168"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor (Clase)

Utilizado por [CEnumerator](../../data/oledb/cenumerator-class.md) para tener acceso a los datos desde el conjunto de filas del enumerador.

## <a name="syntax"></a>Sintaxis

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_bIsParent](#bisparent)|Una variable que indica si el enumerador es un enumerador primario, si la fila es un enumerador.|
|[m_nType](#ntype)|Una variable que indica si la fila describe un origen de datos o un enumerador.|
|[m_szDescription](#szdescription)|La descripción del origen de datos o enumerador.|
|[m_szName](#szname)|El nombre del origen de datos o enumerador.|
|[m_szParseName](#szparsename)|Cadena que se pasan al [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) para obtener un moniker para el origen de datos o enumerador.|

## <a name="remarks"></a>Comentarios

Este conjunto de filas se compone de los orígenes de datos y enumeradores visibles desde el enumerador actual.

## <a name="bisparent"></a> CEnumeratorAccessor::m_bIsParent

Una variable que indica si el enumerador es un enumerador primario, si la fila es un enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>Comentarios

Consulte [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en el *referencia del programador de OLE DB* para obtener más información.

## <a name="ntype"></a> CEnumeratorAccessor::m_nType

Una variable que indica si la fila describe un origen de datos o un enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>Comentarios

Consulte [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en el *referencia del programador de OLE DB* para obtener más información.

## <a name="szdescription"></a> CEnumeratorAccessor::m_szDescription

La descripción del origen de datos o enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>Comentarios

Consulte [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en el *referencia del programador de OLE DB* para obtener más información.

## <a name="szname"></a> CEnumeratorAccessor::m_szName

El nombre del origen de datos o enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>Comentarios

Consulte [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en el *referencia del programador de OLE DB* para obtener más información.

## <a name="szparsename"></a> CEnumeratorAccessor::m_szParseName

Cadena que se pasan al [IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname) para obtener un moniker para el origen de datos o enumerador.

### <a name="syntax"></a>Sintaxis

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>Comentarios

Consulte [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) en el *referencia del programador de OLE DB* para obtener más información.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)