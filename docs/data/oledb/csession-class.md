---
title: CSession (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs:
- C++
helpviewer_keywords:
- CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 03c0bfec758bb663803b05b1f690816394f61239
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097086"
---
# <a name="csession-class"></a>CSession (Clase)
Representa una sesión de acceso de base de datos único.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CSession  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Anulación](../../data/oledb/csession-abort.md)|Cancela (finaliza) la transacción.|  
|[Cerrar](../../data/oledb/csession-close.md)|Cierra la sesión.|  
|[Confirmación](../../data/oledb/csession-commit.md)|Confirma la transacción.|  
|[GetTransactionInfo](../../data/oledb/csession-gettransactioninfo.md)|Devuelve información relativa a una transacción.|  
|[Abrir](../../data/oledb/csession-open.md)|Abre una nueva sesión para el objeto de origen de datos.|  
|[StartTransaction](../../data/oledb/csession-starttransaction.md)|Comienza una nueva transacción para esta sesión.|  
  
## <a name="remarks"></a>Comentarios  
 Una o varias sesiones se pueden asociadas a cada conexión del proveedor (origen de datos), que se representa mediante un [CDataSource](../../data/oledb/cdatasource-class.md) objeto. Para crear un nuevo `CSession` para un `CDataSource`, llame a [CSession:: Open](../../data/oledb/csession-open.md). Para iniciar una transacción de base de datos, `CSession` proporciona el `StartTransaction` método. Una vez que se inicia una transacción, puede confirmar mediante la **confirmación** método, o en Cancelar mediante el **anular** método.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CatDB](../../visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)