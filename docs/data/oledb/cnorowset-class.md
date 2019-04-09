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
ms.openlocfilehash: 6193e2d461761c53fb05e5c16b3914c56d545173
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035681"
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
Una clase de descriptor de acceso. De manera predeterminada, es `CAccessorBase`.

## <a name="remarks"></a>Comentarios

Use `CNoRowset` como argumento de plantilla si el comando no devuelve un conjunto de filas.

`CNoRowset` implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponde a otros métodos de clase de descriptor de acceso:

- `BindFinished` : Indica cuando el enlace está completando (devuelve `S_OK`).

- `Close` -Libera las filas y la interfaz IRowset actual.

- `GetIID` -Recupera el identificador de interfaz de un punto de conexión.

- `GetInterface` -Recupera una interfaz.

- `GetInterfacePtr` -Recupera un puntero de interfaz encapsulado.

- `SetAccessor` -Establece un puntero al descriptor de acceso.

- `SetupOptionalRowsetInterfaces` -Configura interfaces opcionales para el conjunto de filas.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)