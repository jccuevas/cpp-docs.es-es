---
title: COLUMN_NAME_PS_STATUS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_NAME_PS_STATUS
dev_langs: C++
helpviewer_keywords: COLUMN_NAME_PS_STATUS macro
ms.assetid: 134e1bfe-abfa-4b64-9159-e492f31de44b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0505197265a2507927aa5e7e7d09d0bd8d0029c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="columnnamepsstatus"></a>COLUMN_NAME_PS_STATUS
Representa un enlace en el conjunto de filas a la columna específica en el conjunto de filas. Similar a [COLUMN_NAME](../../data/oledb/column-name.md), salvo que esta macro también toma la precisión, escala y columna de estado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
COLUMN_NAME_PS_STATUS(  
pszName  
,   
nPrecision  
,   
nScale  
,   
data  
,   
status )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszName`  
 [in] Un puntero al nombre de columna. El nombre debe ser una cadena Unicode. Puede lograr esto colocando un 'L' delante del nombre, por ejemplo: `L"MyColumn"`.  
  
 `nPrecision`  
 [in] La precisión máxima de la columna que desea enlazar.  
  
 `nScale`  
 [in] La escala de la columna que desea enlazar.  
  
 `data`  
 [in] El miembro de datos correspondiente en el registro de usuario.  
  
 *status*  
 [in] La variable esté enlazado con el estado de la columna.  
  
## <a name="remarks"></a>Comentarios  
 Vea [COLUMN_NAME](../../data/oledb/column-name.md) para obtener información sobre dónde el **COLUMN_NAME_\***  se utilizan macros.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)   
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)