---
title: "CREATESTRUCT (Estructura) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATESTRUCT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CREATESTRUCT (estructura)"
ms.assetid: 028c7b5e-4fdc-48da-a550-d3e4f9e6cc85
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# CREATESTRUCT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `CREATESTRUCT` define los parámetros de la inicialización pasados al procedimiento de ventana de una aplicación.  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `lpCreateParams`  
 Señala a los datos que se usarán para crear la ventana.  
  
 `hInstance`  
 Identifica el identificador de la módulo\- instancia de módulo que posee la nueva ventana.  
  
 `hMenu`  
 Identifica el menú que se usará en la nueva ventana.  Si una ventana secundaria, contiene el identificador entero  
  
 `hwndParent`  
 Identifica la ventana que posee la nueva ventana.  Este miembro es **nulo** si la nueva ventana es una ventana de nivel superior.  
  
 `cy`  
 Especifica el alto de la nueva ventana.  
  
 `cx`  
 Especifica el ancho de la nueva ventana.  
  
 `y`  
 Especifica la y\-coordenada de la esquina superior izquierda de la nueva ventana.  Las coordenadas son relativas a la ventana primaria si la nueva ventana es una ventana secundaria; si no las coordenadas son relativas al origen de la pantalla.  
  
 `x`  
 Especifica la x\-coordenada de la esquina superior izquierda de la nueva ventana.  Las coordenadas son relativas a la ventana primaria si la nueva ventana es una ventana secundaria; si no las coordenadas son relativas al origen de la pantalla.  
  
 `style`  
 Especifica [estilo](../../mfc/reference/styles-used-by-mfc.md)de la nueva ventana.  
  
 `lpszName`  
 Señala una cadena terminada en null que especifica el nombre de la nueva ventana.  
  
 `lpszClass`  
 Señala una cadena terminada en null que especifica el nombre de clase de Windows de la nueva ventana \(una estructura de [Clase WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) ; para obtener más información, vea [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]\).  
  
 `dwExStyle`  
 Especifica [estilo extendido](../../mfc/reference/extended-window-styles.md) para la nueva ventana.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnCreate](../Topic/CWnd::OnCreate.md)