---
title: 'CArrayRowset:: operator | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CArrayRowset::operator[]
- CArrayRowset.operator[]
dev_langs: C++
helpviewer_keywords:
- operator [], arrays
- '[] operator'
- operator[], arrays
ms.assetid: 3bb8c310-cc1e-46e8-9711-9b565488acaa
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 61929df340fb12afc5c2abdc6bd9f4e8bd899108
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="carrayrowsetoperator"></a>CArrayRowset::operator
Proporciona la sintaxis de matriz para tener acceso a una fila del conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
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