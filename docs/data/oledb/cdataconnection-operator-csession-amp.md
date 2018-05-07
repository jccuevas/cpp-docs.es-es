---
title: 'CDataConnection:: operator CSession&amp; | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
dev_langs:
- C++
helpviewer_keywords:
- operator CSession&
- CSession& operator
ms.assetid: fba1e498-e482-4dda-8e0f-2542163bf627
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d46aeb352016c41dddaee972d438be8c28e22a9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdataconnectionoperator-csessionamp"></a>CDataConnection:: operator CSession&amp;
Devuelve una referencia al contenido `CSession` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
operator const CSession&();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Este operador devuelve una referencia a contenido `CSession` objeto, lo que le permite pasar un `CDataConnection` objeto donde un `CSession` referencia se espera.  
  
## <a name="example"></a>Ejemplo  
 Si tiene una función (como `func` a continuación) que toma un `CSession` referencia, puede usar **CSession &** para pasar un `CDataConnection` objeto en su lugar.  
  
 [!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (clase)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CSession*](../../data/oledb/cdataconnection-operator-csession-star.md)