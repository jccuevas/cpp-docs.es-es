---
title: 'CCommand:: GetNextResult | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d833c3e644ac6ed44216542ce4fc6d995cc22efa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094200"
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