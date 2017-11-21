---
title: 'CCommand:: ReleaseCommand | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
dev_langs: C++
helpviewer_keywords: ReleaseCommand method
ms.assetid: 3b58230c-13d5-45c5-b43e-bb013ecc3019
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 756e85d0fd3c00b65c3fee2f1f225327cf63a32a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandreleasecommand"></a>CCommand::ReleaseCommand
Libera el descriptor de acceso de parámetro, a continuación, libera el propio comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
void CCommandBase::ReleaseCommand( ) throw( );  
  
```  
  
## <a name="remarks"></a>Comentarios  
 `ReleaseCommand`se utiliza junto con **cerrar**. Vea [cerrar](../../data/oledb/ccommand-close.md) para obtener detalles de uso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (clase)](../../data/oledb/ccommand-class.md)   
 [CCommand::Close](../../data/oledb/ccommand-close.md)