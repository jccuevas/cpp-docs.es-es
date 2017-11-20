---
title: 'CRowset:: GetOriginalData | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.GetOriginalData
- CRowset<TAccessor>::GetOriginalData
- GetOriginalData
- ATL::CRowset<TAccessor>::GetOriginalData
- ATL.CRowset.GetOriginalData
- CRowset::GetOriginalData
- ATL::CRowset::GetOriginalData
- CRowset.GetOriginalData
dev_langs: C++
helpviewer_keywords: GetOriginalData method
ms.assetid: 5b69d30e-34f4-41a4-a82d-cd175be88d53
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d7a1c5fe26d17ac353138abc21b3ae46d9a72101
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetgetoriginaldata"></a>CRowset::GetOriginalData
Llamadas **IRowsetUpdate::GetOriginalData** para recuperar los datos que se captura más recientemente o transmitida al origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT GetOriginalData( ) throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método recupera los datos que se captura más recientemente o transmitida al origen de datos; no recuperan valores basados en los cambios pendientes.  
  
 Este método requiere que la interfaz opcional `IRowsetUpdate`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetUpdate** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [IRowsetUpdate::GetOriginalData](https://msdn.microsoft.com/en-us/library/ms709947.aspx)