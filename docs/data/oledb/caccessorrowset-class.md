---
title: CAccessorRowset (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CAccessorRowset
- ATL.CAccessorRowset
- ATL::CAccessorRowset
- CAccessorRowset.Bind
- CAccessorRowset::Bind
- CAccessorRowset::CAccessorRowset
- CAccessorRowset.CAccessorRowset
- CAccessorRowset
- ATL.CAccessorRowset.CAccessorRowset
- ATL::CAccessorRowset::CAccessorRowset
- CAccessorRowset.Close
- CAccessorRowset::Close
- CAccessorRowset::FreeRecordMemory
- CAccessorRowset.FreeRecordMemory
- FreeRecordMemory
- GetColumnInfo
- CAccessorRowset.GetColumnInfo
- CAccessorRowset::GetColumnInfo
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: adb59e553565d9886cf27b55f2cfffb4cd0e7aa9
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060161"
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

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Bind](#bind)|Crea los enlaces (se usa cuando `bBind` se especifica como **false** en [CCommand:: Open](../../data/oledb/ccommand-open.md)).|
|[CAccessorRowset](#caccessorrowset)|Constructor.|
|[Cerrar](#close)|Cierra el conjunto de filas y los descriptores de acceso.|
|[FreeRecordMemory](#freerecordmemory)|Libera las columnas en el registro actual que necesitan ser liberados.|
|[GetColumnInfo](#getcolumninfo)|Implementa [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704).|

## <a name="remarks"></a>Comentarios

Clase `TAccessor` administra el descriptor de acceso. Clase *TRowset* administra el conjunto de filas.

## <a name="bind"></a> CAccessorRowset:: Bind

Crea los enlaces si especifica `bBind` como **false** en [CCommand:: Open](../../data/oledb/ccommand-open.md).

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Bind();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="caccessorrowset"></a> CAccessorRowset:: CAccessorRowset

Inicializa el objeto `CAccessorRowset`.

### <a name="syntax"></a>Sintaxis

```cpp
CAccessorRowset();
```

## <a name="close"></a> CAccessorRowset:: Close

Libera los descriptores de acceso activos y el conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

### <a name="remarks"></a>Comentarios

Libera la memoria asociada.

## <a name="freerecordmemory"></a> CAccessorRowset:: Freerecordmemory

Libera las columnas en el registro actual que necesitan ser liberados.

### <a name="syntax"></a>Sintaxis

```cpp
void FreeRecordMemory();
```

## <a name="getcolumninfo"></a> CAccessorRowset:: GetColumnInfo

Obtiene información de columna del conjunto de filas abierto.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetColumnInfo(DBORDINAL* pulColumns,
   DBCOLUMNINFO** ppColumnInfo,
   LPOLESTR* ppStrings) const;

HRESULT GetColumnInfo(DBORDINAL* pColumns,
   DBCOLUMNINFO** ppColumnInfo);
```

#### <a name="parameters"></a>Parámetros

Consulte [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

El usuario debe liberar el búfer de cadena y la información de la columna devuelta. Use la segunda versión de este método cuando se usa [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) y necesita reemplazar los enlaces.

Para obtener más información, consulte [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704) en el *referencia del programador de OLE DB*.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)