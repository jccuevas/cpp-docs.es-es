---
title: CNoRowset (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 19a1e01fd29c74cf1c44081c24bf384704cf2acd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211478"
---
# <a name="cnorowset-class"></a>CNoRowset (Clase)

Se puede usar como un argumento de plantilla (`TRowset`) para [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md).

## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
Una clase de descriptor de acceso. El valor predeterminado es `CAccessorBase`.

## <a name="remarks"></a>Observaciones

Use `CNoRowset` como argumento de plantilla si el comando no devuelve un conjunto de filas.

`CNoRowset` implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponde a otros métodos de clase de descriptor de acceso:

- `BindFinished`: indica cuándo se completa el enlace (devuelve `S_OK`).

- `Close`: libera las filas y la interfaz IRowset actual.

- `GetIID`: recupera el identificador de interfaz de un punto de conexión.

- `GetInterface`: recupera una interfaz.

- `GetInterfacePtr`: recupera un puntero de interfaz encapsulado.

- `SetAccessor`: establece un puntero al descriptor de acceso.

- `SetupOptionalRowsetInterfaces`: configura interfaces opcionales para el conjunto de filas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
