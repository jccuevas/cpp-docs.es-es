---
title: 'CArrayRowset:: operator | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs:
- C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0921ad4c574c496656ec616d1d569158c596c5ad
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
Proporciona la sintaxis de matriz para tener acceso a una fila del conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      TAccessor  
      & operator[](int nrow);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `TAccessor`  
 Un parámetro de plantilla que especifica el tipo de descriptor de acceso almacenada en el conjunto de filas.  
  
 `nRow`  
 [in] Número de la fila (elemento de matriz) que desea tener acceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El contenido de la fila solicitada.  
  
## <a name="remarks"></a>Comentarios  
 Si `nRow` supera el número de filas del conjunto de filas, se produce una excepción.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CArrayRowset (Clase)](../../data/oledb/carrayrowset-class.md)