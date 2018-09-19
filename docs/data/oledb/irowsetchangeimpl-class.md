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
ms.openlocfilehash: 3cac23621959fb71247b649171309ec9d12cf35b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038755"
---
# <a name="irowsetchangeimpl-class"></a>IRowsetChangeImpl (Clase)

La implementación de plantillas OLE DB de la [IRowsetChange](/previous-versions/windows/desktop/ms715790\(v=vs.85\)) interfaz en la especificación de OLE DB.  
  
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

*T*<br/>
Una clase derivada de `IRowsetChangeImpl`.  
  
*Almacenamiento de información*<br/>
El registro de usuario.  
  
*BaseInterface*<br/>
La clase base para la interfaz, como `IRowsetChange`.  
  
*RowClass*<br/>
La unidad de almacenamiento para el identificador de fila.  
  
*MapClass*<br/>
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
  
- [Crear un proveedor actualizable](../../data/oledb/creating-an-updatable-provider.md)  
  
- Capítulo 6 de la *referencia del programador OLE DB*  
  
- Consulte también cómo el `RUpdateRowset` clase se utiliza en el [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) ejemplo.  
  
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

Consulte [IRowsetChange:: DeleteRows](/previous-versions/windows/desktop/ms724362(v%3dvs.85)) en el *referencia del programador OLE DB*. 

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

Consulte [IRowsetChange:: insertRow](/previous-versions/windows/desktop/ms716921\(v=vs.85\)) en el *referencia del programador OLE DB*. 

## <a name="setdata"></a> IRowsetChangeImpl:: SetData

Establece los valores de datos en una o varias columnas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
STDMETHOD (SetData )(HROW hRow,  
   HACCESSOR hAccessor,  
   void* pSrcData);  
```  
  
#### <a name="parameters"></a>Parámetros  

Consulte [IRowsetChange:: SetData](/previous-versions/windows/desktop/ms721232\(v=vs.85\)) en el *referencia del programador OLE DB*. 

## <a name="flushdata"></a> IRowsetChangeImpl:: FlushData

Omitido por el proveedor para confirmar los datos en su almacén.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT FlushData(HROW hRowToFlush,  
   HACCESSOR hAccessorToFlush);  
```  
  
#### <a name="parameters"></a>Parámetros  

*hRowToFlush*<br/>
[in] Identificador de las filas de los datos. El tipo de esta fila se determina a partir del *RowClass* argumento de plantilla de la `IRowsetImpl` clase (`CSimpleRow` de forma predeterminada).  
  
*hAccessorToFlush*<br/>
[in] Identificador de descriptor de acceso, que contiene información de enlace e información de tipo en su `PROVIDER_MAP` (consulte [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)).  
  
### <a name="return-value"></a>Valor devuelto  

Un HRESULT estándar.  
  
## <a name="see-also"></a>Vea también  

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)