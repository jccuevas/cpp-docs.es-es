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
- CStreamRowset
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
ms.openlocfilehash: b566ddab89d2198e3f6b24eb9a20c60747749d1a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59022585"
---
# <a name="cstreamrowset-class"></a>CStreamRowset (Clase)

Utilizado en un `CCommand` o `CTable` declaración.

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
|[CStreamRowset](#cstreamrowset)|Constructor. Crea una instancia e inicializa el `CStreamRowset` objeto.|
|[Cerrar](#close)|Las versiones del [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) puntero de interfaz en la clase.|

## <a name="remarks"></a>Comentarios

Use `CStreamRowset` en su `CCommand` o `CTable` declaración, por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

o

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` Devuelve un `ISequentialStream` puntero, que se almacena en `m_spStream`. A continuación, usa el `Read` método para recuperar los datos (cadena Unicode) en formato XML. Por ejemplo:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 realiza la aplicación de formato XML y devolverá todas las columnas y todas las filas del conjunto de filas como una cadena XML.

> [!NOTE]
>  Esta característica solo funciona con SQL Server 2000.

## <a name="cstreamrowset"></a> CStreamRowset::CStreamRowset

Crea una instancia e inicializa el `CStreamRowset` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
CStreamRowset();
```

## <a name="close"></a> CStreamRowset::Close

Las versiones del [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) puntero de interfaz en la clase.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)