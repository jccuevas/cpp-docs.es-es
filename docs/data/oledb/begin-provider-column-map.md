---
title: BEGIN_PROVIDER_COLUMN_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- BEGIN_PROVIDER_COLUMN_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_PROVIDER_COLUMN_MAP macro
ms.assetid: 506b8c0f-6be9-4c97-ba81-c4b7f7d428fa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4bc977f95dff0bf555d251bdfb75820875c668ca
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="beginprovidercolumnmap"></a>BEGIN_PROVIDER_COLUMN_MAP
Marca el principio de las entradas de asignación de columna de proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `theClass`  
 [in] El nombre de la clase a la que pertenece este mapa.  
  
## <a name="example"></a>Ejemplo  
 Este es un mapa de columnas del proveedor de ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [Plantillas del proveedor OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)