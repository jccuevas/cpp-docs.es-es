---
title: 'IErrorRecordsImpl:: Geterrordescriptionstring | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- GetErrorDescriptionString
- IErrorRecordsImpl.GetErrorDescriptionString
- IErrorRecordsImpl::GetErrorDescriptionString
dev_langs:
- C++
helpviewer_keywords:
- GetErrorDescriptionString method
ms.assetid: 8bc71c45-ca9f-4632-bb02-1aa9ed8086c4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b52bfba3313b6d5fe6423f3911bbef6af5253e86
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ierrorrecordsimplgeterrordescriptionstring"></a>IErrorRecordsImpl::GetErrorDescriptionString
Obtiene la cadena de descripción del error de un registro de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      LPOLESTR GetErrorDescriptionString(ERRORINFO& rCurError);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rCurError`  
 Un `ERRORINFO` registros en un **IErrorInfo** interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Un puntero a una cadena que describe el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IErrorRecordsImpl (Clase)](../../data/oledb/ierrorrecordsimpl-class.md)