---
title: 'CManualAccessor:: AddBindEntry | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
dev_langs:
- C++
helpviewer_keywords:
- AddBindEntry method
ms.assetid: 8556dda9-dda1-4f67-96bc-6031e6c6a271
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59793bd61b17fe2ead4948932efa1b583da8e1a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098060"
---
# <a name="cmanualaccessoraddbindentry"></a>CManualAccessor::AddBindEntry
Agrega una entrada de enlace a las columnas de salida.  
  
## <a name="syntax"></a>Sintaxis  
  
```
void AddBindEntry(DBORDINAL nOrdinal,  
   DBTYPE wType,  DBLENGTH nColumnSize,  
   void* pData,  
   void* pLength = NULL,  
   void* pStatus = NULL) throw ();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [DBBINDING](https://msdn.microsoft.com/en-us/library/ms716845.aspx) en el *referencia del programador OLE DB*.  
  
 `nOrdinal`  
 [in] Número de columna.  
  
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
  
## <a name="remarks"></a>Comentarios  
 Para usar esta función, primero debe llamar a [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md). No se puede agregar más entradas que el número de columnas especificadas en `CreateAccessor`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CManualAccessor (clase)](../../data/oledb/cmanualaccessor-class.md)   
 [Ejemplo DBViewer](../../visual-cpp-samples.md)