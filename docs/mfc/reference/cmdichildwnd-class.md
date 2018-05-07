---
title: CMDIChildWnd (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMDIChildWnd
- AFXWIN/CMDIChildWnd
- AFXWIN/CMDIChildWnd::CMDIChildWnd
- AFXWIN/CMDIChildWnd::Create
- AFXWIN/CMDIChildWnd::GetMDIFrame
- AFXWIN/CMDIChildWnd::MDIActivate
- AFXWIN/CMDIChildWnd::MDIDestroy
- AFXWIN/CMDIChildWnd::MDIMaximize
- AFXWIN/CMDIChildWnd::MDIRestore
- AFXWIN/CMDIChildWnd::SetHandles
dev_langs:
- C++
helpviewer_keywords:
- CMDIChildWnd [MFC], CMDIChildWnd
- CMDIChildWnd [MFC], Create
- CMDIChildWnd [MFC], GetMDIFrame
- CMDIChildWnd [MFC], MDIActivate
- CMDIChildWnd [MFC], MDIDestroy
- CMDIChildWnd [MFC], MDIMaximize
- CMDIChildWnd [MFC], MDIRestore
- CMDIChildWnd [MFC], SetHandles
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e27551c04be5d6e985c6e7829f11f94d0aafeba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd (clase)
Proporciona la funcionalidad de una ventana secundaria de la interfaz de múltiples documentos (MDI) de Windows, junto con los miembros para administrar la ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Construye un objeto `CMDIChildWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMDIChildWnd::Create](#create)|Crea la ventana secundaria de MDI de Windows asociada a la `CMDIChildWnd` objeto.|  
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Devuelve al elemento primario de marco MDI de la ventana de cliente MDI.|  
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Activa esta ventana secundaria MDI.|  
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Destruye esta ventana secundaria MDI.|  
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximiza esta ventana secundaria MDI.|  
|[CMDIChildWnd::MDIRestore](#mdirestore)|Restaura esta ventana secundaria MDI de tamaño minimizado o maximizado.|  
|[CMDIChildWnd::SetHandles](#sethandles)|Establece los identificadores de recursos de menú y aceleradores.|  
  
## <a name="remarks"></a>Comentarios  
 Una ventana secundaria MDI se parece mucho a una ventana marco típica, salvo que la ventana secundaria MDI aparece dentro de una ventana de marco MDI en lugar de en el escritorio. Una ventana secundaria MDI no tiene una barra de menús de su propia, pero en su lugar, comparte el menú de la ventana de marco MDI. El marco de trabajo cambia automáticamente el menú de marco MDI para representar la ventana secundaria MDI activa actualmente.  
  
 Para crear una ventana secundaria MDI útil para la aplicación, derive una clase de `CMDIChildWnd`. Agregue variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.  
  
 Hay tres formas de crear una ventana secundaria MDI:  
  
-   Crear directamente mediante **crear**.  
  
-   Crear directamente mediante `LoadFrame`.  
  
-   Crearlo indirectamente a través de una plantilla de documento.  
  
 Antes de llamar a **crear** o `LoadFrame`, debe crear el objeto de ventana de marco en el montón mediante C++ **nueva** operador. Antes de llamar a **crear** también se puede registrar una clase de ventana con la [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.  
  
 Use la **crear** función miembro para pasar parámetros de creación del marco inmediatas como argumentos.  
  
 `LoadFrame` requiere menos argumentos que **crear**y en su lugar recupera la mayoría de sus valores predeterminados de recursos, incluidos el título del marco, icono, tabla de aceleradores y menús. Para ser accesibles para `LoadFrame`, todos estos recursos deben tener el mismo identificador de recurso (por ejemplo, **IDR_MAINFRAME**).  
  
 Cuando un `CMDIChildWnd` objeto contiene documentos y vistas, se crean indirectamente mediante el marco de trabajo en lugar de directamente por el programador. La `CDocTemplate` objeto Orquesta la creación del marco, la creación de las vistas que lo contiene y la conexión de las vistas al documento adecuado. Los parámetros de la `CDocTemplate` constructor especifica la `CRuntimeClass` de estas tres clases implicadas (documento, marco y ver). Un `CRuntimeClass` objeto se usa el marco de trabajo para crear de forma dinámica nuevos marcos al especificado por el usuario (por ejemplo, mediante el comando archivo nuevo o el comando MDI ventana nueva).  
  
 Deriva una clase de ventana de marco `CMDIChildWnd` deben declararse con `DECLARE_DYNCREATE` en orden para los sistemas anteriores `RUNTIME_CLASS` mecanismo funcione correctamente.  
  
 El `CMDIChildWnd` clase hereda gran parte de su implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte la [CFrameWnd](../../mfc/reference/cframewnd-class.md) descripción de la clase. La `CMDIChildWnd` clase tiene las siguientes características adicionales:  
  
-   Junto con el `CMultiDocTemplate` (clase), varios `CMDIChildWnd` objetos desde la misma plantilla de documento comparten el mismo menú, guardar los recursos del sistema de Windows.  
  
-   El menú de ventana de elemento secundario MDI activo actualmente reemplaza completamente el menú de la ventana de marco MDI y se agrega el título de la ventana secundaria MDI activo actualmente al título de la ventana de marco MDI. Para obtener más ejemplos de funciones de ventana secundaria MDI que se implementan junto con una ventana de marco MDI, consulte el `CMDIFrameWnd` descripción de la clase.  
  
 No use C++ **eliminar** operador para destruir una ventana de marco. Utilice `CWnd::DestroyWindow` en su lugar. El `CFrameWnd` implementación de `PostNcDestroy` eliminará el objeto de C++ cuando se destruye la ventana. Cuando el usuario cierra la ventana de marco, el valor predeterminado `OnClose` controlador llamará `DestroyWindow`.  
  
 Para obtener más información sobre `CMDIChildWnd`, consulte [ventanas de marco](../../mfc/frame-windows.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMDIChildWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cmdichildwnd"></a>  CMDIChildWnd::CMDIChildWnd  
 Llamada a construir un `CMDIChildWnd` objeto.  
  
```  
CMDIChildWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a **crear** para crear la ventana visible.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMDIChildWnd::Create](#create).  
  
##  <a name="create"></a>  CMDIChildWnd::Create  
 Llame a esta función miembro para crear una ventana secundaria MDI de Windows y adjuntarlo a la `CMDIChildWnd` objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszClassName,  
    LPCTSTR lpszWindowName,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_OVERLAPPEDWINDOW,  
    const RECT& rect = rectDefault,  
    CMDIFrameWnd* pParentWnd = NULL,  
    CCreateContext* pContext = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszClassName`  
 Apunta a una cadena de caracteres terminada en null que designa la clase de Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura). El nombre de clase puede ser cualquier nombre registrado con el [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global. Debe ser **NULL** para un estándar `CMDIChildWnd`.  
  
 `lpszWindowName`  
 Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se utiliza como texto de la barra de título.  
  
 `dwStyle`  
 Especifica la ventana [estilo](../../mfc/reference/styles-used-by-mfc.md#window-styles) atributos. El **WS_CHILD** estilo es necesario.  
  
 `rect`  
 Contiene el tamaño y la posición de la ventana. El `rectDefault` valor permite a Windows especificar el tamaño y la posición del nuevo `CMDIChildWnd`.  
  
 `pParentWnd`  
 Especifica el elemento primario de la ventana. Si **NULL**, se utiliza la ventana de la aplicación principal.  
  
 `pContext`  
 Especifica un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La ventana de marco de secundario MDI activa actualmente puede determinar el título de la ventana de marco principal. Esta característica está deshabilitada si se desactiva la **FWS_ADDTOTITLE** bit de estilo de la ventana de marco secundarias.  
  
 El marco de trabajo llama a esta función miembro en respuesta a un comando de usuario para crear una ventana secundaria, y el marco de trabajo usa el `pContext` parámetro para conectarse correctamente la ventana secundaria a la aplicación. Cuando se llama a **crear**, `pContext` puede ser **NULL**.  
  
### <a name="example"></a>Ejemplo  
 Ejemplo 1:  
  
 [!code-cpp[NVC_MFCWindowing#7](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]  
  
### <a name="example"></a>Ejemplo  
 Ejemplo 2:  
  
 [!code-cpp[NVC_MFCWindowing#8](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing#9](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]  
  
##  <a name="getmdiframe"></a>  CMDIChildWnd::GetMDIFrame  
 Llame a esta función para devolver el marco MDI primario.  
  
```  
CMDIFrameWnd* GetMDIFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana de marco principal MDI.  
  
### <a name="remarks"></a>Comentarios  
 El marco devuelto es dos principales que se quitará el `CMDIChildWnd` y es el primario de la ventana de tipo **MDICLIENT** que administra el `CMDIChildWnd` objeto. Llame a la [GetParent](../../mfc/reference/cwnd-class.md#getparent) función de miembro para devolver el `CMDIChildWnd` inmediato del objeto **MDICLIENT** primario como un archivo temporal `CWnd` puntero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).  
  
##  <a name="mdiactivate"></a>  CMDIChildWnd::MDIActivate  
 Llame a esta función miembro para activar una ventana secundaria MDI independientemente de la ventana de marco MDI.  
  
```  
void MDIActivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el marco se activa, también se activará la ventana secundaria que se activó por última vez.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).  
  
##  <a name="mdidestroy"></a>  CMDIChildWnd::MDIDestroy  
 Llame a esta función miembro para destruir una ventana secundaria MDI.  
  
```  
void MDIDestroy();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro quita el título de la ventana secundaria de la ventana de marco y desactiva la ventana secundaria.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#10](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]  
  
##  <a name="mdimaximize"></a>  CMDIChildWnd::MDIMaximize  
 Llame a esta función miembro para maximizar una ventana secundaria MDI.  
  
```  
void MDIMaximize();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se maximiza una ventana secundaria, Windows lo modifica para realizar su área cliente rellenar el área de cliente de la ventana de marco. Windows coloca el menú ventana secundaria del Control de barra de menús del marco para que el usuario puede restaurar o cerrar la ventana secundaria y agrega el título de la ventana secundaria para el título de ventana de marco.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#11](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]  
  
##  <a name="mdirestore"></a>  CMDIChildWnd::MDIRestore  
 Llame a esta función miembro para restaurar una ventana secundaria MDI de tamaño minimizado o maximizado.  
  
```  
void MDIRestore();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing#12](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]  
  
##  <a name="sethandles"></a>  CMDIChildWnd::SetHandles  
 Establece los identificadores de recursos de menú y aceleradores.  
  
```  
void SetHandles(
    HMENU hMenu,  
    HACCEL hAccel);
```  
  
### <a name="parameters"></a>Parámetros  
 `hMenu`  
 El identificador de un recurso de menú.  
  
 `hAccel`  
 El identificador de un recurso de aceleradores.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para definir los recursos de menú y aceleradores utilizados por el objeto de ventana secundaria MDI.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDI de MFC](../../visual-cpp-samples.md)   
 [Ejemplo MFC MDIDOCVW](../../visual-cpp-samples.md)   
 [Ejemplo SNAPVW de MFC](../../visual-cpp-samples.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)
