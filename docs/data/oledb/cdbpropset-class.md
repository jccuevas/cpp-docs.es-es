---
title: CDBPropSet (Clase)
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: 08cab967fbfbd4b3207e96a4fdbd2d2dbc6da793
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546120"
---
# <a name="cdbpropset-class"></a>CDBPropSet (Clase)

Hereda de la estructura `DBPROPSET` y agrega un constructor que inicializa los campos clave, así como el método de acceso `AddProperty`.

## <a name="syntax"></a>Sintaxis

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddProperty](#addproperty)|Agrega una propiedad al conjunto de propiedades.|
|[CDBPropSet](#cdbpropset)|Constructor.|
|[SetGUID](#setguid)|Establece el campo de `guidPropertySet` de la estructura de `DBPROPSET`.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#op_equal)|Asigna el contenido de un conjunto de propiedades a otro.|

## <a name="remarks"></a>Observaciones

OLE DB proveedores y consumidores usan estructuras de `DBPROPSET` para pasar matrices de estructuras `DBPROP`. Cada estructura de `DBPROP` representa una propiedad única que se puede establecer.

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a>CDBPropSet:: AddProperty

Agrega una propiedad al conjunto de propiedades.

### <a name="syntax"></a>Sintaxis

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>Parámetros

*dwPropertyID*<br/>
de IDENTIFICADOR de la propiedad que se va a agregar. Se utiliza para inicializar el `dwPropertyID` de la estructura de `DBPROP` agregada al conjunto de propiedades.

*var*<br/>
de Variant que se usa para inicializar el valor de propiedad de la estructura de `DBPROP` agregada al conjunto de propiedades.

*szValue*<br/>
de Cadena que se usa para inicializar el valor de propiedad de la estructura `DBPROP` agregada al conjunto de propiedades.

*bValue*<br/>
de `BYTE` o valor booleano que se usa para inicializar el valor de propiedad de la estructura de `DBPROP` agregada al conjunto de propiedades.

*Nvalor*<br/>
de Valor entero que se usa para inicializar el valor de propiedad de la estructura de `DBPROP` agregada al conjunto de propiedades.

*fltValue*<br/>
de Un valor de punto flotante que se usa para inicializar el valor de propiedad de la estructura de `DBPROP` agregada al conjunto de propiedades.

*dblValue*<br/>
de Un valor de punto flotante de precisión doble que se usa para inicializar el valor de propiedad de la estructura de `DBPROP` agregada al conjunto de propiedades.

*cyValue*<br/>
de Valor de moneda CY que se usa para inicializar el valor de propiedad de la estructura de `DBPROP` agregada al conjunto de propiedades.

### <a name="return-value"></a>Valor devuelto

**true** si la propiedad se agregó correctamente. De lo contrario, se devuelve el valor **False**.

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a>CDBPropSet:: CDBPropSet

El constructor. Inicializa los campos `rgProperties`, `cProperties`y `guidPropertySet` de la estructura [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) .

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Parámetros

*guid*<br/>
de GUID que se usa para inicializar el campo de `guidPropertySet`.

*propset*<br/>
de Otro objeto `CDBPropSet` para la construcción de copia.

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a>CDBPropSet:: SetGUID

Establece el campo de `guidPropertySet` en la estructura de `DBPROPSET`.

### <a name="syntax"></a>Sintaxis

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parámetros

*guid*<br/>
de GUID que se usa para establecer el `guidPropertySet` campo de la estructura [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) .

### <a name="remarks"></a>Observaciones

Este campo también se puede establecer mediante el [constructor](../../data/oledb/cdbpropset-cdbpropset.md) .

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a>CDBPropSet:: Operator =

Asigna el contenido de un conjunto de propiedades a otro conjunto de propiedades.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet (Clase)](../../data/oledb/cdbpropidset-class.md)<br/>
Estructura [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))
[estructura DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85))