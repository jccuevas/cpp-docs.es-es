---
title: 'CCommand:: CreateCommand | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
dev_langs: C++
helpviewer_keywords: CreateCommand method
ms.assetid: 3652a313-07a1-40ec-82d6-fc7182f2a6f6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b5ed543cb58316a617590d4304a72459d606429
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="ccommandcreatecommand"></a>CCommand::CreateCommand
Crea un nuevo comando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT CCommandBase::CreateCommand(  
   const CSession& session   
) throw ( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `session`  
 [in] Un `CSession` objeto que se asociará con el nuevo comando.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método crea un comando con el objeto de sesión especificado.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CCommand (Clase)](../../data/oledb/ccommand-class.md)