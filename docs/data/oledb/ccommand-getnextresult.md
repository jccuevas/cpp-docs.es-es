---
title: 'CCommand:: GetNextResult | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
dev_langs:
- C++
helpviewer_keywords:
- GetNextResult method
ms.assetid: 63df9b55-9490-45c4-934a-879c5c2725d8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fa77785373545b2c4efd2faef0a8c0a02ee26910
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ccommandgetnextresult"></a>CCommand::GetNextResult
Obtiene el siguiente conjunto de resultados si hay uno disponible.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,  
   bool bBind = true) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pulRowsAffected*  
 [los in/out] Un puntero a memoria que se devuelve el recuento de filas afectadas por un comando.  
  
 `bBind`  
 [in] Especifica si se debe enlazar el comando automáticamente después de que se está ejecutando. El valor predeterminado es **true**, lo que hace que el comando enlazar automáticamente. Establecer `bBind` a **false** evita que el enlace automático del comando para que pueda enlazar manualmente. (Enlace manual es de particular interés para los usuarios OLAP).  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Si un conjunto de resultados se hayan extraído anteriormente, esta función libera el conjunto de resultados anterior y desenlaza las columnas. Si `bBind` es **true**, enlaza las columnas nuevas.  
  
 Debería llamar a esta función solo si ha especificado varios resultados estableciendo la `CCommand` parámetro de plantilla *TMultiple*=`CMultipleResults`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (Clase)](../../data/oledb/ccommand-class.md)