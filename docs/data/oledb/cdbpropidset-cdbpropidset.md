---
title: 'Cdbpropidset:: Cdbpropidset | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
dev_langs:
- C++
helpviewer_keywords:
- CDBPropIDSet class, constructor
ms.assetid: e68cc20e-fce2-4cc1-9e9d-05c542334cc8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 19fc024fc0edb11f5211ba51469adb622524454f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdbpropidsetcdbpropidset"></a>CDBPropIDSet::CDBPropIDSet
El constructor. Inicializa el **rgProperties**, **cProperties**y (opcionalmente) **guidPropertySet** campos de la [DBPROPIDSET](https://msdn.microsoft.com/en-us/library/ms717981.aspx) estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      CDBPropIDSet(const GUID& guid);  

CDBPropIDSet(const CDBPropIDSet& propidset);  

CDBPropIDSet();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guid`  
 [in] Un GUID que se utiliza para inicializar el **guidPropertySet** campo.  
  
 *propidset*  
 [in] Otro `CDBPropIDSet` objeto para la construcción de copia.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDBPropIDSet (clase)](../../data/oledb/cdbpropidset-class.md)   
 [CDBPropIDSet::SetGUID](../../data/oledb/cdbpropidset-setguid.md)