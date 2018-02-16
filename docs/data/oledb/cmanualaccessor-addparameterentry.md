---
title: 'CManualAccessor:: AddParameterEntry | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
dev_langs:
- C++
helpviewer_keywords:
- AddParameterEntry method
ms.assetid: 9048b164-052b-41b1-a861-227fc529e0b5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e0b730ad81eb827fb86b77b95d4abb96ac73b3c3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cmanualaccessoraddparameterentry"></a>CManualAccessor::AddParameterEntry
Agrega una entrada de parámetro a las estructuras de entrada de parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```
void AddParameterEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL,  
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en el *referencia del programador OLE DB*.  
  
 `nOrdinal`  
 [in] Número de parámetro.  
  
 `wType`  
 [in] Tipo de datos.  
  
 `nColumnSize`  
 [in] Tamaño de la columna en bytes.  
  
 `pData`  
 [in] Un puntero a la columna de datos almacenado en el búfer.  
  
 `pLength`  
 [in] Un puntero a la longitud de campo, si es necesario.  
  
 `pStatus`  
 [in] Un puntero a la variable esté enlazado con el estado de la columna, si es necesario.  
  
 *eParamIO*  
 [in] Especifica si el parámetro al que está asociado el enlace es un parámetro de entrada, entrada/salida o de salida.  
  
## <a name="remarks"></a>Comentarios  
 Para usar esta función, primero debe llamar a [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CManualAccessor (clase)](../../data/oledb/cmanualaccessor-class.md)   
 [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md)   
 [Ejemplo DBViewer](../../visual-cpp-samples.md)