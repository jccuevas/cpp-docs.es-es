---
title: CREATESTRUCT (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CREATESTRUCT
dev_langs:
- C++
helpviewer_keywords:
- CREATESTRUCT structure
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: 14
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
ms.openlocfilehash: ec72d4725cb7e5959369b24a6ff7f0e3e9da1ca7
ms.lasthandoff: 02/24/2017

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
 Puntos de datos que se usará para crear la ventana.  
  
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
 Especifica la coordenada y de la esquina superior izquierda de la nueva ventana. Coordenadas son relativas a la ventana principal si la nueva ventana es una ventana secundaria; de lo contrario coordenadas son en relación con el origen de la pantalla.  
  
 `x`  
 Especifica la coordenada x de la esquina superior izquierda de la nueva ventana. Coordenadas son relativas a la ventana principal si la nueva ventana es una ventana secundaria; de lo contrario coordenadas son en relación con el origen de la pantalla.  
  
 `style`  
 Especifica la nueva ventana [estilo](../../mfc/reference/styles-used-by-mfc.md).  
  
 `lpszName`  
 Apunta a una cadena terminada en null que especifica el nombre de la nueva ventana.  
  
 `lpszClass`  
 Señala a una cadena terminada en null que especifica el nombre de clase de Windows de la nueva ventana (una [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura; para obtener más información, consulte la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]).  
  
 `dwExStyle`  
 Especifica la [estilo extendido](../../mfc/reference/extended-window-styles.md) de la nueva ventana.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** winuser.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate)



