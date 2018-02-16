---
title: CXMLAccessor::GetXMLRowData | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
dev_langs:
- C++
helpviewer_keywords:
- GetXMLRowData method
ms.assetid: 156b66e3-42fd-491c-8943-38cf5e36f687
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b4b0307b649b702ad78ddb90d9985e14df2331b1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cxmlaccessorgetxmlrowdata"></a>CXMLAccessor::GetXMLRowData
Recupera el contenido completo de una tabla como datos de cadena con formato XML, por fila.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,   
   bool bAppend = false) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `strOutput`  
 [out] Una referencia a un búfer que contiene los datos de la tabla va a recuperar. Los datos tienen el formato de datos de cadena con los nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.  
  
 *bAppend*  
 [in] Un valor booleano que especifica si se va a anexar una cadena al final de los datos de salida.  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
## <a name="remarks"></a>Comentarios  
 A continuación muestra cómo se da formato a la fila de datos en XML. `DATA` a continuación representa la fila de datos. Utilice move métodos para desplazarse a la fila deseada.  
  
 `<row>`  
  
 `<column name>DATA</column name>`  
  
 `</row>`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CXMLAccessor (Clase)](../../data/oledb/cxmlaccessor-class.md)