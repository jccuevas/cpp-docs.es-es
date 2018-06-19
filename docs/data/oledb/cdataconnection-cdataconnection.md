---
title: 'CDataConnection:: CDataConnection | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 267341f88886f3ff94a6b828034e8acbaa2dc0c1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093329"
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
Crea e inicializa un `CDataConnection` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      CDataConnection();   

CDataConnection(const CDataConnection &ds);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ds`  
 [in] Una referencia a una conexión de datos existente.  
  
## <a name="remarks"></a>Comentarios  
 La invalidación de la primera crea un nuevo `CDataConnection` objeto con la configuración predeterminada.  
  
 El segundo reemplazada crea un nuevo `CDataConnection` objeto con una configuración equivalente para el objeto de conexión de datos que especificó.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (Clase)](../../data/oledb/cdataconnection-class.md)