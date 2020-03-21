---
title: IRowsetInfoImpl (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: 691871bfc4a9e63167611a3228807fb12e32d1cb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077868"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl (Clase)

Proporciona una implementación para la interfaz [IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) .

## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de `IRowsetInfoImpl`.

*PropClass*<br/>
Una clase de propiedad definible por el usuario que tiene como valor predeterminado *T*.

## <a name="requirements"></a>Requisitos

**Encabezado:** altdb. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Métodos de interfaz

|||
|-|-|
|[GetProperties](#getproperties)|Devuelve los valores actuales de todas las propiedades que el conjunto de filas admite.|
|[GetReferencedRowset](#getreferencedrowset)|Devuelve un puntero de interfaz al conjunto de filas al que se aplica un marcador.|
|[GetSpecification](#getspecification)|Devuelve un puntero de interfaz en el objeto (comando o sesión) que creó este conjunto de filas.|

## <a name="remarks"></a>Observaciones

Una interfaz obligatoria en conjuntos de filas. Esta clase implementa las propiedades del conjunto de filas utilizando la [asignación de conjuntos de propiedades](../../data/oledb/begin-propset-map.md) definida en la clase Command. Aunque la clase de conjunto de filas parece estar usando los conjuntos de propiedades de la clase de comando, el conjunto de filas se suministra con su propia copia de las propiedades en tiempo de ejecución, cuando se crea mediante un objeto de comando o de sesión.

## <a name="irowsetinfoimplgetproperties"></a><a name="getproperties"></a>Irowsetinfoimpl (:: GetProperties

Devuelve la configuración actual de las propiedades del grupo de `DBPROPSET_ROWSET`.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetInfo:: GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) en la *Referencia del programador de OLE DB*.

## <a name="irowsetinfoimplgetreferencedrowset"></a><a name="getreferencedrowset"></a>Irowsetinfoimpl (:: GetReferencedRowset

Devuelve un puntero de interfaz al conjunto de filas al que se aplica un marcador.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetInfo:: GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) en la *Referencia del programador de OLE DB*. El parámetro *iOrdinal* debe ser una columna de marcador.

## <a name="irowsetinfoimplgetspecification"></a><a name="getspecification"></a>Irowsetinfoimpl (:: GetSpecification

Devuelve un puntero de interfaz en el objeto (comando o sesión) que creó este conjunto de filas.

### <a name="syntax"></a>Sintaxis

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Parámetros

Vea [IRowsetInfo:: GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="remarks"></a>Observaciones

Use este método con [igetdatasourceimpl (](../../data/oledb/igetdatasourceimpl-class.md) para recuperar las propiedades del objeto de origen de datos.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)