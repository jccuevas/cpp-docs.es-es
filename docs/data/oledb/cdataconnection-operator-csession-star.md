---
title: 'CDataConnection:: operator CSession * | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
dev_langs:
- C++
helpviewer_keywords:
- operator CSession*
- CSession* operator
ms.assetid: 0b0feede-5c3e-4835-be5b-03651597014d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 97219418f18220cde84c80cb9052f17552a3a45d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094474"
---
# <a name="cdataconnectionoperator-csession"></a>CDataConnection::operator CSession*
Devuelve un puntero para el objeto contenido `CSession` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
operator const CSession*() throw();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Este operador devuelve un puntero para el objeto contenido `CSession` objeto, lo que le permite pasar un `CDataConnection` objeto donde un `CSession` puntero se espera.  
  
## <a name="example"></a>Ejemplo  
 Vea [operador CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) para obtener un ejemplo de uso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (clase)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md)