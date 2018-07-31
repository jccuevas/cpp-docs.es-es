---
title: IRowsetChangeImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::IRowsetChangeImpl
- IRowsetChangeImpl
- ATL.IRowsetChangeImpl
- ATL.IRowsetChangeImpl.DeleteRows
- ATL::IRowsetChangeImpl::DeleteRows
- IRowsetChangeImpl.DeleteRows
- DeleteRows
- IRowsetChangeImpl::DeleteRows
- ATL.IRowsetChangeImpl.InsertRow
- InsertRow
- IRowsetChangeImpl.InsertRow
- ATL::IRowsetChangeImpl::InsertRow
- IRowsetChangeImpl::InsertRow
- SetData
- IRowsetChangeImpl::SetData
- ATL.IRowsetChangeImpl.SetData
- IRowsetChangeImpl.SetData
- ATL::IRowsetChangeImpl::SetData
- IRowsetChangeImpl::FlushData
- IRowsetChangeImpl.FlushData
- FlushData
dev_langs:
- C++
helpviewer_keywords:
- providers, updatable
- updatable providers, immediate update
- IRowsetChangeImpl class
- DeleteRows method
- InsertRow method
- SetData method
- FlushData method
ms.assetid: 1e9fee15-ed9e-4387-af8f-215569beca6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0f77f9a33b0cf51ea54d16f89e86ea914640f627
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39339603"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl (Clase)
La implementación de plantillas OLE DB de la [IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx) interfaz en la especificación de OLE DB.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <  
   class T,   
   class Storage,   
   class BaseInterface = IRowsetChange,   
   class RowClass = CSimpleRow,   
   class MapClass = CAtlMap <RowClass::KeyType, RowClass*>>  
class ATL_NO_VTABLE IRowsetChangeImpl : public BaseInterface  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 Una clase derivada de `IRowsetChangeImpl`.  
  
 *Almacenamiento de información*  
 El registro de usuario.  
  
 *BaseInterface*  
 La clase base para la interfaz, como `IRowsetChange`.  
  
 *RowClass*  
 La unidad de almacenamiento para el identificador de fila.  
  
 *MapClass*  
 La unidad de almacenamiento para todos los identificadores de fila mantenidos por el proveedor.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods-used-with-irowsetchange"></a>Métodos de interfaz (usados con IRowsetChange)  
  
|||  
|-|-|  
|[DeleteRows](#deleterows)|Elimina las filas del conjunto de filas.|  
|[InsertRow](#insertrow)|Inserta una fila en el conjunto de filas.|  
|[SetData](#setdata)|Establece los valores de datos en una o varias columnas.|  
  
### <a name="implementation-method-callback"></a>Método de implementación (devolución de llamada)  
  
|||  
|-|-|  
|[FlushData](#flushdata)|Omitido por el proveedor para confirmar los datos en su almacén.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es responsable de operaciones de escritura inmediato en un almacén de datos. Almacena "Inmediato" significa que, cuando el usuario final (es decir, la persona con el consumidor) realiza los cambios, esos cambios se transfieren inmediatamente a los datos (y no se puede deshacer).  
  
 `IRowsetChangeImpl` implementa OLE DB `IRowsetChange` interfaz, lo que permite la actualización de valores de columnas en las filas existentes, eliminar filas y la inserción de nuevas filas.  
  
 La implementación de plantillas OLE DB es compatible con todos los métodos bases (`SetData`, `InsertRow`, y `DeleteRows`).  
  
> [!IMPORTANT]
>  Se recomienda encarecidamente que lea la documentación siguiente antes de intentar implementar el proveedor:  
  
-   [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)  
  
-   Capítulo 6 de la *referencia del programador OLE DB*  
  
-   Consulte también cómo el `RUpdateRowset` clase se utiliza en el ejemplo UpdatePV  
  
## <a name="deleterows"></a> IRowsetChangeImpl:: DeleteRows
Elimina las filas del conjunto de filas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (DeleteRows )(HCHAPTER /* hReserved */,  
   DBCOUNTITEM cRows,  
   const HROW rghRows[],  
   DBROWSTATUS rgRowStatus[]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IRowsetChange:: DeleteRows](https://msdn.microsoft.com/library/ms724362.aspx) en el *referencia del programador OLE DB*. 

## <a name="insertrow"></a> IRowsetChangeImpl:: insertRow
Crea e inicializa una nueva fila del conjunto de filas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (InsertRow )(HCHAPTER /* hReserved */,  
   HACCESSOR hAccessor,  
   void* pData,  
   HROW* phRow);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IRowsetChange:: insertRow](https://msdn.microsoft.com/library/ms716921.aspx) en el *referencia del programador OLE DB*. 

## <a name="setdata"></a> IRowsetChangeImpl:: SetData
Establece los valores de datos en una o varias columnas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IRowsetChange:: SetData](https://msdn.microsoft.com/library/ms721232.aspx) en el *referencia del programador OLE DB*. 

## <a name="flushdata"></a> IRowsetChangeImpl:: FlushData
Omitido por el proveedor para confirmar los datos en su almacén.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT FlushData(HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hRowToFlush*  
 [in] Identificador de las filas de los datos. El tipo de esta fila se determina a partir del *RowClass* argumento de plantilla de la `IRowsetImpl` clase (`CSimpleRow` de forma predeterminada).  
  
 *hAccessorToFlush*  
 [in] Identificador de descriptor de acceso, que contiene información de enlace e información de tipo en su `PROVIDER_MAP` (consulte [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)