---
title: IRowsetUpdateImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IRowsetUpdateImpl
- ATL.IRowsetUpdateImpl
- ATL::IRowsetUpdateImpl
- SetData
- IRowsetUpdateImpl::SetData
- IRowsetUpdateImpl.SetData
- ATL::IRowsetUpdateImpl::SetData
- ATL.IRowsetUpdateImpl.SetData
- ATL.IRowsetUpdateImpl.GetOriginalData
- IRowsetUpdateImpl.GetOriginalData
- GetOriginalData
- ATL::IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetOriginalData
- IRowsetUpdateImpl::GetPendingRows
- GetPendingRows
- IRowsetUpdateImpl.GetPendingRows
- ATL::IRowsetUpdateImpl::GetPendingRows
- ATL.IRowsetUpdateImpl.GetPendingRows
- ATL.IRowsetUpdateImpl.GetRowStatus
- IRowsetUpdateImpl::GetRowStatus
- IRowsetUpdateImpl.GetRowStatus
- ATL::IRowsetUpdateImpl::GetRowStatus
- GetRowStatus
- ATL.IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl::Undo
- IRowsetUpdateImpl.Undo
- ATL::IRowsetUpdateImpl::Update
- IRowsetUpdateImpl::Update
- IRowsetUpdateImpl.Update
- ATL.IRowsetUpdateImpl.Update
- IRowsetUpdateImpl::IsUpdateAllowed
- IRowsetUpdateImpl.IsUpdateAllowed
- IsUpdateAllowed
- IRowsetUpdateImpl.m_mapCachedData
- IRowsetUpdateImpl::m_mapCachedData
- m_mapCachedData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- IRowsetUpdateImpl class
- updatable providers, deferred update
- SetData method
- GetOriginalData method
- GetPendingRows method
- GetRowStatus method
- Undo method
- Update method
- IsUpdateAllowed method
- m_mapCachedData
ms.assetid: f85af76b-ab6f-4f8b-8f4a-337c9679d68f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5dcaa42242410c2823388c7004a0c0a7d1991f59
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573176"
---
# <a name="irowsetupdateimpl-class"></a>IRowsetUpdateImpl (Clase)
La implementación de plantillas OLE DB de la [IRowsetUpdate](/previous-versions/windows/desktop/ms714401\(v=vs.85\)) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <  
   class T,   
   class Storage,   
   class UpdateArray = CAtlArray<Storage>,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>   
>  

class IRowsetUpdateImpl : public IRowsetChangeImpl<  
   T,   
   Storage,   
   IRowsetUpdate,   
   RowClass,   
   MapClass>  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Una clase derivada de `IRowsetUpdateImpl`.  
  
 *Almacenamiento de información*  
 El registro de usuario.  
  
 *UpdateArray*  
 Una matriz que contiene los datos almacenados en caché para actualizar el conjunto de filas.  
  
 *RowClass*  
 La unidad de almacenamiento para el `HROW`.  
  
 *MapClass*  
 La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (usados con IRowsetChange)  
  
|||  
|-|-|  
|[SetData](#setdata)|Establece los valores de datos en una o varias columnas.|  
  
### <a name="interface-methods-used-with-irowsetupdate"></a>Métodos de interfaz (usados con IRowsetUpdate)  
  
|||  
|-|-|  
|[GetOriginalData](#getoriginaldata)|Obtiene los datos transmitidos a más recientemente u obtenido del origen de datos, pasando por alto los cambios pendientes.|  
|[GetPendingRows](#getpendingrows)|Devuelve una lista de filas con cambios pendientes.|  
|[GetRowStatus](#getrowstatus)|Devuelve el estado de las filas especificadas.|  
|[Fase de reversión](#undo)|Deshace los cambios en la fila desde la última captura o actualización.|  
|[Actualizar](#update)|Transmite los cambios realizados en la fila desde la última captura o actualización.|  
  
### <a name="implementation-methods-callback"></a>Métodos de implementación (devolución de llamada)  
  
|||  
|-|-|  
|[IsUpdateAllowed](#isupdateallowed)|Se usa para comprobar la integridad, la seguridad, y así sucesivamente antes de permitir las actualizaciones.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_mapCachedData](#mapcacheddata)|Contiene los datos originales para la operación aplazada.|  
  
## <a name="remarks"></a>Comentarios  
 En primer lugar debe leer y entender la documentación de [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)), ya que todos los elementos descritos en él también se aplica aquí. También debe leer el capítulo 6 de la *referencia del programador de OLE DB* sobre la configuración de datos.  
  
 `IRowsetUpdateImpl` implementa OLE DB `IRowsetUpdate` interfaz, que permite a los consumidores retrasar la transmisión de los cambios realizados con `IRowsetChange` al origen de datos y deshacer los cambios antes de la transmisión.  
  
> [!IMPORTANT]
>  Se recomienda encarecidamente que lea la documentación siguiente antes de intentar implementar el proveedor:  
  
-   [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Capítulo 6 de la *referencia del programador OLE DB*  
  
-   Consulte también cómo el `RUpdateRowset` clase se utiliza en el [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ejemplo  

## <a name="setdata"></a> IRowsetUpdateImpl:: SetData
Establece los valores de datos en una o varias columnas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232\(v=vs.85\)) en el *referencia del programador OLE DB*.  
  
### <a name="remarks"></a>Comentarios  
 Este método invalida el [IRowsetChangeImpl:: SetData](../../data/oledb/irowsetchangeimpl-setdata.md) , pero el método incluye almacenamiento en caché de datos originales para permitir el procesamiento de la operación inmediato o aplazado.

## <a name="getoriginaldata"></a> IRowsetUpdateImpl:: GetOriginalData
Obtiene los datos transmitidos a más recientemente u obtenido del origen de datos, pasando por alto los cambios pendientes.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (GetOriginalData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pData);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IRowsetUpdate::GetOriginalData](/previous-versions/windows/desktop/ms709947\(v=vs.85\)) en el *referencia del programador OLE DB*.   

## <a name="getpendingrows"></a> IRowsetUpdateImpl:: Getpendingrows
Devuelve una lista de filas con cambios pendientes.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (GetPendingRows )(HCHAPTER /* hReserved */,  
   DBPENDINGSTATUS dwRowStatus,  
   DBCOUNTITEM* pcPendingRows,  
   HROW** prgPendingRows,  
   DBPENDINGSTATUS** prgPendingStatus);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hReserved*  
 [in] Corresponde a la *hChapter* parámetro [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626\(v=vs.85\)).  
  
 Para otros parámetros, vea [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626\(v=vs.85\)) en el *referencia del programador de OLE DB*.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [IRowsetUpdate::GetPendingRows](/previous-versions/windows/desktop/ms719626\(v=vs.85\)) en el *referencia del programador de OLE DB*.  

## <a name="getrowstatus"></a> IRowsetUpdateImpl:: GetRowStatus
Devuelve el estado de las filas especificadas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (GetRowStatus )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBPENDINGSTATUS rgPendingStatus[]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hReserved*  
 [in] Corresponde a la *hChapter* parámetro [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377\(v=vs.85\)).  
  
 Para otros parámetros, vea [IRowsetUpdate::GetRowStatus](/previous-versions/windows/desktop/ms724377\(v=vs.85\)) en el *referencia del programador de OLE DB*.  

## <a name="undo"></a> IRowsetUpdateImpl:: Undo
Deshace los cambios en la fila desde la última captura o actualización.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (Undo )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[ ],  
   DBCOUNTITEM* pcRowsUndone,  
   HROW** prgRowsUndone,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hReserved*  
 [in] Corresponde a la *hChapter* parámetro [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)).  
  
 *pcRowsUndone*  
 [out] Corresponde a la *pcRows* parámetro [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)).  
  
 *prgRowsUndone*  
 [in] Corresponde a la *prgRows* parámetro [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)).  
  
 Para otros parámetros, vea [IRowsetUpdate::Undo](/previous-versions/windows/desktop/ms719655\(v=vs.85\)) en el *referencia del programador de OLE DB*. 

## <a name="update"></a> IRowsetUpdateImpl:: Update
Transmite los cambios realizados en la fila desde la última captura o actualización.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (Update )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBCOUNTITEM* pcRows,  
   HROW** prgRows,  
   DBROWSTATUS** prgRowStatus);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hReserved*  
 [in] Corresponde a la *hChapter* parámetro [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709\(v=vs.85\)).  
  
 Para otros parámetros, vea [IRowsetUpdate:: Update](/previous-versions/windows/desktop/ms719709\(v=vs.85\)) en el *referencia del programador de OLE DB*.  
  
### <a name="remarks"></a>Comentarios  
 Los cambios se transmiten mediante una llamada a [IRowsetChangeImpl:: FlushData](../../data/oledb/irowsetchangeimpl-flushdata.md). El consumidor debe llamar a [CRowset:: Update](../../data/oledb/crowset-update.md) para que los cambios surtan efecto. Establecer *prgRowstatus* en un valor adecuado, como se describe en [Estados de fila](/previous-versions/windows/desktop/ms722752\(v=vs.85\)) en el *referencia del programador de OLE DB*. 
  
## <a name="isupdateallowed"></a> IRowsetUpdateImpl:: IsUpdateAllowed
Invalide este método para comprobar la seguridad, integridad, y así sucesivamente antes de las actualizaciones.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT IsUpdateAllowed(DBPENDINGSTATUS /* [in] */ /* status */,  
   HROW /* [in] */ /* hRowUpdate */,  
   DBROWSTATUS* /* [out] */ /* pRowStatus */);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *status*  
 [in] El estado de las operaciones en las filas pendientes.  
  
 *hRowUpdate*  
 [in] Identificador para las filas que el usuario desea actualizar.  
  
 *pRowStatus*  
 [out] Devuelve el estado al usuario.  
  
### <a name="remarks"></a>Comentarios  
 Si determina que se debe permitir una actualización, devuelve S_OK; en caso contrario, devuelve E_FAIL. Si permite que una actualización, también deberá establecer el `DBROWSTATUS` en [IRowsetUpdateImpl:: Update](../../data/oledb/irowsetupdateimpl-update.md) un adecuado [estado de la fila](/previous-versions/windows/desktop/ms722752\(v=vs.85\)).  

## <a name="mapcacheddata"></a> IRowsetUpdateImpl:: M_mapcacheddata
Un mapa que contiene los datos originales para la operación aplazada.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
CAtlMap<   
   HROW hRow,    
   Storage* pData   
>   
m_mapCachedData;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hRow*  
 Identificador de las filas de los datos.  
  
 *pData*  
 Un puntero a los datos en la memoria caché. Los datos están de tipo *almacenamiento* (la clase de registro de usuario). Consulte la *almacenamiento* argumento de plantilla en [IRowsetUpdateImpl (clase)](../../data/oledb/irowsetupdateimpl-class.md).  

## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)