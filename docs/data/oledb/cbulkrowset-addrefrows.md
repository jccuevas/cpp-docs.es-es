---
title: 'CBulkRowset:: Addrefrows | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CBulkRowset::AddRefRows
- AddRefRows
- CBulkRowset.AddRefRows
- ATL.CBulkRowset<TAccessor>.AddRefRows
- ATL::CBulkRowset::AddRefRows
- CBulkRowset<TAccessor>::AddRefRows
- ATL.CBulkRowset.AddRefRows
- ATL::CBulkRowset<TAccessor>::AddRefRows
dev_langs: C++
helpviewer_keywords: AddRefRows method
ms.assetid: 014be991-50f8-4377-ba16-fec80b54b406
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aa9b84841147add979d420f3fcdb9967b5b97a21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cbulkrowsetaddrefrows"></a>CBulkRowset::AddRefRows
Llamadas [IRowset::AddRefRows](https://msdn.microsoft.com/en-us/library/ms719619.aspx) para incrementar el recuento de referencias para todas las filas recuperadas actualmente desde el conjunto de filas bulk.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
HRESULT AddRefRows( ) throw( );  
  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CBulkRowset (clase)](../../data/oledb/cbulkrowset-class.md)   
 [CBulkRowset::ReleaseRows](../../data/oledb/cbulkrowset-releaserows.md)