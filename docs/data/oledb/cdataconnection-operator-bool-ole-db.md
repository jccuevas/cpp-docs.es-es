---
title: 'CDataConnection:: operator bool (OLE DB) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: e0791faf-2ed2-4dbb-9e68-3b9b5da2b7a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1f466085f1003ca14f9df6db648ba7a3f833b3b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093446"
---
# <a name="cdataconnectionoperator-bool-ole-db"></a>CDataConnection::operator bool (OLE DB)
Determina si la sesión actual está abierta o no.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
operator bool() throw();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Devuelve un `bool` valor (tipo de datos de C++). **True** significa que la sesión actual está abierta; **false** significa que se cierra la sesión actual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (clase)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator BOOL](../../data/oledb/cdataconnection-operator-bool.md)