---
title: IConvertTypeImpl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IConvertTypeImpl<T>
- IConvertTypeImpl
- ATL.IConvertTypeImpl
- ATL::IConvertTypeImpl
- ATL::IConvertTypeImpl<T>
dev_langs:
- C++
helpviewer_keywords:
- IConvertTypeImpl class
ms.assetid: 7f81e79e-7d3f-4cbe-b93c-d632a94b15f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e19d10b061cd5126f46f2f54a4489caf6d26d40b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="iconverttypeimpl-class"></a>IConvertTypeImpl (Clase)
Proporciona una implementación de la [IConvertType](https://msdn.microsoft.com/en-us/library/ms715926.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T>  
class ATL_NO_VTABLE IConvertTypeImpl   
   : public IConvertType, public CConvertHelper  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `IConvertTypeImpl`.  
  
## <a name="members"></a>Miembros  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[CanConvert](../../data/oledb/iconverttypeimpl-canconvert.md)|Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz es obligatoria en conjuntos de filas de índice, comandos y conjuntos de filas. **IConvertTypeImpl** implementa la interfaz mediante la delegación para el objeto de conversión proporcionado por OLE DB.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)