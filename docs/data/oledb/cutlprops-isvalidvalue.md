---
title: 'CUtlProps:: IsValidValue | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs: C++
helpviewer_keywords: IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 06193b8c560c5ac6006698813222e698a98bccc3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
Se utiliza para validar un valor antes de establecer una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      virtual HRESULT CUtlPropsBase::IsValidValue(  
   ULONG /* iCurSet */,  
   DBPROP* pDBProp   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `iCurSet`  
 El índice en la matriz de conjunto de propiedades; Devuelve cero si hay una sola propiedad.  
  
 `pDBProp`  
 El identificador de propiedad y el nuevo valor en un [DBPROP](https://msdn.microsoft.com/en-us/library/ms717970.aspx) estructura.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar. El valor predeterminado de valor devuelto es el valor `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 Si dispone de las rutinas de validación que desea ejecutar en un valor que va a utilizar para establecer una propiedad, se debe reemplazar esta función. Por ejemplo, podría validar **DBPROP_AUTH_PASSWORD** en una tabla de contraseña para determinar un valor válido.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CUtlProps (Clase)](../../data/oledb/cutlprops-class.md)