---
title: CStreamRowset (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
dev_langs:
- C++
helpviewer_keywords:
- CStreamRowset class
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e499d732beb2d73dbb6ec0bbe0b360eeb394b9d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cstreamrowset-class"></a>CStreamRowset (Clase)
Usar en un `CCommand` o `CTable` declaración.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CAccessorBase>  
class CStreamRowset  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CStreamRowset](../../data/oledb/cstreamrowset-cstreamrowset.md)|Constructor. Crea e inicializa la `CStreamRowset` objeto.|  
|[Cerrar](../../data/oledb/cstreamrowset-close.md)|Las versiones del [ISequentialStream](https://msdn.microsoft.com/en-us/library/ms718035.aspx) puntero de interfaz en la clase.|  
  
## <a name="remarks"></a>Comentarios  
 Use `CStreamRowset` en su `CCommand` o `CTable` declaración, por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]  
  
 o  
  
 [!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]  
  
 `ICommand::Execute` Devuelve un `ISequentialStream` puntero, que se almacena en `m_spStream`. A continuación, utilice la **lectura** método para recuperar los datos (cadena Unicode) en formato XML. Por ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]  
  
 SQL Server 2000 lleva a cabo la aplicación de formato XML y devuelve todas las columnas y todas las filas del conjunto de filas como una sola cadena XML.  
  
> [!NOTE]
>  Esta característica solo funciona con SQL Server 2000.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)