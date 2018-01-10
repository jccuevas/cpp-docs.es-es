---
title: 'CDBPropSet:: CDBPropSet | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
dev_langs: C++
helpviewer_keywords: CDBPropSet class, constructor
ms.assetid: 02ae5d9e-c067-47ca-8111-a03e86b5626b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 239f6c0a03186736d35b8d082913aeb76cac1d14
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdbpropsetcdbpropset"></a>CDBPropSet::CDBPropSet
El constructor. Inicializa el **rgProperties**, **cProperties**, y **guidPropertySet** campos de la [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      CDBPropSet(  
   const GUID& guid   
);  
CDBPropSet(   
   const CDBPropSet& propset    
);  
CDBPropSet( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guid`  
 [in] Un GUID que se utiliza para inicializar el **guidPropertySet** campo.  
  
 *conjunto de propiedades*  
 [in] Otro `CDBPropSet` objeto para la construcción de copia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDBPropSet (clase)](../../data/oledb/cdbpropset-class.md)   
 [CDBPropSet:: SetGuid](../../data/oledb/cdbpropset-setguid.md)   
 [Estructura DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx)