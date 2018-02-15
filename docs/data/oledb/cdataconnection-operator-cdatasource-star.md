---
title: 'CDataConnection:: operator CDataSource * | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
dev_langs:
- C++
helpviewer_keywords:
- CDataSource* operator
- operator * (CDataSource)
ms.assetid: 9118e324-e68d-45c5-a791-03f041d420ed
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 25e5f175579989f033a746263924758816bf63a3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdataconnectionoperator-cdatasource"></a>CDataConnection::operator CDataSource*
Devuelve un puntero para el objeto contenido `CDataSource` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
operator const CDataSource*() throw();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Este operador devuelve un puntero para el objeto contenido `CDataSource` objeto, lo que le permite pasar un `CDataConnection` objeto donde un `CDataSource` puntero se espera.  
  
 Vea [operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) para obtener un ejemplo de uso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (clase)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)