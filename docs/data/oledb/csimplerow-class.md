---
title: CSimpleRow (Clase)
ms.date: 11/04/2016
f1_keywords:
- CSimpleRow
- ATL::CSimpleRow
- ATL.CSimpleRow
- CSimpleRow::AddRefRow
- AddRefRow
- ATL.CSimpleRow.AddRefRow
- ATL::CSimpleRow::AddRefRow
- CSimpleRow.AddRefRow
- CSimpleRow.Compare
- CSimpleRow::Compare
- CSimpleRow
- ATL::CSimpleRow::CSimpleRow
- CSimpleRow.CSimpleRow
- ATL.CSimpleRow.CSimpleRow
- CSimpleRow::CSimpleRow
- ATL::CSimpleRow::ReleaseRow
- CSimpleRow::ReleaseRow
- ReleaseRow
- CSimpleRow.ReleaseRow
- ATL.CSimpleRow.ReleaseRow
- CSimpleRow.m_dwRef
- CSimpleRow::m_dwRef
- CSimpleRow::m_iRowset
- CSimpleRow.m_iRowset
helpviewer_keywords:
- CSimpleRow class
- AddRefRow method
- Compare method
- CSimpleRow class, constructor
- ReleaseRow method
- m_dwRef
- m_iRowset
ms.assetid: 06d9621d-60cc-4508-8b0c-528d1b1a809b
ms.openlocfilehash: dba86b310dcd9b89026d95732f9ca542e6995146
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556639"
---
# <a name="csimplerow-class"></a>CSimpleRow (Clase)

Proporciona una implementación predeterminada para el identificador de fila, que se utiliza en el [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) clase.

## <a name="syntax"></a>Sintaxis

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRefRow](#addrefrow)|Agrega un contador de referencia a un identificador de fila existente.|
|[Compare](#compare)|Compara dos filas para ver si hacen referencia a la misma instancia de fila.|
|[CSimpleRow](#csimplerow)|El constructor.|
|[ReleaseRow](#releaserow)|Libera filas.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_dwRef](#dwref)|Recuento de referencias a un identificador de fila existente.|
|[m_iRowset](#irowset)|Un índice al conjunto de filas que representa el cursor.|

## <a name="remarks"></a>Comentarios

Identificador de fila es, lógicamente, una etiqueta única para una fila de resultados. `IRowsetImpl` crea un nuevo `CSimpleRow` para todas las filas solicitaron en [IRowsetImpl:: GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` También se puede reemplazar por su propia implementación del identificador de fila, ya que es un argumento de plantilla predeterminado a `IRowsetImpl`. El único requisito para reemplazar esta clase es que la clase de reemplazo proporciona un constructor que acepta un único parámetro de tipo **largo**.

## <a name="addrefrow"></a> Csimplerow:: Addrefrow

Agrega un contador de referencia a un identificador de fila existente de una manera segura para subprocesos.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD AddRefRow();
```

## <a name="compare"></a> Csimplerow:: Compare

Compara dos filas para ver si hacen referencia a la misma instancia de fila.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Parámetros

*pRow*<br/>
Puntero a un objeto `CSimpleRow` .

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT, normalmente S_OK, que indica las dos filas son la misma instancia de fila o S_FALSE, que indica las dos filas son diferentes. Consulte [IRowsetIdentity::IsSameRow](https://docs.microsoft.com/previous-versions/windows/desktop/ms719629(v=vs.85)) en el *referencia del programador de OLE DB* para otros posibles valores devueltos.

## <a name="csimplerow"></a> Csimplerow:: Csimplerow

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Parámetros

*iRowsetCur*<br/>
[in] Índice de filas actual.

### <a name="remarks"></a>Comentarios

Conjuntos de [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) a *iRowsetCur*.

## <a name="releaserow"></a> Csimplerow:: Releaserow

Libera las filas de una manera segura para subprocesos.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD ReleaseRow();
```

## <a name="dwref"></a> Csimplerow:: M_dwref

Recuento de referencias a un identificador de fila existente.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD m_dwRef;
```

## <a name="irowset"></a> Csimplerow:: M_irowset

Índice al conjunto de filas que representa el cursor.

### <a name="syntax"></a>Sintaxis

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Vea también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)