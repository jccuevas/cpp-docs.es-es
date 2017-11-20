---
title: CSession (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CSession
- ATL::CSession
- ATL.CSession
dev_langs: C++
helpviewer_keywords: CSession class
ms.assetid: 83cd798f-b45d-4f11-a23c-29183390450c
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8b62b22f7e5a4cd4da0486069b31d80e3a2e18af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="csession-class"></a>CSession (Clase)
Representa una sesión de acceso de base de datos único.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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