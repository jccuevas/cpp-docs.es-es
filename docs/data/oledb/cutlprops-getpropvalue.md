---
title: 'CUtlProps:: GetPropValue | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
dev_langs: C++
helpviewer_keywords: GetPropValue method
ms.assetid: 9a3fbadb-7814-48f7-96a4-b960fc4ecf2e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f6af9c8d909039927a7b4ad1f4840adac4353c97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cutlpropsgetpropvalue"></a>CUtlProps::GetPropValue
Obtiene una propiedad de un conjunto de propiedades.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      OUT_OF_LINE HRESULT GetPropValue(  
   const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pguidPropSet`  
 [in] El GUID para el conjunto de propiedades.  
  
 `dwPropId`  
 [in] El índice de la propiedad.  
  
 `pvValue`  
 [out] Un puntero a una variante que contiene el nuevo valor de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 `Failure`en caso de error y `S_OK` si se realiza correctamente.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CUtlProps (Clase)](../../data/oledb/cutlprops-class.md)