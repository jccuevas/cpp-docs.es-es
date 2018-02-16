---
title: 'CDataConnection:: Opennewsession | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
dev_langs:
- C++
helpviewer_keywords:
- OpenNewSession method
ms.assetid: 0a70e573-9498-4ca7-b524-45666dc7b0a3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ee1d92178d0bb00e6ef3a760a4f775b7854696d2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdataconnectionopennewsession"></a>CDataConnection::OpenNewSession
Se abre una nueva sesión con el origen de datos del objeto de conexión actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OpenNewSession(CSession & session) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `session`  
 [los in/out] Una referencia al objeto de nueva sesión.  
  
 **Comentarios**  
 La nueva sesión utiliza el objeto de origen de datos independiente del objeto de conexión actual como su elemento primario y puede tener acceso a toda la misma información que el origen de datos.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (Clase)](../../data/oledb/cdataconnection-class.md)