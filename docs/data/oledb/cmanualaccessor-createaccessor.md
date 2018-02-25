---
title: 'CManualAccessor:: CreateAccessor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
dev_langs:
- C++
helpviewer_keywords:
- CreateAccessor method
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 44b9edf987baf9ff2470ed536a1c657025766f23
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cmanualaccessorcreateaccessor"></a>CManualAccessor::CreateAccessor
Asigna memoria a estructuras de enlace de la columna e inicializa a los miembros de datos de columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nBindEntries`  
 [in] Número de columnas. Este número debe coincidir con el número de llamadas a la [CManualAccessor:: AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) función.  
  
 `pBuffer`  
 [in] Un puntero al búfer donde se almacenan las columnas de salida.  
  
 `nBufferSize`  
 [in] El tamaño del búfer en bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
## <a name="remarks"></a>Comentarios  
 Llame a esta función antes de llamar a la `CManualAccessor::AddBindEntry` (función).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CManualAccessor (clase)](../../data/oledb/cmanualaccessor-class.md)   
 [Ejemplo DBViewer](../../visual-cpp-samples.md)