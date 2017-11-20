---
title: BEGIN_COLUMN_MAP | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BEGIN_COLUMN_MAP
dev_langs: C++
helpviewer_keywords: BEGIN_COLUMN_MAP macro
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 29e62e08ef03d863b17ea0d269cf049b23602774
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="begincolumnmap"></a>BEGIN_COLUMN_MAP
Marca el inicio de una entrada de mapa de columnas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
BEGIN_COLUMN_MAP(  
x  
 )  
  
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