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
ms.openlocfilehash: 0d91cc0374474a38bd2caba66ab98003852195f9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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