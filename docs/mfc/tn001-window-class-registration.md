---
title: "TN001: Registro de clases de ventana | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.registration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxRegisterClass (función)"
  - "TN001"
  - "WNDCLASS"
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN001: Registro de clases de ventana
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta nota describe las rutinas de MFC que registran [Clase WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)especial es necesario por Microsoft Windows.  Los atributos específicos de `WNDCLASS` utilizados por MFC y Windows se tratan.  
  
## El problema  
 Los atributos de un objeto de [CWnd](../mfc/reference/cwnd-class.md) , como un identificador de `HWND` en Windows, se almacenan en dos lugares: el objeto de la ventana y `WNDCLASS`.  El nombre de `WNDCLASS` se pasa a las funciones generales de la creación de la ventana como [CWnd::Create](../Topic/CWnd::Create.md) y [CFrameWnd::Create](../Topic/CFrameWnd::Create.md) en el parámetro de `lpszClassName` .  
  
 Este `WNDCLASS` se debe registrar con uno de cuatro significa:  
  
-   Implícitamente mediante MFC proporcionada `WNDCLASS`.  
  
-   Implícitamente haciendo subclases un control de Windows \(o algún otro control\).  
  
-   Explícitamente llamando a MFC [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md) o [AfxRegisterClass](../Topic/AfxRegisterClass.md).  
  
-   Llamando explícitamente a la rutina [RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586)de Windows.  
  
## Campos de clase WNDCLASS  
 La estructura de `WNDCLASS` consta de varios campos que describen una clase de ventana.  La tabla siguiente se muestran los campos y especificar cómo se utilizan en una aplicación MFC:  
  
|Campo|Descripción|  
|-----------|-----------------|  
|`lpfnWndProc`|el procedimiento de ventana, debe ser `AfxWndProc`|  
|`cbClsExtra`|no utilizado \(debe ser cero\)|  
|`cbWndExtra`|no utilizado \(debe ser cero\)|  
|`hInstance`|rellenado automáticamente con [AfxGetInstanceHandle](../Topic/AfxGetInstanceHandle.md)|  
|`hIcon`|el icono de las ventanas de marco, vea abajo|  
|`hCursor`|el cursor para cuando el mouse está sobre la ventana, vea abajo|  
|`hbrBackground`|el color de fondo, vea abajo|  
|`lpszMenuName`|no utilizado \(debe ser NULL\)|  
|`lpszClassName`|el nombre de clase, vea abajo|  
  
## WNDCLASSes proporcionado  
 Versiones anteriores de MFC \(antes de MFC 4,0\), siempre que varias clases de ventana predefinidas.  Estas clases de ventana se ya no proporcionan de forma predeterminada.  Las aplicaciones deben utilizar `AfxRegisterWndClass` con los parámetros adecuados.  
  
 Si la aplicación proporciona un recurso con el Id. de recurso especificado \(por ejemplo, AFX\_IDI\_STD\_FRAME\), MFC utilizará ese recurso.  Si no utilizará el recurso predeterminado.  Para el icono, se utiliza el icono de aplicación estándar, y para el cursor, se utiliza la flecha estándar el cursor.  
  
 Dos iconos admiten las aplicaciones MDI con los únicos tipos de documento: un icono de la aplicación principal, el otro icono del documento y las ventanas icónicos de MDIChild.  Para los tipos de documento varias con iconos diferentes, debe registrar `WNDCLASS`adicional es o utilizar la función de [CFrameWnd::LoadFrame](../Topic/CFrameWnd::LoadFrame.md) .  
  
 `CFrameWnd::LoadFrame` registrará `WNDCLASS` utilizando el identificador del icono que se especifica como primer parámetro y los atributos estándar siguientes:  
  
-   estilos de clase: CS\_DBLCLKS &#124; CS\_HREDRAW &#124; CS\_VREDRAW;  
  
-   icono AFX\_IDI\_STD\_FRAME  
  
-   flecha cursor  
  
-   Color de fondo de COLOR\_WINDOW  
  
 Los valores para el color de fondo y el cursor para [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) no se utilizan como el área cliente de `CMDIFrameWnd` es cubierta completamente por la ventana de **MDICLIENT** .  Microsoft no anima crear subclases de la ventana de **MDICLIENT** de modo que utilice colores estándar y los tipos de cursor cuando sea posible.  
  
## Crear subclases y creando superclases Controles  
 Si crea subclases o convierte en superclase un control de Windows \(por ejemplo, [CButton](../mfc/reference/cbutton-class.md)\) y la clase obtiene automáticamente los atributos de `WNDCLASS` proporcionados en la implementación de Windows de ese control.  
  
## La función de Clase  
 MFC proporciona una función auxiliar para registrar una clase de ventana.  Dado un conjunto de atributos \(estilos de clase de ventana, el cursor, pincel de fondo, e icono\), se genera un nombre sintetizado, y se registra la clase de ventana resultante.  Por ejemplo,  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle, HCURSOR hCursor, HBRUSH hbrBackground, HICON hIcon);  
```  
  
 Esta función devuelve una cadena temporal del nombre de clase de ventana registrado generado.  Para obtener más información sobre esta función, vea [AfxRegisterWndClass](../Topic/AfxRegisterWndClass.md).  
  
 La cadena devuelta es un puntero temporal en un búfer de cadena estático.  Es válida hasta la siguiente llamada a `AfxRegisterWndClass`.  Si desea conservar esta cadena sobre, almacenarlos en una variable de [CString](../atl-mfc-shared/using-cstring.md) , como en este ejemplo:  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);  
...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);  
...  
```  
  
 `AfxRegisterWndClass` producirá [CResourceException](../mfc/reference/cresourceexception-class.md) si la clase de ventana no podría para registrar \(debido a parámetros incorrectos, o fuera de memoria de Windows\).  
  
## Las funciones de RegisterClass y de AfxRegisterClass  
 Si desea hacer algo compleja que `AfxRegisterWndClass` proporciona, puede llamar a la API de Windows `RegisterClass` o la función `AfxRegisterClass`MFC.  `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) y las funciones de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)`Create` toman un nombre de cadena de `lpszClassName` para la clase de ventana como primer parámetro.  Puede utilizar cualquier nombre de clase de ventana registrado, independientemente del método que lo registrando.  
  
 Es importante utilizar `AfxRegisterClass` \(o `AfxRegisterWndClass`\) en un archivo DLL en Win32.  Win32 no automáticamente las clases de registro registradas por el archivo DLL, por lo que debe explícitamente las clases del registro cuando finaliza el archivo DLL.  Mediante `AfxRegisterClass` en lugar de `RegisterClass` esto se administra automáticamente para usted.  `AfxRegisterClass` mantiene una lista de clases únicas registradas por el archivo DLL y automáticamente con ellos cuando DLL finaliza.  Cuando se utiliza `RegisterClass` en un archivo DLL, deberá asegurarse de que todas las clases no son registradas cuando finaliza DLL \(en función de [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) \).  Error al realizar esta podría hacer `RegisterClass` para producir un error inesperado mientras otra aplicación cliente intenta utilizar el archivo DLL.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)