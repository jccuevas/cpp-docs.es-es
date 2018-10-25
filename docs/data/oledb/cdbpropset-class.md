---
title: CDBPropSet (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
- SetGUID
- CDBPropSet::SetGUID
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a047416c22eb57fc3ee3d3eb6a69275768182525
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50081906"
---
# <a name="cdbpropset-class"></a>CDBPropSet (Clase)

Hereda el `DBPROPSET` estructurar y agrega un constructor que inicializa los campos de clave, así como la `AddProperty` obtener acceso a método.

## <a name="syntax"></a>Sintaxis

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddProperty](#addproperty)|Agrega una propiedad para el conjunto de propiedades.|
|[CDBPropSet](#cdbpropset)|Constructor.|
|[SetGUID](#setguid)|Establece el `guidPropertySet` campo de la `DBPROPSET` estructura.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador =](#op_equal)|Asigna el contenido de una propiedad establecida en otro.|

## <a name="remarks"></a>Comentarios

Uso de consumidores y proveedores OLE DB `DBPROPSET` estructuras para pasar matrices de `DBPROP` estructuras. Cada `DBPROP` estructura representa una propiedad única que se puede establecer.

## <a name="addproperty"></a> CDBPropSet:: AddProperty

Agrega una propiedad para el conjunto de propiedades.

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
[in] El identificador de la propiedad que se va a agregar. Utilizado para inicializar el `dwPropertyID` de la `DBPROP` estructura agregado al conjunto de propiedades.

*var*<br/>
[in] Una variante que se usa para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.

*szValue*<br/>
[in] Una cadena utilizada para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.

*bValue*<br/>
[in] Un `BYTE` o valor booleano utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.

*nvalor*<br/>
[in] Un valor entero utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.

*fltValue*<br/>
[in] Un valor de punto flotante que se usa para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.

*dblValue*<br/>
[in] Un valor de punto flotante de precisión doble utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.

*cyValue*<br/>
[in] Un valor de divisa CY utilizado para inicializar el valor de propiedad para el `DBPROP` estructura agregado al conjunto de propiedades.

### <a name="return-value"></a>Valor devuelto

**True** si la propiedad se agregó correctamente. En caso contrario, **false**.

## <a name="cdbpropset"></a> CDBPropSet:: CDBPropSet

El constructor. Inicializa el `rgProperties`, `cProperties`, y `guidPropertySet` campos de la [DBPROPSET](/previous-versions/windows/desktop/ms714367) estructura.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Parámetros

*GUID*<br/>
[in] Un GUID que se usa para inicializar el `guidPropertySet` campo.

*conjunto de propiedades*<br/>
[in] Otro `CDBPropSet` objeto para la construcción de copia.

## <a name="setguid"></a> CDBPropSet:: SetGuid

Establece el `guidPropertySet` campo el `DBPROPSET` estructura.

### <a name="syntax"></a>Sintaxis

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parámetros

*GUID*<br/>
[in] Un GUID que se usa para establecer el `guidPropertySet` campo de la [DBPROPSET](/previous-versions/windows/desktop/ms714367) estructura.

### <a name="remarks"></a>Comentarios

Este campo se puede establecer el [constructor](../../data/oledb/cdbpropset-cdbpropset.md) también.

## <a name="op_equal"></a> CDBPropSet:: operator =

Asigna el contenido de una propiedad establecida en otro conjunto de propiedades.

### <a name="syntax"></a>Sintaxis

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet (Clase)](../../data/oledb/cdbpropidset-class.md)<br/>
[Estructura DBPROPSET](/previous-versions/windows/desktop/ms714367)
[estructura DBPROP](/previous-versions/windows/desktop/ms717970)