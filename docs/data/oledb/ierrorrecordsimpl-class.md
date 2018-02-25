---
title: IErrorRecordsImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IErrorRecordsImpl
- ATL.IErrorRecordsImpl
- IErrorRecordsImpl
dev_langs:
- C++
helpviewer_keywords:
- IErrorRecordsImpl class
ms.assetid: dea8e938-c5d8-45ab-86de-eb8fbf534ffb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f3d466cbf761342706774a9b5a52c5b4e69a7328
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ierrorrecordsimpl-class"></a>IErrorRecordsImpl (Clase)
Implementa OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) interfaz, agregar registros a y recuperar los registros de un miembro de datos ([m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)) de tipo **CAtlArray <** `RecordClass`**>**.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, class RecordClass = ATLERRORINFO>  
class IErrorRecordsImpl : public IErrorRecords  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada de `IErrorRecordsImpl`.  
  
 `RecordClass`  
 Una clase que representa un objeto de error de OLE DB.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetErrorDescriptionString](../../data/oledb/ierrorrecordsimpl-geterrordescriptionstring.md)|Obtiene la cadena de descripción del error de un registro de error.|  
|[GetErrorGUID](../../data/oledb/ierrorrecordsimpl-geterrorguid.md)|Obtiene el GUID de error de un registro de error.|  
|[GetErrorHelpContext](../../data/oledb/ierrorrecordsimpl-geterrorhelpcontext.md)|Obtiene el identificador de contexto de Ayuda de un registro de error.|  
|[GetErrorHelpFile](../../data/oledb/ierrorrecordsimpl-geterrorhelpfile.md)|Obtiene la ruta de acceso completa del archivo de Ayuda de un registro de error.|  
|[GetErrorSource](../../data/oledb/ierrorrecordsimpl-geterrorsource.md)|Obtiene el código de origen del error de un registro de error.|  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[AddErrorRecord](../../data/oledb/ierrorrecordsimpl-adderrorrecord.md)|Agrega un registro para el objeto de error de OLE DB.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Devuelve información básica sobre el error, como el código de retorno y el número de error específico del proveedor.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Devuelve un puntero a una interfaz en un objeto de error personalizado.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Devuelve un [IErrorInfo](https://msdn.microsoft.com/en-us/library/ms718112.aspx) puntero de interfaz en el registro especificado.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Devuelve los parámetros de error.|  
|[GetRecordCount](../../mfc/reference/cdaorecordset-class.md#getrecordcount)|Devuelve el número de registros en el objeto de registro de OLE DB.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_rgErrors](../../data/oledb/ierrorrecordsimpl-m-rgerrors.md)|Una matriz de registros de error.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)