---
title: 'CBulkRowset:: Movetoratio | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset.MoveToRatio
- ATL::CBulkRowset::MoveToRatio
- MoveToRatio
- CBulkRowset::MoveToRatio
- ATL.CBulkRowset<TAccessor>.MoveToRatio
- ATL::CBulkRowset<TAccessor>::MoveToRatio
- ATL.CBulkRowset.MoveToRatio
- CBulkRowset<TAccessor>::MoveToRatio
dev_langs: C++
helpviewer_keywords: MoveToRatio method
ms.assetid: 86be60f5-9341-44c1-8e1e-9174c082d0d5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 98536344e3282008ace529565e6c8d805b546ef2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cbulkrowsetmovetoratio"></a>CBulkRowset::MoveToRatio
Captura de filas a partir de una posición fracciones del conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT MoveToRatio(  
   DBCOUNTITEM nNumerator,  
   DBCOUNTITEM nDenominator   
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nNumerator`  
 [in] El numerador utilizado para determinar la posición desde la que se va a capturar datos fraccionaria.  
  
 `nDenominator`  
 [in] El denominador que se utiliza para determinar la posición desde la que se va a capturar datos fraccionaria.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 `MoveToRatio`captura las filas más o menos según la siguiente fórmula:  
  
 `( nNumerator *  RowsetSize ) / nDenominator`  
  
 donde `RowsetSize` es el tamaño del conjunto de filas, medido en filas. La precisión de esta fórmula depende del proveedor específico. Para obtener más información, consulte [IRowsetScroll:: GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx) en el *referencia del programador de OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CBulkRowset (Clase)](../../data/oledb/cbulkrowset-class.md)