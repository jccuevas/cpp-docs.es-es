---
title: 'CUtlProps:: GetPropValue | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
dev_langs:
- C++
helpviewer_keywords:
- GetPropValue method
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 00f56c317f9325fa51f7165fc3872b1e4ca6e9da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cutlpropsgetpropvalue"></a>CUtlProps::GetPropValue
Obtiene una propiedad de un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pguidPropSet`  
 [in] El GUID para el conjunto de propiedades.  
  
 `dwPropId`  
 [in] El índice de la propiedad.  
  
 `pvValue`  
 [out] Un puntero a una variante que contiene el nuevo valor de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 `Failure` en caso de error y `S_OK` si se realiza correctamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CUtlProps (Clase)](../../data/oledb/cutlprops-class.md)