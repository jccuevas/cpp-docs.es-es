---
title: 'CUtlProps:: OnPropertyChanged | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
dev_langs:
- C++
helpviewer_keywords:
- OnPropertyChanged method
ms.assetid: c5924210-b685-46c4-87f8-1b81e5bd3378
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3117a22a2b08b95528692d88cfb6e136d209e346
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cutlpropsonpropertychanged"></a>CUtlProps::OnPropertyChanged
Se llama después de establecer una propiedad que se va a administrar propiedades encadenadas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,  
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
 Si desea controlar propiedades encadenadas, como marcadores o actualizaciones cuyos valores dependen del valor de otra propiedad, se debe reemplazar esta función.  
  
## <a name="example"></a>Ejemplo  
 En esta función, el usuario obtiene el identificador de propiedad de la `DBPROP*` parámetro. Ahora, es posible comparar el identificador en una propiedad de cadena. Cuando se encuentra la propiedad, `SetProperties` se llama con la propiedad que se establecerá ahora junto con la otra propiedad. En este caso, si uno obtiene la `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, o `DBPROP_ORDEREDBOOKMARKS` propiedad, uno puede establecer el `DBPROP_BOOKMARKS` propiedad.  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CUtlProps (Clase)](../../data/oledb/cutlprops-class.md)