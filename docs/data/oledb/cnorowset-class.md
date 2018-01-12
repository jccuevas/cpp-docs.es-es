---
title: CNoRowset (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
dev_langs: C++
helpviewer_keywords: CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 901d857b5095dd882a368b9a87e8a7d38d20bc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cnorowset-class"></a>CNoRowset (Clase)
Puede usarse como un argumento de plantilla (`TRowset`) para [CCommand](../../data/oledb/ccommand-class.md) o [CTable](../../data/oledb/ctable-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <class TAccessor = CAccessorBase>  
class CNoRowset  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 Una clase de descriptor de acceso. De manera predeterminada, es `CAccessorBase`.  
  
## <a name="remarks"></a>Comentarios  
 Use `CNoRowset` como un argumento de plantilla si el comando no devuelve un conjunto de filas.  
  
 `CNoRowset`implementa los siguientes métodos de código auxiliar, cada uno de los cuales corresponde a otros métodos de la clase de descriptor de acceso:  
  
-   **BindFinished** -indica cuándo ha finalizado enlace (devuelve `S_OK`).  
  
-   **Cerrar** -libera filas y la interfaz IRowset actual.  
  
-   `GetIID`-Recupera el identificador de interfaz de un punto de conexión.  
  
-   **GetInterface** -recupera una interfaz.  
  
-   `GetInterfacePtr`-Recupera un puntero de interfaz encapsulado.  
  
-   **SetAccessor** -establece un puntero al descriptor de acceso.  
  
-   **SetupOptionalRowsetInterfaces** -configura interfaces opcionales para el conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)