---
title: 'TN001: Registro de la clase de ventana | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.registration
dev_langs:
- C++
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 245ffcb66223813c7146c50c964cd97203ed8d53
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383859"
---
# <a name="tn001-window-class-registration"></a>TN001: Registro de clases de ventana
Esta nota describe las rutinas MFC que registrar especial [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576)es necesarios para Microsoft Windows. Específica `WNDCLASS` se describen los atributos utilizados por MFC y Windows.  
  
## <a name="the-problem"></a>El problema  
 Los atributos de un [CWnd](../mfc/reference/cwnd-class.md) objeto, como un `HWND` controlar en Windows, se almacenan en dos lugares: el objeto de ventana y el `WNDCLASS`. El nombre de la `WNDCLASS` se pasa a funciones de creación de ventana general como [CWnd:: Create](../mfc/reference/cwnd-class.md#create) y [CFrameWnd::Create](../mfc/reference/cframewnd-class.md#create) en el `lpszClassName` parámetro.  
  
 Esto `WNDCLASS` debe registrarse a través de uno de cuatro significa:  
  
-   Implícitamente mediante una MFC proporcionan `WNDCLASS`.  
  
-   Implícitamente mediante la creación de subclases de un control de Windows (o algún otro control).  
  
-   Explícitamente mediante una llamada a la MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) o [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
-   Explícitamente mediante una llamada a la rutina de Windows [RegisterClass](http://msdn.microsoft.com/library/windows/desktop/ms633586).  
  
## <a name="wndclass-fields"></a>Campos WNDCLASS  
 El `WNDCLASS` estructura consta de varios campos que describen una clase de ventana. En la siguiente tabla muestra los campos y especifica cómo se utilizan en una aplicación MFC:  
  
|Campo|Descripción|  
|-----------|-----------------|  
|`lpfnWndProc`|procedimiento de ventana, debe ser un `AfxWndProc`|  
|`cbClsExtra`|no usa (debe ser cero)|  
|`cbWndExtra`|no usa (debe ser cero)|  
|`hInstance`|rellena automáticamente con [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle)|  
|`hIcon`|icono de ventanas de marco, vea a continuación|  
|`hCursor`|cursor para cuando el mouse está sobre la ventana, vea a continuación|  
|`hbrBackground`|color de fondo, consulte el siguiente|  
|`lpszMenuName`|no usa (debe ser NULL)|  
|`lpszClassName`|nombre de clase, vea a continuación|  
  
## <a name="provided-wndclasses"></a>Proporciona WNDCLASSes  
 Versiones anteriores de MFC (antes de MFC 4.0), proporcionadas varias clases de ventana predefinidas. Estas clases de ventana ya no se proporcionan de forma predeterminada. Las aplicaciones deben utilizar `AfxRegisterWndClass` con los parámetros adecuados.  
  
 Si la aplicación proporciona un recurso con el identificador de recurso especificado (por ejemplo, AFX_IDI_STD_FRAME), MFC utilizará ese recurso. En caso contrario, utilizará el recurso predeterminado. Para el icono, se utilizará el icono de aplicación estándar y para el cursor, se utiliza el cursor de flecha estándar.  
  
 Dos iconos de admiten aplicaciones de MDI con tipos de documento único: un icono de la aplicación principal, el otro icono para el icono de documento/MDIChild windows. Para varios tipos de documentos con iconos diferentes, debe registrar adicionales `WNDCLASS`es o use la [CFrameWnd::LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) (función).  
  
 `CFrameWnd::LoadFrame` se registrará un `WNDCLASS` con el Id. del icono puede especificar como el primer parámetro y los atributos estándares siguientes:  
  
-   estilo de clase: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;  
  
-   icono AFX_IDI_STD_FRAME  
  
-   cursor de flecha  
  
-   Color de fondo COLOR_WINDOW  
  
 Los valores de color de fondo y de cursor para la [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) no se usan desde el área de cliente de la `CMDIFrameWnd` está cubierta completamente por la **MDICLIENT** ventana. Microsoft no recomienda subclases el **MDICLIENT** ventana por lo que usar los colores estándar y los tipos de cursor siempre que sea posible.  
  
## <a name="subclassing-and-superclassing-controls"></a>Controles de creación de superclases y subclases  
 Si deriva una subclase o superclase una ventana de control (por ejemplo, [CButton](../mfc/reference/cbutton-class.md)), a continuación, la clase obtiene automáticamente la `WNDCLASS` atributos que se proporcionan en la implementación de Windows de ese control.  
  
## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass (función)  
 MFC proporciona una función auxiliar para registrar una clase de ventana. Dado un conjunto de atributos (estilo de clase de ventana, cursor, pincel de fondo e icono), se genera un nombre sintético, y se registra la clase de ventana resultante. Por ejemplo,  
  
```  
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```  
  
 Esta función devuelve una cadena temporal con el nombre de clase de ventana registrados generada. Para obtener más información acerca de esta función, consulte [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass).  
  
 La cadena devuelta es un puntero a un búfer de cadena estática temporal. Es válido hasta la siguiente llamada a `AfxRegisterWndClass`. Si desea mantener esta cadena alrededor, almacenarla en un [CString](../atl-mfc-shared/using-cstring.md) variable, como en este ejemplo:  
  
```  
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...  
CWnd* pWnd = new CWnd;  
pWnd->Create(strWndClass, ...);

...  
```  
  
 `AfxRegisterWndClass` se producirá un [CResourceException](../mfc/reference/cresourceexception-class.md) si la clase de ventana no se pudo registrar (debido a parámetros incorrectos, o fuera de la memoria de Windows).  
  
## <a name="the-registerclass-and-afxregisterclass-functions"></a>Las funciones de AfxRegisterClass y RegisterClass  
 Si desea hacer algo más sofisticado a lo que `AfxRegisterWndClass` proporciona, se puede llamar a la API de Windows `RegisterClass` o la función MFC `AfxRegisterClass`. El `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) y [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` funciones toman un `lpszClassName` nombre de cadena para la clase de ventana como primer parámetro. Puede utilizar cualquier nombre de clase de ventana registrados, independientemente del método usado para registrarla.  
  
 Es importante que use `AfxRegisterClass` (o `AfxRegisterWndClass`) en un archivo DLL de Win32. Win32 no automáticamente anular el registro de clases registradas por un archivo DLL, por lo que explícitamente debe anular el registro clases cuando finaliza el archivo DLL. Mediante el uso de `AfxRegisterClass` en lugar de `RegisterClass` se controla automáticamente para usted. `AfxRegisterClass` mantiene una lista de las clases únicas registrados por el archivo DLL y eliminará automáticamente del registro ellos cuando finaliza el archivo DLL. Cuando usas `RegisterClass` en un archivo DLL, debe asegurarse de que todas las clases se eliminan del registradas cuando finaliza el archivo DLL (en su [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583) función). Si no lo hace podría provocar `RegisterClass` a producir errores inesperados cuando otra aplicación cliente intenta usar el archivo DLL.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

