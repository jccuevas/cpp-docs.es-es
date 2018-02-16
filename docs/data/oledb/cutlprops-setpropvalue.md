---
title: CUtlProps::SetPropValue | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
dev_langs:
- C++
helpviewer_keywords:
- SetPropValue method
ms.assetid: 69a703c0-f640-4ca3-8850-0c4e75d52429
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f129453d438858b4a4f74c8fc6bf602c97e33e56
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropssetpropvalue"></a>CUtlProps::SetPropValue
Establece una propiedad en un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pguidPropSet`  
 [in] El GUID para el conjunto de propiedades.  
  
 `dwPropId`  
 [in] El índice de la propiedad.  
  
 `pvValue`  
 [in] Un puntero a una variante que contiene el nuevo valor de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 `Failure` en caso de error y `S_OK` si se realiza correctamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CUtlProps (Clase)](../../data/oledb/cutlprops-class.md)