---
title: 'CCommand:: ReleaseCommand | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
dev_langs:
- C++
helpviewer_keywords:
- ReleaseCommand method
ms.assetid: 3b58230c-13d5-45c5-b43e-bb013ecc3019
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a12b3fc3d12e79e93bd77bf02b6f7bfa87dc0052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094883"
---
# <a name="ccommandreleasecommand"></a>CCommand::ReleaseCommand
Libera el descriptor de acceso de parámetro, a continuación, libera el propio comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
void CCommandBase::ReleaseCommand() throw();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 `ReleaseCommand` se utiliza junto con **cerrar**. Vea [cerrar](../../data/oledb/ccommand-close.md) para obtener detalles de uso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (clase)](../../data/oledb/ccommand-class.md)   
 [CCommand::Close](../../data/oledb/ccommand-close.md)