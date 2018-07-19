---
title: CREATESTRUCT (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure [MFC]
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6036490b21ccbd86dfed56ea90226cbb2db8d596
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848475"
---
# <a name="createstruct-structure"></a>CREATESTRUCT (Estructura)
El `CREATESTRUCT` estructura define los parámetros de inicialización pasados al procedimiento de ventana de una aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef struct tagCREATESTRUCT {  
    LPVOID lpCreateParams;  
    HANDLE hInstance;  
    HMENU hMenu;  
    HWND hwndParent;  
    int cy;  
    int cx;  
    int y;  
    int x;  
    LONG style;  
    LPCSTR lpszName;  
    LPCSTR lpszClass;  
    DWORD dwExStyle;  
} CREATESTRUCT;  
```  
  
#### <a name="parameters"></a>Parámetros  
 *lpCreateParams*  
 Puntos de datos que se usará para crear la ventana.  
  
 *hInstance*  
 Identifica el identificador de instancia de módulo del módulo que posee la ventana nueva.  
  
 *hMenu*  
 Identifica el menú que va a usar la nueva ventana. Si una ventana secundaria, contiene el identificador entero.  
  
 *hwndParent*  
 Identifica la ventana que posee la ventana nueva. Este miembro es NULL si la nueva ventana es una ventana de nivel superior.  
  
 *CY*  
 Especifica el alto de la nueva ventana.  
  
 *CX*  
 Especifica el ancho de la nueva ventana.  
  
 *y*  
 Especifica la coordenada y de la esquina superior izquierda de la nueva ventana. Las coordenadas son relativas a la ventana principal si la nueva ventana es una ventana secundaria; en caso contrario, las coordenadas son en relación con el origen de la pantalla.  
  
 *x*  
 Especifica la coordenada x de la esquina superior izquierda de la nueva ventana. Las coordenadas son relativas a la ventana principal si la nueva ventana es una ventana secundaria; en caso contrario, las coordenadas son en relación con el origen de la pantalla.  
  
 *Estilo*  
 Especifica la nueva ventana [estilo](../../mfc/reference/styles-used-by-mfc.md).  
  
 *lpszName*  
 Apunta a una cadena terminada en null que especifica el nombre de la ventana nueva.  
  
 *lpszClass*  
 Señala a una cadena terminada en null que especifica el nombre de la ventana nueva de la clase de Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura; para obtener más información, consulte el SDK de Windows).  
  
 *dwExStyle*  
 Especifica el [estilo extendido](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) para la nueva ventana.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


