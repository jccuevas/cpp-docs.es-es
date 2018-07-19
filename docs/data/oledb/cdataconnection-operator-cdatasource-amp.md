---
title: 'CDataConnection:: operator CDataSource&amp; | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
dev_langs:
- C++
helpviewer_keywords:
- CDataSource& operator
- operator & (CDataSource)
ms.assetid: 852faeee-f1b1-4465-9828-b261d1edf022
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8aca05cd83123e2866b8d46e5d5f085b5edd04f6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33093433"
---
# <a name="cdataconnectionoperator-cdatasourceamp"></a>CDataConnection:: operator CDataSource&amp;
Devuelve una referencia al contenido `CDataSource` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
operator const CDataSource&() throw();  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Este operador devuelve una referencia a contenido `CDataSource` objeto, lo que le permite pasar un `CDataConnection` objeto donde un `CDataSource` referencia se espera.  
  
## <a name="example"></a>Ejemplo  
 Si tiene una función (como `func` a continuación) que toma un `CDataSource` referencia, puede usar **CDataSource &** para pasar un `CDataConnection` objeto en su lugar.  
  
 [!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]  
  
 [!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (clase)](../../data/oledb/cdataconnection-class.md)   
 [CDataConnection::operator CDataSource*](../../data/oledb/cdataconnection-operator-cdatasource-star.md)