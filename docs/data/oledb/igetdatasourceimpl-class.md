---
title: IGetDataSourceImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IGetDataSourceImpl
- ATL.IGetDataSourceImpl<T>
- ATL.IGetDataSourceImpl
- ATL::IGetDataSourceImpl
- ATL::IGetDataSourceImpl<T>
- GetDataSource
- IGetDataSourceImpl.GetDataSource
- IGetDataSourceImpl::GetDataSource
dev_langs:
- C++
helpviewer_keywords:
- IGetDataSourceImpl class
- GetDataSource method
ms.assetid: d63f3178-d663-4f01-8c09-8aab2dd6805a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0c6e304547af06d5de6d81bae2ceace119e4681d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339801"
---
# <a name="igetdatasourceimpl-class"></a>IGetDataSourceImpl (Clase)
Proporciona una implementación de la [IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx) objeto.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T>  
class ATL_NO_VTABLE IGetDataSourceImpl : public IGetDataSource  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IGetDataSourceImpl`.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[GetDataSource](#getdatasource)|Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.|  
  
## <a name="remarks"></a>Comentarios  
 Esto es una interfaz obligatoria en la sesión para obtener un puntero de interfaz al objeto de origen de datos.  

## <a name="getdatasource"></a> Igetdatasourceimpl:: GetDatasource
Devuelve un puntero de interfaz en el objeto de origen de datos que creó la sesión.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD(GetDataSource)(REFIID riid,   
   IUnknown ** ppDataSource);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IGetDataSource::GetDataSource](https://msdn.microsoft.com/library/ms725443.aspx) en el *referencia del programador OLE DB*.  
  
### <a name="remarks"></a>Comentarios  
 Resulta útil si necesita tener acceso a propiedades en el objeto de origen de datos.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)