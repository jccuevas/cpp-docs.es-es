---
title: 'CRowset:: Movetoratio | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9c864933070af4f2a40572d0133027fb81f0855a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096670"
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