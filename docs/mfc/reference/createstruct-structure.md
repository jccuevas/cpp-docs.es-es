---
title: CREATESTRUCT (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: e51aed1eb7f74c721a5a4da092f205a2492ba5f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
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
 `lpCreateParams`  
 Puntos de datos que se utilizarán para crear la ventana.  
  
 `hInstance`  
 Identifica el identificador de instancia del módulo del módulo al que pertenece la nueva ventana.  
  
 `hMenu`  
 Identifica el menú que va a usar la nueva ventana. Si una ventana secundaria, contiene el identificador entero.  
  
 `hwndParent`  
 Identifica la ventana que posee la nueva ventana. Este miembro es **NULL** si la nueva ventana es una ventana de nivel superior.  
  
 `cy`  
 Especifica el alto de la nueva ventana.  
  
 `cx`  
 Especifica el ancho de la nueva ventana.  
  
 `y`  
 Especifica la coordenada y de la esquina superior izquierda de la nueva ventana. Coordenadas son relativas a la ventana primaria si la nueva ventana es una ventana secundaria; en caso contrario, las coordenadas son con respecto al origen de la pantalla.  
  
 `x`  
 Especifica la coordenada x de la esquina superior izquierda de la nueva ventana. Coordenadas son relativas a la ventana primaria si la nueva ventana es una ventana secundaria; en caso contrario, las coordenadas son con respecto al origen de la pantalla.  
  
 `style`  
 Especifica la nueva ventana [estilo](../../mfc/reference/styles-used-by-mfc.md).  
  
 `lpszName`  
 Apunta a una cadena terminada en null que especifica el nombre de la ventana nueva.  
  
 `lpszClass`  
 Señala a una cadena terminada en null que especifica el nombre de clase de Windows de la nueva ventana (una [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura; para obtener más información, consulte el SDK de Windows).  
  
 `dwExStyle`  
 Especifica la [estilo extendido](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) de la nueva ventana.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)


