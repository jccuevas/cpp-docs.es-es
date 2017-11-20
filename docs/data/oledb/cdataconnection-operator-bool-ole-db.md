---
title: 'CDataConnection:: operator bool (OLE DB) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
dev_langs: C++
helpviewer_keywords:
- BOOL operator
- operator bool
ms.assetid: e0791faf-2ed2-4dbb-9e68-3b9b5da2b7a7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: be875b6d8a048472a2ddafa56f16101959704270
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectionoperator-bool-ole-db"></a>CDataConnection::operator bool (OLE DB)
Determina si la sesión actual está abierta o no.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
operator bool( ) throw( );  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Devuelve un `bool` valor (tipo de datos de C++). **True** significa que la sesión actual está abierta; **false** significa que se cierra la sesión actual.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (clase)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator BOOL](../../data/oledb/cdataconnection-operator-bool.md)