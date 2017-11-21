---
title: 'Cdberrorinfo:: Getbasicerrorinfo | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
dev_langs: C++
helpviewer_keywords: GetBasicErrorInfo method
ms.assetid: 263cec53-63f6-48fe-b46e-31d20251863e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6e8fa2ae4e7e44fb04b6fd3747ffd50ff617c227
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdberrorinfogetbasicerrorinfo"></a>CDBErrorInfo::GetBasicErrorInfo
Llamadas [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) para devolver información básica sobre el error, como el código de retorno y el número de error específico del proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT GetBasicErrorInfo(   
   ULONG ulRecordNum,   
   ERRORINFO* pErrorInfo    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDBErrorInfo (Clase)](../../data/oledb/cdberrorinfo-class.md)