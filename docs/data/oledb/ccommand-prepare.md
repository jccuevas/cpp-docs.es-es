---
title: 'CCommand:: Prepare | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.Prepare
- CCommand::Prepare
- Prepare
dev_langs:
- C++
helpviewer_keywords:
- Prepare method
ms.assetid: f0e473fc-2f7a-4d29-96c2-1328dc21e702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d029664508b6be71348aa3aa8d5801191f2aca3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33089342"
---
# <a name="ccommandprepare"></a>CCommand::Prepare
Valida y optimiza el comando actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *cExpectedRuns*  
 [in] El número de veces que tiene previsto ejecutar el comando.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método ajusta el método de OLE DB [ICommandPrepare:: Prepare](https://msdn.microsoft.com/en-us/library/ms718370.aspx).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (Clase)](../../data/oledb/ccommand-class.md)