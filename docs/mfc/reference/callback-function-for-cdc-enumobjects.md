---
title: "Función de devolución de llamada para CDC:: EnumObjects | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::EnumObjects
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::EnumObjects
ms.assetid: 380088b1-88a5-4fb4-bbb5-dd9e8386572b
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: e4b24b5f5333d5514b9fdf69d204bca5d7947d7a
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcenumobjects"></a>Función de devolución de llamada para CDC::EnumObjects
El *ObjectFunc* nombre es un marcador de posición para el nombre de la función proporcionada por la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,  
    LPSTR* lpData);
```  
  
#### <a name="parameters"></a>Parámetros  
 *lpszLogObject*  
 Apunta a un [LOGPEN](../../mfc/reference/logpen-structure.md) o [LOGBRUSH](../../mfc/reference/logbrush-structure.md) estructura de datos que contiene información acerca de los atributos de la lógicos del objeto.  
  
 `lpData`  
 Apunta a los datos proporcionados por la aplicación pasa a la `EnumObjects` (función).  
  
## <a name="return-value"></a>Valor devuelto  
 La función de devolución de llamada devuelve un `int`. El valor de esta devolución es definido por el usuario. Si la función de devolución de llamada devuelve 0, `EnumObjects` deja de enumeración al principio.  
  
## <a name="remarks"></a>Comentarios  
 Se debe exportar el nombre real.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)


