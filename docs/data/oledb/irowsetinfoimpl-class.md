---
title: IRowsetInfoImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- GetProperties
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
dev_langs:
- C++
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 542c97c1e13d5979290772668b6dccebe1ece9f9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113167"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl (Clase)

Proporciona una implementación para el [IRowsetInfo](/previous-versions/windows/desktop/ms724541\(v=vs.85\)) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class PropClass = T>  
class ATL_NO_VTABLE IRowsetInfoImpl :   
   public IRowsetInfo,    
   public CUtlProps<PropClass>  
```  
  
### <a name="parameters"></a>Parámetros  

*T*<br/>
La clase derivada de `IRowsetInfoImpl`.  
  
*PropClass*<br/>
Una clase de propiedad definidos por el usuario que el valor predeterminado es *T*. 

## <a name="requirements"></a>Requisitos  

**Encabezado:** altdb.h   
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetProperties](#getproperties)|Devuelve la configuración actual de todas las propiedades admitidas por el conjunto de filas.|  
|[GetReferencedRowset](#getreferencedrowset)|Devuelve un puntero de interfaz al conjunto de filas al que se aplica un marcador.|  
|[GetSpecification](#getspecification)|Devuelve un puntero de interfaz en el objeto (comando o sesión) que creó este conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  

Una interfaz obligatoria en conjuntos de filas. Esta clase implementa las propiedades del conjunto de filas utilizando el [mapa del conjunto de propiedades](../../data/oledb/begin-propset-map.md) definido en la clase de comando. Aunque la clase de conjunto de filas aparece usarán la propiedad de la clase de comando establece, el conjunto de filas se suministra con su propia copia de las propiedades de tiempo de ejecución, cuando se crea un objeto de comando o sesión.  
  
## <a name="getproperties"></a> Irowsetinfoimpl:: GetProperties

Devuelve la configuración actual de propiedades en el `DBPROPSET_ROWSET` grupo.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,  
   const DBPROPIDSET rgPropertyIDSets[],  
   ULONG* pcPropertySets,  
   DBPROPSET** prgPropertySets);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IRowsetInfo:: GetProperties](/previous-versions/windows/desktop/ms719611\(v=vs.85\)) en el *referencia del programador OLE DB*. 

## <a name="getreferencedrowset"></a> Irowsetinfoimpl:: Getreferencedrowset

Devuelve un puntero de interfaz al conjunto de filas al que se aplica un marcador.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,  
   REFIID riid,  
   IUnknown** ppReferencedRowset);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IRowsetInfo::GetReferencedRowset](/previous-versions/windows/desktop/ms721145\(v=vs.85\)) en el *referencia del programador OLE DB*. El *iOrdinal* parámetro debe ser una columna de marcador. 

## <a name="getspecification"></a> Irowsetinfoimpl:: Getspecification

Devuelve un puntero de interfaz en el objeto (comando o sesión) que creó este conjunto de filas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (GetSpecification )(REFIID riid,  
   IUnknown** ppSpecification);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IRowsetInfo::GetSpecification](/previous-versions/windows/desktop/ms716746\(v=vs.85\)) en el *referencia del programador OLE DB*.  
  
### <a name="remarks"></a>Comentarios  

Utilice este método con [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md) para recuperar las propiedades del objeto de origen de datos.  
  
## <a name="see-also"></a>Vea también  

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)