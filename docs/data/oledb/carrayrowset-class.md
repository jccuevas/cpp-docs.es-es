---
title: CArrayRowset (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.CArrayRowset<TAccessor>
- ATL.CArrayRowset
- CArrayRowset
- ATL::CArrayRowset
- ATL::CArrayRowset<TAccessor>
- ATL::CArrayRowset::CArrayRowset
- CArrayRowset.CArrayRowset
- ATL.CArrayRowset.CArrayRowset
- ATL.CArrayRowset<TAccessor>.CArrayRowset
- CArrayRowset::CArrayRowset
- CArrayRowset<TAccessor>::CArrayRowset
- ATL::CArrayRowset<TAccessor>::CArrayRowset
- CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset::Snapshot
- Snapshot
- CArrayRowset<TAccessor>::Snapshot
- ATL.CArrayRowset.Snapshot
- ATL.CArrayRowset<TAccessor>.Snapshot
- ATL::CArrayRowset<TAccessor>::Snapshot
- CArrayRowset::Snapshot
- CArrayRowset.Snapshot
- CArrayRowset::operator[]
- CArrayRowset.operator[]
- ATL::CArrayRowset::m_nRowsRead
- ATL::CArrayRowset<TAccessor>::m_nRowsRead
- CArrayRowset<TAccessor>::m_nRowsRead
- ATL.CArrayRowset<TAccessor>.m_nRowsRead
- CArrayRowset.m_nRowsRead
- m_nRowsRead
- ATL.CArrayRowset.m_nRowsRead
- CArrayRowset::m_nRowsRead
helpviewer_keywords:
- CArrayRowset class
- CArrayRowset class, constructor
- Snapshot method
- operator [], arrays
- '[] operator'
- operator[], arrays
- m_nRowsRead
ms.assetid: 511427e1-73ca-4fd8-9ba1-ae9463557cb6
ms.openlocfilehash: 66b7607eb28392196f6b7d3790aee976a861f2b6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545616"
---
# <a name="carrayrowset-class"></a>CArrayRowset (Clase)

Obtiene acceso a los elementos de un conjunto de filas mediante la sintaxis de la matriz.

## <a name="syntax"></a>Sintaxis

```cpp
template < class TAccessor >
class CArrayRowset :
   public CVirtualBuffer <TAccessor>,
   protected CBulkRowset <TAccessor>
```

### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
Tipo de clase de descriptor de acceso que se desea que utilice el conjunto de filas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[CArrayRowset](#carrayrowset)|Constructor.|
|[Instantánea](#snapshot)|Lee el conjunto de filas completo en la memoria.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[Operator&#91;&#93;](#operator)|Obtiene acceso a un elemento del conjunto de filas.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[CArrayRowset::m_nRowsRead](#nrowsread)|Número de filas ya leídas.|

## <a name="carrayrowsetcarrayrowset"></a><a name="carrayrowset"></a>CArrayRowset:: CArrayRowset

Crea un nuevo objeto `CArrayRowset`.

### <a name="syntax"></a>Sintaxis

```cpp
CArrayRowset(int nMax = 100000);
```

#### <a name="parameters"></a>Parámetros

*Nmáx.*<br/>
de Número máximo de filas del conjunto de filas.

## <a name="carrayrowsetsnapshot"></a><a name="snapshot"></a>CArrayRowset:: Snapshot

Lee el conjunto de filas completo en la memoria, creando una imagen o una instantánea del mismo.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Snapshot() throw();
```

## <a name="carrayrowsetoperator"></a><a name="operator"></a>CArrayRowset:: Operator

Proporciona una sintaxis similar a la de la matriz para tener acceso a una fila del conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
TAccessor & operator[](int nrow);
```

#### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
Parámetro de plantilla que especifica el tipo de descriptor de acceso almacenado en el conjunto de filas.

*nRow*<br/>
de Número de la fila (elemento de matriz) a la que se desea obtener acceso.

### <a name="return-value"></a>Valor devuelto

Contenido de la fila solicitada.

### <a name="remarks"></a>Observaciones

Si *nRow* supera el número de filas del conjunto de filas, se produce una excepción.

## <a name="carrayrowsetm_nrowsread"></a><a name="nrowsread"></a>CArrayRowset:: m_nRowsRead

Contiene el número de filas del conjunto de filas que ya se han leído.

### <a name="syntax"></a>Sintaxis

```cpp
ULONG m_nRowsRead;
```

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CRowset (Clase)](../../data/oledb/crowset-class.md)