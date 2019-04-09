---
title: CDBPropIDSet (Clase)
ms.date: 11/04/2016
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
ms.openlocfilehash: 9e878af3acf4c4d3a6ca785454c4bb072f17cf09
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022416"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet (Clase)

Hereda el `DBPROPIDSET` estructurar y agrega un constructor que inicializa los campos de clave, así como la [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) obtener acceso a método.

## <a name="syntax"></a>Sintaxis

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Agrega una propiedad para el conjunto de Id. de propiedad.|
|[CDBPropIDSet](#cdbpropidset)|Constructor.|
|[SetGUID](#setguid)|Establece el GUID del identificador de propiedad de conjunto.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#op_equal)|Asigna el contenido de Id. de propiedad de un juego a otro.|

## <a name="remarks"></a>Comentarios

Uso de los consumidores de OLE DB `DBPROPIDSET` estructuras para pasar una matriz de identificadores de propiedad para el que el consumidor desea obtener información de la propiedad. Las propiedades identificadas en un único [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) estructura pertenecen a una propiedad establecida.

## <a name="addpropertyid"></a> CDBPropIDSet::AddPropertyID

Agrega un identificador de propiedad para el conjunto de Id. de propiedad.

### <a name="syntax"></a>Sintaxis

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parámetros

*propid*<br/>
[in] Establece el identificador de propiedad que se agregarán al identificador de propiedad.

## <a name="cdbpropidset"></a> CDBPropIDSet::CDBPropIDSet

El constructor. Inicializa el `rgProperties`, `cProperties`y (opcionalmente) `guidPropertySet` campos de la [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) estructura.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parámetros

*guid*<br/>
[in] Un GUID que se usa para inicializar el `guidPropertySet` campo.

*propidset*<br/>
[in] Otro `CDBPropIDSet` objeto para la construcción de copia.

## <a name="setguid"></a> CDBPropIDSet::SetGUID

Establece el campo GUID de la `DBPROPIDSET` estructura.

### <a name="syntax"></a>Sintaxis

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parámetros

*guid*<br/>
[in] Un GUID que se usa para establecer el `guidPropertySet` campo de la [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) estructura.

### <a name="remarks"></a>Comentarios

Este campo se puede establecer el [constructor](../../data/oledb/cdbpropidset-cdbpropidset.md) también. Si utiliza el constructor predeterminado para esta clase, llame a esta función.

## <a name="op_equal"></a> CDBPropIDSet::operator =

Asigna el contenido de Id. de una propiedad establecida en otro conjunto de propiedades de identificador.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)