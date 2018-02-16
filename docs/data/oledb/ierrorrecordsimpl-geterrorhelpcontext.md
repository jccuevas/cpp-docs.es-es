---
title: IErrorRecordsImpl::GetErrorHelpContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetErrorHelpContext
- IErrorRecordsImpl::GetErrorHelpContext
- IErrorRecordsImpl.GetErrorHelpContext
dev_langs:
- C++
helpviewer_keywords:
- GetErrorHelpContext method
ms.assetid: 53d70239-0d64-482e-9ad4-4e1f4f02d5a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 603ac50d787a8f6f94e3efb38e1ca473b4ec7b79
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ierrorrecordsimplgeterrorhelpcontext"></a>IErrorRecordsImpl::GetErrorHelpContext
Obtiene el identificador de contexto de Ayuda de un registro de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      DWORD GetErrorHelpContext(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rCurError`  
 Un `ERRORINFO` registros en un **IErrorInfo** interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Id. de contexto de ayuda para el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IErrorRecordsImpl (Clase)](../../data/oledb/ierrorrecordsimpl-class.md)