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
ms.openlocfilehash: 5fb39d2291c2698dc57150eb44a6bbd6778812bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509313"
---
# <a name="caccessorbase-class"></a>CAccessorBase (Clase)

Todos los descriptores de acceso de las plantillas OLE DB que se derivan de esta clase. `CAccessorBase` permite que un conjunto de filas administrar varios descriptores de acceso. También proporciona enlaces para los parámetros y columnas de salida.

## <a name="syntax"></a>Sintaxis

```cpp
// Replace with syntax
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Cerrar](#close)|Cierra los descriptores de acceso.|
|[GetHAccessor](#geth)|Recupera el identificador de descriptor de acceso.|
|[GetNumAccessors](#getnum)|Recupera el número de descriptores de acceso creado por la clase.|
|[IsAutoAccessor](#isauto)|Comprueba si el descriptor de acceso especificada es autoaccessor.|
|[ReleaseAccessors](#release)|Libera los descriptores de acceso.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="close"></a> CAccessorBase:: Close

Cierra los descriptores de acceso.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

### <a name="remarks"></a>Comentarios

Debe llamar a [ReleaseAccessors](../../data/oledb/caccessorbase-releaseaccessors.md) primero.

## <a name="geth"></a> CAccessorBase:: Gethaccessor

Recupera el identificador de descriptor de acceso de un descriptor de acceso especificada.

### <a name="syntax"></a>Sintaxis

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parámetros

*nAccessor*<br/>
[in] El número de desplazamiento de cero para el descriptor de acceso.

### <a name="return-value"></a>Valor devuelto

El identificador de descriptor de acceso.

## <a name="getnum"></a> CAccessorBase:: Getnumaccessors

Recupera el número de descriptores de acceso creado por la clase.

### <a name="syntax"></a>Sintaxis

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Valor devuelto

El número de descriptores de acceso creado por la clase.

## <a name="isauto"></a> CAccessorBase:: Isautoaccessor

Devuelve true si se recuperan automáticamente los datos para el descriptor de acceso durante una operación de movimiento.

### <a name="syntax"></a>Sintaxis

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parámetros

*nAccessor*<br/>
[in] El número de desplazamiento de cero para el descriptor de acceso.

### <a name="return-value"></a>Valor devuelto

Devuelve **true** si el descriptor de acceso es autoaccessor. En caso contrario, devuelve **false**.

## <a name="release"></a> CAccessorBase:: Releaseaccessors

Libera los descriptores de acceso creados por la clase.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parámetros

*pUnk*<br/>
[in] Un puntero a un `IUnknown` interfaz para el objeto COM para el que se han creado los descriptores de acceso.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Se llama desde [CAccessorRowset:: Close](../../data/oledb/caccessorrowset-close.md).

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase (Clase)](../../data/oledb/caccessorbase-class.md)