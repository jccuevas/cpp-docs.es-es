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
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
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
ms.openlocfilehash: e2fced2ed0e32af15e75c7290733fdc2b4b34dc9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546126"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet (Clase)

Hereda de la estructura `DBPROPIDSET` y agrega un constructor que inicializa los campos clave, así como el método de acceso [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) .

## <a name="syntax"></a>Sintaxis

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Agrega una propiedad al conjunto de IDENTIFICADOres de propiedad.|
|[CDBPropIDSet](#cdbpropidset)|Constructor.|
|[SetGUID](#setguid)|Establece el GUID del conjunto de IDENTIFICADOres de propiedad.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#op_equal)|Asigna el contenido de un identificador de propiedad establecido en otro.|

## <a name="remarks"></a>Observaciones

OLE DB consumidores usan estructuras `DBPROPIDSET` para pasar una matriz de identificadores de propiedad para los que el consumidor desea obtener información de propiedades. Las propiedades identificadas en una única estructura [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) pertenecen a un conjunto de propiedades.

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a>CDBPropIDSet:: AddPropertyID

Agrega un identificador de propiedad al conjunto de IDENTIFICADOres de propiedad.

### <a name="syntax"></a>Sintaxis

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parámetros

*PROPID*<br/>
de IDENTIFICADOR de propiedad que se va a agregar al conjunto de IDENTIFICADOres de propiedad.

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a>CDBPropIDSet:: CDBPropIDSet

El constructor. Inicializa el `rgProperties`, `cProperties`y, opcionalmente, `guidPropertySet` campos de la estructura [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parámetros

*guid*<br/>
de GUID que se usa para inicializar el campo de `guidPropertySet`.

*propidset*<br/>
de Otro objeto `CDBPropIDSet` para la construcción de copia.

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a>CDBPropIDSet:: SetGUID

Establece el campo GUID en la estructura de `DBPROPIDSET`.

### <a name="syntax"></a>Sintaxis

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parámetros

*guid*<br/>
de GUID que se usa para establecer el `guidPropertySet` campo de la estructura [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) .

### <a name="remarks"></a>Observaciones

Este campo también se puede establecer mediante el [constructor](../../data/oledb/cdbpropidset-cdbpropidset.md) . Llame a esta función si usa el constructor predeterminado para esta clase.

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a>CDBPropIDSet:: Operator =

Asigna el contenido de un identificador de propiedad establecido en otro conjunto de propiedades de identificador.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)