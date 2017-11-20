---
title: CDBPropSet (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
dev_langs: C++
helpviewer_keywords: CDBPropSet class
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 919a448a33bae03cfb1da9ba8bbed864cc92129d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdbpropset-class"></a>CDBPropSet (Clase)
Hereda de la **DBPROPSET** estructurar y agrega un constructor que inicializa los campos clave, así como la `AddProperty` acceder a método.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDBPropSet : public tagDBPROPSET  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddProperty](../../data/oledb/cdbpropset-addproperty.md)|Agrega una propiedad al conjunto de propiedades.|  
|[CDBPropSet](../../data/oledb/cdbpropset-cdbpropset.md)|Constructor.|  
|[SetGUID](../../data/oledb/cdbpropset-setguid.md)|Establece el **guidPropertySet** campo de la **DBPROPSET** estructura.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador =](../../data/oledb/cdbpropset-operator-equal.md)|Asigna el contenido de una propiedad establecida en el otro.|  
  
## <a name="remarks"></a>Comentarios  
 Uso de consumidores y proveedores OLE DB **DBPROPSET** estructuras para pasar matrices de `DBPROP` estructuras. Cada `DBPROP` estructura representa una propiedad única que se puede establecer.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CDBPropIDSet (clase)](../../data/oledb/cdbpropidset-class.md)   
 [Estructura DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx)   
 [Estructura DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)