---
title: 'CCommand:: Unprepare | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
dev_langs: C++
helpviewer_keywords: Unprepare method
ms.assetid: 4fe59988-fe51-4c7c-a156-72b68e3d642b
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 19622da4735d4dba86079c9009ddc52ffabd1e9d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccommandunprepare"></a>CCommand::Unprepare
Descarta el plan de ejecución del comando actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT CCommandBase::Unprepare( ) throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método ajusta el método de OLE DB [ICommandPrepare:: Unprepare](https://msdn.microsoft.com/en-us/library/ms719635.aspx).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (Clase)](../../data/oledb/ccommand-class.md)