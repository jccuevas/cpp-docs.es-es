---
title: CAccessorRowset (Clase)
ms.date: 11/04/2016
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
helpviewer_keywords:
- CAccessorRowset class
- CAccessorRowset class, methods
- CAccessorRowset class, members
- Bind method
- CAccessorRowset class, constructor
- Close method
- FreeRecordMemory method
- GetColumnInfo method
ms.assetid: bd4f58ed-cebf-4d43-8985-1e5fcbf06953
ms.openlocfilehash: 77c4eebae6ede5d74e24421cc4d3951c78e08777
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546024"
---
# <a name="caccessorrowset-class"></a>CAccessorRowset (Clase)

Encapsula un conjunto de filas y sus descriptores de acceso asociados en una sola clase.

## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset>
class CAccessorRowset : public TAccessor, public TRowset<TAccessor>
```

### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
Una clase de descriptor de acceso.

*TRowset*<br/>
Una clase de conjunto de filas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Bind](#bind)|Crea enlaces (se usa cuando se especifica `bBind` como **false** en [CCommand:: Open](../../data/oledb/ccommand-open.md)).|
|[Caccessorrowset (](#caccessorrowset)|Constructor.|
|[Close](#close)|Cierra el conjunto de filas y los descriptores de acceso.|
|[FreeRecordMemory](#freerecordmemory)|Libera todas las columnas del registro actual que se deben liberar.|
|[GetColumnInfo](#getcolumninfo)|Implementa [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)).|

## <a name="remarks"></a>Observaciones

La clase `TAccessor` administra el descriptor de acceso. La clase *TRowset* administra el conjunto de filas.

## <a name="caccessorrowsetbind"></a><a name="bind"></a>CAccessorRowset:: Bind

Crea los enlaces si se especifica `bBind` como **false** en [CCommand:: Open](../../data/oledb/ccommand-open.md).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="caccessorrowsetcaccessorrowset"></a><a name="caccessorrowset"></a>CAccessorRowset:: CAccessorRowset

Inicializa el objeto `CAccessorRowset`.

### <a name="syntax"></a>Sintaxis

```cpp
CAccessorRowset();
```

## <a name="caccessorrowsetclose"></a><a name="close"></a>CAccessorRowset:: Close

Libera todos los descriptores de acceso activos y el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

### <a name="remarks"></a>Observaciones

Libera cualquier memoria asociada.

## <a name="caccessorrowsetfreerecordmemory"></a><a name="freerecordmemory"></a>CAccessorRowset:: FreeRecordMemory

Libera todas las columnas del registro actual que se deben liberar.

### <a name="syntax"></a>Sintaxis

```cpp
void FreeRecordMemory();
```

## <a name="caccessorrowsetgetcolumninfo"></a><a name="getcolumninfo"></a>CAccessorRowset:: GetColumnInfo

Obtiene la información de columna del conjunto de filas abierto.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>Parámetros

Vea [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

El usuario debe liberar la información de columna y el búfer de cadena devueltos. Use la segunda versión de este método cuando use [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) y necesite invalidar los enlaces.

Para obtener más información, vea [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en la *Referencia del programador de OLE DB*.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)