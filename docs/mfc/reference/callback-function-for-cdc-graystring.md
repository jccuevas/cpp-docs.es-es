---
title: "Función de devolución de llamada para CDC:: graystring | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::GrayString
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::GrayString
ms.assetid: 5217e183-df48-426b-931b-6245022ca36f
caps.latest.revision: 11
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
ms.openlocfilehash: 3ce3afefae9618420a8a97b27994c33604745677
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcgraystring"></a>Función de devolución de llamada para CDC::GrayString
*OutputFunc* es un marcador de posición para el nombre de la función de devolución de llamada proporcionada por la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,  
    LPARAM lpData,  
    int nCount);
```  
  
#### <a name="parameters"></a>Parámetros  
 `hDC`  
 Identifica un contexto de dispositivo de memoria con un mapa de bits de al menos el ancho y alto especificado por `nWidth` y `nHeight` a `GrayString`.  
  
 `lpData`  
 Apunta a la cadena de caracteres que se va a dibujar.  
  
 `nCount`  
 Especifica el número de caracteres a la salida.  
  
## <a name="return-value"></a>Valor devuelto  
 Valor devuelto de la función de devolución de llamada debe ser **TRUE** para indicar éxito; de lo contrario es **FALSE**.  
  
## <a name="remarks"></a>Comentarios  
 La función de devolución de llamada (*OutputFunc*) debe dibujar una imagen en relación con las coordenadas (0,0) en lugar de (*x*, *y*).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC:: graystring](../../mfc/reference/cdc-class.md#graystring)


