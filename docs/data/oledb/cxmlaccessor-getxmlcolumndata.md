---
title: CXMLAccessor::GetXMLColumnData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
dev_langs:
- C++
helpviewer_keywords:
- GetXMLColumnData method
ms.assetid: 719e8efe-8758-4af7-a855-0e44ea196546
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0e9a11434be63b75eef5ac0aaed729b7a8c2f0b7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cxmlaccessorgetxmlcolumndata"></a>CXMLAccessor::GetXMLColumnData
Recupera la información de tipo de columna de una tabla como datos de cadena con formato XML, por columna.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `strOutput`  
 [out] Una referencia a un búfer de cadena que contiene la información de tipo de columna van a recuperar. La cadena está formateada con los nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
## <a name="remarks"></a>Comentarios  
 A continuación muestra cómo se da formato a la información de tipo de columna en XML. `type` Especifica el tipo de datos de la columna. Tenga en cuenta que los tipos de datos se basan en tipos de datos de OLE DB, no sucede con los de la base de datos que se obtiene acceso.  
  
 `<columninfo>`  
  
 `<column type = I2/> ColumnName`  
  
 `</columninfo>`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CXMLAccessor (Clase)](../../data/oledb/cxmlaccessor-class.md)