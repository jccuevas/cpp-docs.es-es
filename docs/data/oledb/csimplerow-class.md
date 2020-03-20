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
ms.openlocfilehash: 00d8164425ada573020971f66312b2282cc72c45
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545568"
---
# <a name="csimplerow-class"></a>CSimpleRow (Clase)

Proporciona una implementación predeterminada para el identificador de fila, que se usa en la clase [IRowsetImpl](../../data/oledb/irowsetimpl-class.md) .

## <a name="syntax"></a>Sintaxis

```cpp
class CSimpleRow
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddRefRow](#addrefrow)|Agrega un contador de referencias a un identificador de fila existente.|
|[Comparar](#compare)|Compara dos filas para ver si hacen referencia a la misma instancia de fila.|
|[CSimpleRow](#csimplerow)|El constructor.|
|[ReleaseRow](#releaserow)|Libera filas.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_dwRef](#dwref)|Recuento de referencias a un identificador de fila existente.|
|[m_iRowset](#irowset)|Índice del conjunto de filas que representa el cursor.|

## <a name="remarks"></a>Observaciones

Un identificador de fila es lógicamente una etiqueta única para una fila de resultados. `IRowsetImpl` crea un `CSimpleRow` nuevo para cada fila solicitada en [IRowsetImpl:: GetNextRows](../../data/oledb/irowsetimpl-getnextrows.md). `CSimpleRow` también se pueden reemplazar por su propia implementación del identificador de fila, ya que se trata de un argumento de plantilla predeterminado que se va a `IRowsetImpl`. El único requisito para reemplazar esta clase es hacer que la clase de reemplazo proporcione un constructor que acepte un parámetro único de tipo **Long**.

## <a name="csimplerowaddrefrow"></a><a name="addrefrow"></a>CSimpleRow:: AddRefRow

Agrega un recuento de referencias a un identificador de fila existente de una manera segura para subprocesos.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD AddRefRow();
```

## <a name="csimplerowcompare"></a><a name="compare"></a>CSimpleRow:: Compare

Compara dos filas para ver si hacen referencia a la misma instancia de fila.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Compare(CSimpleRow* pRow);
```

#### <a name="parameters"></a>Parámetros

*pRow*<br/>
Puntero a un objeto `CSimpleRow` .

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT, normalmente S_OK, que indica que las dos filas son la misma instancia de fila, o S_FALSE, que indica que las dos filas son diferentes. Vea [IRowsetIdentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) en la *Referencia del programador de OLE DB* para ver otros posibles valores devueltos.

## <a name="csimplerowcsimplerow"></a><a name="csimplerow"></a>CSimpleRow:: CSimpleRow

El constructor.

### <a name="syntax"></a>Sintaxis

```cpp
CSimpleRow(DBCOUNTITEM iRowsetCur);
```

#### <a name="parameters"></a>Parámetros

*iRowsetCur*<br/>
de Índice del conjunto de filas actual.

### <a name="remarks"></a>Observaciones

Establece [m_iRowset](../../data/oledb/csimplerow-m-irowset.md) en *iRowsetCur*.

## <a name="csimplerowreleaserow"></a><a name="releaserow"></a>CSimpleRow:: ReleaseRow

Libera filas de una manera segura para subprocesos.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD ReleaseRow();
```

## <a name="csimplerowm_dwref"></a><a name="dwref"></a>CSimpleRow:: m_dwRef

Recuento de referencias a un identificador de fila existente.

### <a name="syntax"></a>Sintaxis

```cpp
DWORD m_dwRef;
```

## <a name="csimplerowm_irowset"></a><a name="irowset"></a>CSimpleRow:: m_iRowset

Índice del conjunto de filas que representa el cursor.

### <a name="syntax"></a>Sintaxis

```cpp
KeyType m_iRowset;
```

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)