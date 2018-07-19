---
title: CRestrictions (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
dev_langs:
- C++
helpviewer_keywords:
- CRestrictions class
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b0b174a8e53f72b0077d10fd1728c4e726e0f218
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098490"
---
# <a name="crestrictions-class"></a>CRestrictions (Clase)
Una clase genérica que le permite especificar restricciones para conjuntos de filas de esquema.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T, short nRestrictions, const GUID* pguid>  
class CRestrictions : 
        public CSchemaRowset <T, nRestrictions>  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase utilizada para el descriptor de acceso.  
  
 `nRestrictions`  
 El número de columnas de restricción para el conjunto de filas de esquema.  
  
 `pguid`  
 Un puntero al GUID del servicio para el esquema.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Abrir](../../data/oledb/crestrictions-open.md)|Devuelve un resultado que se establece de acuerdo con las restricciones proporcionadas por el usuario.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbsch.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)