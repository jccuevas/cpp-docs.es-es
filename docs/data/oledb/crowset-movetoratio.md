---
title: CRowset::MoveToRatio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MoveToRatio
- CRowset<TAccessor>::MoveToRatio
- CRowset::MoveToRatio
- CRowset<TAccessor>.MoveToRatio
- ATL.CRowset.MoveToRatio
- ATL::CRowset::MoveToRatio
- CRowset.MoveToRatio
- ATL.CRowset<TAccessor>.MoveToRatio
- ATL::CRowset<TAccessor>::MoveToRatio
dev_langs:
- C++
helpviewer_keywords:
- MoveToRatio method
ms.assetid: 1fa313bd-8fd1-4608-8e85-44993b97dd88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: df1e7f51fb1bf82ced62c18a863f25870a4e4493
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetmovetoratio"></a>CRowset::MoveToRatio
Captura de filas a partir de una posición fracciones del conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
HRESULT MoveToRatio(DBCOUNTITEM nNumerator,   
   DBCOUNTITEM nDenominator,bool bForward = true) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nNumerator`  
 [in] El numerador usa para determinar las fracciones posicionales desde el que se va a capturar datos.  
  
 `nDenominator`  
 [in] El denominador que se utiliza para determinar las fracciones posicionales desde el que se va a capturar datos.  
  
 `bForward`  
 [in] Indica si se debe avanzar o retroceder. Es el valor predeterminado.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 `MoveToRatio` recupera filas de aproximadamente, según la siguiente fórmula:  
  
 `(nNumerator *  RowsetSize ) / nDenominator`  
  
 donde `RowsetSize` es el tamaño del conjunto de filas, medido en filas. La precisión de esta fórmula depende del proveedor específico. Para obtener más información, consulte [IRowsetScroll:: GetRowsAtRatio](https://msdn.microsoft.com/en-us/library/ms709602.aspx).  
  
 Este método requiere que la interfaz opcional `IRowsetScroll`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetScroll** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (Clase)](../../data/oledb/crowset-class.md)