---
title: BEGIN_PROPERTY_SET_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_PROPERTY_SET_EX
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROPERTY_SET_EX macro
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bc3738ca9fc03014b68cc47cadad32ac4865b0d1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="beginpropertysetex"></a>BEGIN_PROPERTY_SET_EX
Mapa del conjunto de marcas de que establece el principio de una propiedad en una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid  
, flags )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guid`  
 [in] El GUID de la propiedad.  
  
 `flags`  
 [in] **UPROPSET_HIDDEN** para los conjuntos de propiedades que no desea exponer, o **UPROPSET_PASSTHROUGH** para un proveedor de exponer propiedades definidas fuera del ámbito del proveedor.  
  
## <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)