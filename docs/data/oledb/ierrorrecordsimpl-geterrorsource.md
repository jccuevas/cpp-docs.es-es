---
title: 'IErrorRecordsImpl:: Geterrorsource | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IErrorRecordsImpl.GetErrorSource
- GetErrorSource
- IErrorRecordsImpl::GetErrorSource
dev_langs: C++
helpviewer_keywords: GetErrorSource method
ms.assetid: 5436f1ce-c5a4-403b-a62b-c58e70e5c925
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5f566a8657d4ca31ec4d3a946b0069243a5c18af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ierrorrecordsimplgeterrorsource"></a>IErrorRecordsImpl::GetErrorSource
Obtiene el código de origen que causó el error de un registro de error.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      LPOLESTR GetErrorSource(  
   ERRORINFO& rCurError   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `rCurError`  
 Un `ERRORINFO` registros en un **IErrorInfo** interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero a una cadena que contiene el código fuente para el error.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IErrorRecordsImpl (Clase)](../../data/oledb/ierrorrecordsimpl-class.md)