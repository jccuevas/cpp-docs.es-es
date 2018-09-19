---
title: IColumnsInfoImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IColumnsInfoImpl<T>
- ATL::IColumnsInfoImpl
- IColumnsInfoImpl
- ATL.IColumnsInfoImpl
- ATL::IColumnsInfoImpl<T>
- GetColumnInfo
- ATL::IColumnsInfoImpl::GetColumnInfo
- ATL.IColumnsInfoImpl.GetColumnInfo
- ATL::IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl::GetColumnInfo
- IColumnsInfoImpl<T>::GetColumnInfo
- IColumnsInfoImpl.GetColumnInfo
- IColumnsInfoImpl<T>::MapColumnIDs
- MapColumnIDs
- ATL::IColumnsInfoImpl::MapColumnIDs
- IColumnsInfoImpl.MapColumnIDs
- ATL::IColumnsInfoImpl<T>::MapColumnIDs
- IColumnsInfoImpl::MapColumnIDs
- ATL.IColumnsInfoImpl<T>.MapColumnIDs
- ATL.IColumnsInfoImpl.MapColumnIDs
dev_langs:
- C++
helpviewer_keywords:
- IColumnsInfoImpl class
- GetColumnInfo method
- MapColumnIDs method
ms.assetid: ba74c1c5-2eda-4452-8b57-84919fa0d066
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bde6a3947d7afa836d93387e80c9b7885b1bc15c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099413"
---
# <a name="icolumnsinfoimpl-class"></a>IColumnsInfoImpl (Clase)

Proporciona una implementación de la [IColumnsInfo](/previous-versions/windows/desktop/ms724541\(v=vs.85\)) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T>  
class ATL_NO_VTABLE IColumnsInfoImpl :   
   public IColumnsInfo,    
   public CDBIDOps  
```  
  
### <a name="parameters"></a>Parámetros  

*T*<br/>
La clase derivada de `IColumnsInfoImpl`.  

## <a name="requirements"></a>Requisitos  

**Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetColumnInfo](#getcolumninfo)|Devuelve los metadatos de columna necesarios para la mayoría de los consumidores.|  
|[MapColumnIDs](#mapcolumnids)|Devuelve una matriz de ordinales de las columnas en un conjunto de filas que se identifican mediante los identificadores de columna especificado.|  
  
## <a name="remarks"></a>Comentarios  

Una interfaz obligatoria en los conjuntos de filas y los comandos. Para modificar el comportamiento de su proveedor `IColumnsInfo` implementación, deberá modificar la asignación de columna del proveedor.  

## <a name="getcolumninfo"></a> Icolumnsinfoimpl:: GetColumnInfo

Devuelve los metadatos de columna necesarios para la mayoría de los consumidores.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (GetColumnInfo)(DBORDINAL* pcColumns,  
   DBCOLUMNINFO** prgInfo,  
   OLECHAR** ppStringsBuffer);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IColumnsInfo:: GetColumnInfo](/previous-versions/windows/desktop/ms722704\(v=vs.85\)) en el *referencia del programador OLE DB*.  

## <a name="mapcolumnids"></a> Icolumnsinfoimpl:: Mapcolumnids

Devuelve una matriz de ordinales de las columnas en un conjunto de filas que se identifican mediante los identificadores de columna especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (MapColumnIDs)(DBORDINAL cColumnIDs,  
   const DBID rgColumnIDs[],  
   DBORDINAL rgColumns[]);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IColumnsInfo::MapColumnIDs](/previous-versions/windows/desktop/ms714200\(v=vs.85\)) en el *referencia del programador OLE DB*.  
  
## <a name="see-also"></a>Vea también  

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)