---
title: BEGIN_COLUMN_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BEGIN_COLUMN_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_COLUMN_MAP macro
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 45d5438d1a4ba946aa3db36cc2b92eef1aa93ba3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="begincolumnmap"></a>BEGIN_COLUMN_MAP
Marca el inicio de una entrada de mapa de columnas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
BEGIN_COLUMN_MAP(x)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *x*  
 [in] Nombre de la clase de registro de usuario derivada de `CAccessor`.  
  
## <a name="remarks"></a>Comentarios  
 Esta macro se usa en el caso de un único descriptor de acceso en un conjunto de filas. Si tiene varios descriptores de acceso en un conjunto de filas, use [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
 La macro `BEGIN_COLUMN_MAP` se completa con la macro `END_COLUMN_MAP` . Esta macro se usa cuando solamente hay un descriptor de acceso necesario en el registro de usuario.  
  
 Las columnas corresponden a los campos del conjunto de filas que quiere enlazar.  
  
## <a name="example"></a>Ejemplo  
 Este es un mapa de columnas y parámetros de ejemplo:  
  
 <!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)