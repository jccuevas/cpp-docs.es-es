---
title: IErrorRecordsImpl::GetBasicErrorInfo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::IErrorRecordsImpl::GetBasicErrorInfo
- IErrorRecordsImpl::GetBasicErrorInfo
- GetBasicErrorInfo
- ATL.IErrorRecordsImpl.GetBasicErrorInfo
- IErrorRecordsImpl.GetBasicErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- GetBasicErrorInfo method
ms.assetid: d0b4dec3-f32a-4aaa-8365-524f2e7c8395
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2955b0f4579b92adba609e4854fb1cdef5b6a14b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ierrorrecordsimplgetbasicerrorinfo"></a>IErrorRecordsImpl::GetBasicErrorInfo
Devuelve información básica sobre el error, como el código de retorno y el número de error específico del proveedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(GetBasicErrorInfo )(ULONG ulRecordNum,  
   ERRORINFO *pErrorInfo);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IErrorRecordsImpl (Clase)](../../data/oledb/ierrorrecordsimpl-class.md)