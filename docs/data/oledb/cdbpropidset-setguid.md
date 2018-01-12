---
title: 'Cdbpropidset:: SetGuid | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
dev_langs: C++
helpviewer_keywords: SetGUID method
ms.assetid: 8dd0f3bf-1490-4d53-9063-322b8d821bbe
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa70e704cd8e132404442ef390ea5582155a76e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropidsetsetguid"></a>CDBPropIDSet::SetGUID
Establece el campo GUID de la **DBPROPIDSET** estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      void SetGUID(   
   const GUID& guid    
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guid`  
 [in] Un GUID que se utiliza para establecer el **guidPropertySet** campo de la [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) estructura.  
  
## <a name="remarks"></a>Comentarios  
 Este campo se puede establecer la [constructor](../../data/oledb/cdbpropidset-cdbpropidset.md) así. Llame a esta función si utiliza el constructor predeterminado para esta clase.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDBPropIDSet (Clase)](../../data/oledb/cdbpropidset-class.md)