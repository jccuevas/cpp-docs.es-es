---
title: 'CSession:: Open | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CSession::Open
- CSession::Open
- CSession.Open
- ATL.CSession.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: c2050c2c-9817-4857-be49-189f346968f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 919e87efcf38442954544c0471698fcbe5d563c9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="csessionopen"></a>CSession::Open
Abre una nueva sesión para el objeto de origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Open(const CDataSource& ds,  
   DBPROPSET *pPropSet = NULL,  
   ULONG ulPropSets = 0) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ds`  
 [in] El origen de datos para los que es la sesión que se abran.  
  
 *pPropSet*  
 [in] Un puntero a una matriz de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) las estructuras que contienen propiedades y valores que desea establecer. Vea [conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en el *referencia del programador OLE DB* en el SDK de Windows.  
  
 `ulPropSets`  
 [in] El número de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) estructuras pasan en el *pPropSet* argumento.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Debe abrir el objeto de origen de datos mediante [CDataSource:: Open](../../data/oledb/cdatasource-open.md) antes de pasarlo a `CSession::Open`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CSession (Clase)](../../data/oledb/csession-class.md)