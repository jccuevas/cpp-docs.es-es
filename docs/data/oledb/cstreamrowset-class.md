---
title: CStreamRowset (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
ms.openlocfilehash: ad4987422fd200faef141150908d4df0722f669a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366274"
---
# <a name="cstreamrowset-class"></a>CStreamRowset (Clase)

Se utiliza `CCommand` `CTable` en una declaración o una declaración.

## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
Una clase de descriptor de acceso.

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|Constructor. Crea una instancia `CStreamRowset` e inicializa el objeto.|
|[Cerrar](#close)|Libera el puntero de interfaz [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) en la clase.|

## <a name="remarks"></a>Observaciones

Utilícelo `CStreamRowset` en `CCommand` `CTable` su declaración o en su declaración, por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

or

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute`devuelve `ISequentialStream` un puntero, que `m_spStream`se almacena en . A continuación, `Read` utilice el método para recuperar los datos (cadena Unicode) en formato XML. Por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 realiza el formato XML y devolverá todas las columnas y todas las filas del conjunto de filas como una cadena XML.

> [!NOTE]
> Esta característica solo funciona con SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset::CStreamRowset

Crea una instancia `CStreamRowset` e inicializa el objeto.

### <a name="syntax"></a>Sintaxis

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset::Close

Libera el puntero de interfaz [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) en la clase.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
