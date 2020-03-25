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
ms.openlocfilehash: 300933fd6d10f5da39d9276db746ab789851a9a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211177"
---
# <a name="cstreamrowset-class"></a>CStreamRowset (Clase)

Se utiliza en una declaración de `CCommand` o `CTable`.

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

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[CStreamRowset (](#cstreamrowset)|Constructor. Crea una instancia e inicializa el objeto `CStreamRowset`.|
|[Close](#close)|Libera el puntero de la interfaz [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) en la clase.|

## <a name="remarks"></a>Observaciones

Use `CStreamRowset` en la declaración de `CCommand` o `CTable`, por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

or

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` devuelve un puntero `ISequentialStream`, que se almacena en `m_spStream`. A continuación, use el método `Read` para recuperar los datos de (cadena Unicode) en formato XML. Por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 realiza el formato XML y devolverá todas las columnas y todas las filas del conjunto de filas como una cadena XML.

> [!NOTE]
>  Esta característica solo funciona con SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset:: CStreamRowset

Crea una instancia e inicializa el objeto `CStreamRowset`.

### <a name="syntax"></a>Sintaxis

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset:: Close

Libera el puntero de la interfaz [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) en la clase.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
