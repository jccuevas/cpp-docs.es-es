---
title: CDBPropIDSet (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 32048b9f8e6ab528a3a31ed475cfb2725c20918e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet (Clase)
Hereda de la **DBPROPIDSET** estructurar y agrega un constructor que inicializa los campos clave, así como la [AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md) acceder a método.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CDBPropIDSet : public tagDBPROPIDSET  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddPropertyID](../../data/oledb/cdbpropidset-addpropertyid.md)|Agrega una propiedad para el conjunto de Id. de propiedad.|  
|[CDBPropIDSet](../../data/oledb/cdbpropidset-cdbpropidset.md)|Constructor.|  
|[SetGUID](../../data/oledb/cdbpropidset-setguid.md)|Establece el GUID del identificador de propiedad de conjunto.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](../../data/oledb/cdbpropidset-operator-equal.md)|Asigna el contenido de un identificador de propiedad de un juego a otro.|  
  
## <a name="remarks"></a>Comentarios  
 Uso de los consumidores de OLE DB **DBPROPIDSET** estructuras para pasar una matriz de identificadores de propiedad para el que el consumidor desea obtener información sobre las propiedades. Las propiedades identificadas en una sola [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) estructura pertenecen al conjunto de una propiedad.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)