---
title: IAccessorImpl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IAccessorImpl
dev_langs:
- C++
helpviewer_keywords:
- IAccessorImpl class
ms.assetid: 768606da-8b71-417c-a62c-88069ce7730d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d62deeb487fded5895bbd47332a0f8a6ad7bbce6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33102529"
---
# <a name="iaccessorimpl-class"></a>IAccessorImpl (Clase)
Proporciona una implementación de la [IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, 
          class BindType = ATLBINDINGS,
          class BindingVector = CAtlMap <HACCESSOR hAccessor, BindType* pBindingsStructure>>  
class ATL_NO_VTABLE IAccessorImpl : public IAccessorImplBase<BindType>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase de objeto de conjunto de filas o un comando.  
  
 `BindType`  
 Unidad de almacenamiento de información de enlace. El valor predeterminado es el **ATLBINDINGS** estructura (vea atldb.h).  
  
 `BindingVector`  
 Unidad de almacenamiento para obtener información de columna. El valor predeterminado es [CAtlMap](../../atl/reference/catlmap-class.md) donde el elemento clave es un **HACCESSOR** valor y el elemento de valor es un puntero a un `BindType` estructura.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)|El constructor.|  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[AddRefAccessor](../../data/oledb/iaccessorimpl-addrefaccessor.md)|Agrega un recuento de referencias a un descriptor de acceso existente.|  
|[CreateAccessor](../../data/oledb/iaccessorimpl-createaccessor.md)|Crea un descriptor de acceso de un conjunto de enlaces.|  
|[GetBindings](../../data/oledb/iaccessorimpl-getbindings.md)|Devuelve los enlaces de un descriptor de acceso.|  
|[ReleaseAccessor](../../data/oledb/iaccessorimpl-releaseaccessor.md)|Libera un descriptor de acceso.|  
  
## <a name="remarks"></a>Comentarios  
 Esto es obligatorio en conjuntos de filas y comandos. OLE DB requiere que los proveedores implementar un **HACCESSOR**, que es una etiqueta a una matriz de [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) estructuras. **HACCESSOR**s proporcionado por `IAccessorImpl` son direcciones de la `BindType` estructuras. De forma predeterminada, `BindType` se define como un **ATLBINDINGS** en `IAccessorImpl`de definición de plantilla. `BindType` Proporciona un mecanismo que utiliza `IAccessorImpl` para realizar un seguimiento del número de elementos de su **DBBINDING** de matriz, así como una marcas de recuento y el descriptor de acceso de referencia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)