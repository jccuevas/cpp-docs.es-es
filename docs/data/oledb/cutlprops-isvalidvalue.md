---
title: 'CUtlProps:: IsValidValue | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
dev_langs:
- C++
helpviewer_keywords:
- IsValidValue method
ms.assetid: 1164556e-8d98-429c-a396-fc9a699e0e97
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0a37f0e0e9d415f9b7c78c8a619fd7fd66d24f28
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101970"
---
# <a name="cutlpropsisvalidvalue"></a>CUtlProps::IsValidValue
Se utiliza para validar un valor antes de establecer una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
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