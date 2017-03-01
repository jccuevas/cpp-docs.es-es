---
title: "Función de devolución de llamada para CDC:: SETABORTPROC | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Callback Function for CDC::SetAbortProc
dev_langs:
- C++
helpviewer_keywords:
- callback functions, for CDC::SetAbortProc
ms.assetid: daa36d5d-15de-40fc-8d37-a865d06c4710
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
ms.openlocfilehash: 1ba16ea60d8b18abd1962ded2da7e11ff2ef09a1
ms.lasthandoff: 02/24/2017

---
# <a name="callback-function-for-cdcsetabortproc"></a>Función de devolución de llamada para CDC::SetAbortProc
El nombre *AbortFunc* es un marcador de posición para el nombre de la función proporcionada por la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,  
    int code);
```  
  
#### <a name="parameters"></a>Parámetros  
 *hPr*  
 Identifica el contexto de dispositivo.  
  
 `code`  
 Especifica si se ha producido un error. Es 0 si no se ha producido ningún error. Es **SP_OUTOFDISK** si el Administrador de impresión está quedando sin espacio y más espacio en disco estará disponible si la aplicación espera. Si `code` es **SP_OUTOFDISK**, la aplicación no tiene que anular el trabajo de impresión. Si no es así, debe dar al administrador de impresión mediante una llamada a la **PeekMessage** o **GetMessage** función de Windows.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor devuelto de la función de controlador de interrupción es distinto de cero si el trabajo de impresión es continuar y 0 si se cancela.  
  
## <a name="remarks"></a>Comentarios  
 El nombre real debe exportarse como se describe en la sección Comentarios de [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CDC:: SETABORTPROC](../../mfc/reference/cdc-class.md#setabortproc)


