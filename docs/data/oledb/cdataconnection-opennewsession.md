---
title: 'CDataConnection:: Opennewsession | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f20f66ec6cc494c14e99c50de4824ba68d27264d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094327"
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