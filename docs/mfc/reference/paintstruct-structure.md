---
title: PAINTSTRUCT (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- PAINTSTRUCT
dev_langs:
- C++
helpviewer_keywords:
- PAINTSTRUCT structure [MFC]
ms.assetid: 81ce4993-3e89-43b2-8c98-7946f1314d24
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bfeddfd1ebf0c5c2247b27a0c69a8a6ef33e7766
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370443"
---
# <a name="paintstruct-structure"></a>PAINTSTRUCT (Estructura)
El `PAINTSTRUCT` estructura contiene información que puede utilizarse para pintar el área de cliente de una ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagPAINTSTRUCT {  
    HDC hdc;  
    BOOL fErase;  
    RECT rcPaint;  
    BOOL fRestore;  
    BOOL fIncUpdate;  
    BYTE rgbReserved[16];  
} PAINTSTRUCT;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *HDC*  
 Identifica el contexto de presentación que se utiliza para pintar.  
  
 *fErase*  
 Especifica si es necesario volver a dibujar el fondo. No es 0 si la aplicación debe volver a dibujar el fondo. La aplicación es responsable de dibujar el fondo si se crea una clase de ventana de Windows sin un pincel de fondo (vea la descripción de la **hbrBackground** miembro de la [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura en el SDK de Windows).  
  
 *rcPaint*  
 Especifica la esquina superior izquierda esquinas e inferior derecha del rectángulo en el que se solicita la pintura.  
  
 *fRestore*  
 Miembro reservado. Se utiliza internamente por Windows.  
  
 *fIncUpdate*  
 Miembro reservado. Se utiliza internamente por Windows.  
  
 *rgbReserved [16]*  
 Miembro reservado. Un bloque reservado de memoria utilizada internamente por Windows.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPaintDC::m_ps](../../mfc/reference/cpaintdc-class.md#m_ps)

