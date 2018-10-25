---
title: CDBPropIDSet (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6ab6e58ad6f25232be5c298673cefe6d0488f63b
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083105"
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

Uso de los consumidores de OLE DB `DBPROPIDSET` estructuras para pasar una matriz de identificadores de propiedad para el que el consumidor desea obtener información de la propiedad. Las propiedades identificadas en un único [DBPROPIDSET](/previous-versions/windows/desktop/ms717981) estructura pertenecen a una propiedad establecida.

## <a name="addpropertyid"></a> Cdbpropidset:: Addpropertyid

Agrega un identificador de propiedad para el conjunto de Id. de propiedad.

### <a name="syntax"></a>Sintaxis

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parámetros

*PROPID*<br/>
[in] Establece el identificador de propiedad que se agregarán al identificador de propiedad.

## <a name="cdbpropidset"></a> Cdbpropidset:: Cdbpropidset

El constructor. Inicializa el `rgProperties`, `cProperties`y (opcionalmente) `guidPropertySet` campos de la [DBPROPIDSET](/previous-versions/windows/desktop/ms717981) estructura.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parámetros

*GUID*<br/>
[in] Un GUID que se usa para inicializar el `guidPropertySet` campo.

*propidset*<br/>
[in] Otro `CDBPropIDSet` objeto para la construcción de copia.

## <a name="setguid"></a> Cdbpropidset:: SetGuid

Establece el campo GUID de la `DBPROPIDSET` estructura.

### <a name="syntax"></a>Sintaxis

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parámetros

*GUID*<br/>
[in] Un GUID que se usa para establecer el `guidPropertySet` campo de la [DBPROPIDSET](/previous-versions/windows/desktop/ms717981) estructura.

### <a name="remarks"></a>Comentarios

Este campo se puede establecer el [constructor](../../data/oledb/cdbpropidset-cdbpropidset.md) también. Si utiliza el constructor predeterminado para esta clase, llame a esta función.

## <a name="op_equal"></a> Cdbpropidset:: operator =

Asigna el contenido de Id. de una propiedad establecida en otro conjunto de propiedades de identificador.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)