---
title: 'Cdberrorinfo:: Getcustomerrorobject | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
dev_langs: C++
helpviewer_keywords: GetCustomErrorObject method
ms.assetid: 295c053c-b76c-47a5-adfb-333e65d2df0d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9367c048ec78990f0544c745256a27916b46f919
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdberrorinfogetcustomerrorobject"></a>CDBErrorInfo::GetCustomErrorObject
Llamadas [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) para devolver un puntero a una interfaz en un objeto de error personalizado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT GetCustomErrorObject(   
   ULONG ulRecordNum,   
   REFIID riid,   
   IUnknown** ppObject    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDBErrorInfo (Clase)](../../data/oledb/cdberrorinfo-class.md)