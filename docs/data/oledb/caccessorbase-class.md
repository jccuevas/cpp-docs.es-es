---
title: CAccessorBase (Clase)
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 8aef8a04d7adff903e21491a91014d55aab769da
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212297"
---
# <a name="caccessorbase-class"></a>CAccessorBase (Clase)

Todos los descriptores de acceso de las plantillas de OLE DB derivan de esta clase. `CAccessorBase` permite que un conjunto de filas administre varios descriptores de acceso. También proporciona enlaces para los parámetros y las columnas de salida.

## <a name="syntax"></a>Sintaxis

```cpp
// Replace with syntax
```

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Close](#close)|Cierra los descriptores de acceso.|
|[GetHAccessor](#geth)|Recupera el identificador del descriptor de acceso.|
|[GetNumAccessors](#getnum)|Recupera el número de descriptores de acceso creados por la clase.|
|[IsAutoAccessor](#isauto)|Comprueba si el descriptor de acceso especificado es un autoscriptor.|
|[ReleaseAccessors](#release)|Libera los descriptores de acceso.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="caccessorbaseclose"></a><a name="close"></a>CAccessorBase:: Close

Cierra los descriptores de acceso.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

### <a name="remarks"></a>Observaciones

Primero debe llamar a [ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) .

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a>CAccessorBase:: GetHAccessor

Recupera el identificador de descriptor de acceso de un descriptor de acceso especificado.

### <a name="syntax"></a>Sintaxis

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parámetros

*nAccessor*<br/>
de Número de desplazamiento cero para el descriptor de acceso.

### <a name="return-value"></a>Valor devuelto

Identificador del descriptor de acceso.

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a>CAccessorBase:: GetNumAccessors

Recupera el número de descriptores de acceso creados por la clase.

### <a name="syntax"></a>Sintaxis

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Valor devuelto

El número de descriptores de acceso creados por la clase.

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a>CAccessorBase:: IsAutoAccessor

Devuelve true si los datos se recuperan automáticamente para el descriptor de acceso durante una operación de movimiento.

### <a name="syntax"></a>Sintaxis

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parámetros

*nAccessor*<br/>
de Número de desplazamiento cero para el descriptor de acceso.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si el descriptor de acceso es un autoscriptor. En caso contrario, devuelve **false**.

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a>CAccessorBase:: ReleaseAccessors

Libera los descriptores de acceso creados por la clase.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parámetros

*pUnk*<br/>
de Puntero a una interfaz de `IUnknown` para el objeto COM para el que se han creado los descriptores de acceso.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Se llama desde [CAccessorRowset:: Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase (Clase)](../../data/oledb/caccessorbase-class.md)
