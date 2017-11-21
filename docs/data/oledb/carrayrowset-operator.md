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
ms.openlocfilehash: 14d0c07f8d1b8ff5cef19620fc00d156e251bf80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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