---
title: CMDIChildWnd (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMDIChildWnd
dev_langs:
- C++
helpviewer_keywords:
- MDI [C++], child windows
- windows [C++], MDI
- CMDIChildWnd class
- child windows, CMDIChildWnd class
ms.assetid: 6d07f5d4-9a3e-4723-9fa5-e65bb669fdd5
caps.latest.revision: 22
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
ms.openlocfilehash: 240af1fe5f3afa4cdb7d4d585dc74cc4836799cc
ms.lasthandoff: 02/24/2017

---
# <a name="cmdichildwnd-class"></a>CMDIChildWnd (clase)
Proporciona la funcionalidad de una ventana secundaria de la interfaz de múltiples documentos (MDI) de Windows, junto con los miembros para administrar la ventana.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMDIChildWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDIChildWnd::CMDIChildWnd](#cmdichildwnd)|Construye un objeto `CMDIChildWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMDIChildWnd::Create](#create)|Crea la ventana secundaria de MDI de Windows asociada con el `CMDIChildWnd` objeto.|  
|[CMDIChildWnd::GetMDIFrame](#getmdiframe)|Devuelve al elemento primario de marco MDI de la ventana de cliente MDI.|  
|[CMDIChildWnd::MDIActivate](#mdiactivate)|Activa esta ventana secundaria MDI.|  
|[CMDIChildWnd::MDIDestroy](#mdidestroy)|Destruye esta ventana secundaria MDI.|  
|[CMDIChildWnd::MDIMaximize](#mdimaximize)|Maximiza esta ventana secundaria MDI.|  
|[CMDIChildWnd::MDIRestore](#mdirestore)|Restaura esta ventana secundaria MDI de tamaño maximizado o minimizado.|  
|[CMDIChildWnd::SetHandles](#sethandles)|Establece los identificadores de recursos de menú y aceleradores.|  
  
## <a name="remarks"></a>Comentarios  
 Una ventana secundaria MDI se parece mucho a una ventana marco típica, excepto en que la ventana secundaria MDI aparece dentro de una ventana de marco MDI en lugar de en el escritorio. Una ventana secundaria MDI no tiene una barra de menús propia, pero en su lugar, comparte el menú de la ventana de marco MDI. El marco de trabajo cambia automáticamente el menú de marco MDI para representar la ventana secundaria MDI activa actualmente.  
  
 Para crear una ventana secundaria MDI útil para su aplicación, derive una clase de `CMDIChildWnd`. Agregar variables miembro a la clase derivada para almacenar datos específicos de la aplicación. Implemente funciones miembro de controlador de mensajes y un mapa de mensajes en la clase derivada para especificar qué ocurre cuando los mensajes se dirigen a la ventana.  
  
 Hay tres formas de crear una ventana secundaria MDI:  
  
-   Crear directamente mediante **crear**.  
  
-   Crear directamente mediante `LoadFrame`.  
  
-   Construirla indirectamente a través de una plantilla de documento.  
  
 Antes de llamar a **crear** o `LoadFrame`, debe crear el objeto de ventana de marco en el montón mediante C++ **nuevo** operador. Antes de llamar a **crear** también se puede registrar una clase de ventana con el [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función global para establecer los estilos de icono y de clase para el marco.  
  
 Utilice la **crear** función miembro para pasar los parámetros de creación del marco inmediatas como argumentos.  
  
 `LoadFrame`requiere menos argumentos que **crear**y en su lugar recupera la mayor parte de sus valores predeterminados de recursos, como el título del marco, icono, tabla de aceleradores y menús. Para tener acceso a `LoadFrame`, todos estos recursos deben tener el mismo identificador de recursos (por ejemplo, **IDR_MAINFRAME**).  
  
 Cuando un `CMDIChildWnd` objeto contiene documentos y vistas, que se crean indirectamente mediante el marco de trabajo en lugar de directamente por el programador. La `CDocTemplate` objeto organiza la creación del marco, la creación de las vistas que contienen y la conexión de las vistas para el documento adecuado. Los parámetros de la `CDocTemplate` constructor especifica la `CRuntimeClass` de las tres clases implicadas (documento, marco y ver). Un `CRuntimeClass` objeto se utiliza el marco para crear dinámicamente nuevos marcos al especificado por el usuario (por ejemplo, mediante el comando nuevo archivo o el comando nuevo de ventana MDI).  
  
 Deriva una clase de ventana de marco `CMDIChildWnd` deben declararse con `DECLARE_DYNCREATE` en orden para los sistemas anteriores `RUNTIME_CLASS` mecanismo funcione correctamente.  
  
 El `CMDIChildWnd` clase hereda gran parte de la implementación predeterminada de `CFrameWnd`. Para obtener una lista detallada de estas características, consulte la [CFrameWnd](../../mfc/reference/cframewnd-class.md) descripción de clase. La `CMDIChildWnd` clase tiene las siguientes características adicionales:  
  
-   Junto con el `CMultiDocTemplate` (clase), varios `CMDIChildWnd` objetos desde la misma plantilla de documento comparten el mismo menú, ahorrando recursos de sistema de Windows.  
  
-   El menú de ventana de secundario MDI activo completamente reemplaza el menú de la ventana de marco MDI y el título de la ventana secundaria MDI activa actualmente se agrega al título de la ventana de marco MDI. Para obtener más ejemplos de funciones de ventana secundaria MDI que se implementan junto con una ventana de marco MDI, consulte el `CMDIFrameWnd` descripción de clase.  
  
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
  
##  <a name="a-namecmdichildwnda--cmdichildwndcmdichildwnd"></a><a name="cmdichildwnd"></a>CMDIChildWnd::CMDIChildWnd  
 Llamada a construir un `CMDIChildWnd` objeto.  
  
```  
CMDIChildWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a **crear** para crear la ventana visible.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMDIChildWnd::Create](#create).  
  
##  <a name="a-namecreatea--cmdichildwndcreate"></a><a name="create"></a>CMDIChildWnd::Create  
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
 Apunta a una cadena de caracteres terminada en null que los nombres de la clase Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura). El nombre de clase puede ser cualquier nombre registrado con el [AfxRegisterWndClass](http://msdn.microsoft.com/library/62c7d4b1-7a29-4abb-86f7-dec541659db0) función global. Debe ser **NULL** un estándar `CMDIChildWnd`.  
  
 `lpszWindowName`  
 Apunta a una cadena de caracteres terminada en null que representa el nombre de la ventana. Se utiliza como texto de la barra de título.  
  
 `dwStyle`  
 Especifica el período de [estilo](../../mfc/reference/window-styles.md) atributos. El **WS_CHILD** estilo es necesario.  
  
 `rect`  
 Contiene el tamaño y la posición de la ventana. El `rectDefault` valor permite a Windows especificar el tamaño y la posición del nuevo `CMDIChildWnd`.  
  
 `pParentWnd`  
 Especifica el elemento primario de la ventana. Si **NULL**, se utiliza la ventana principal de la aplicación.  
  
 `pContext`  
 Especifica un [CCreateContext](../../mfc/reference/ccreatecontext-structure.md) estructura. Este parámetro puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La ventana de marco de secundario MDI activa puede determinar el título de la ventana de marco principal. Esta característica está deshabilitada si se desactiva la **FWS_ADDTOTITLE** bit de estilo de la ventana de marco secundario.  
  
 El marco de trabajo llama a esta función miembro en respuesta a un comando de usuario para crear una ventana secundaria, y el marco de trabajo usa el `pContext` parámetro conectarse correctamente a la ventana secundaria a la aplicación. Cuando se llama a **crear**, `pContext` puede ser **NULL**.  
  
### <a name="example"></a>Ejemplo  
 Ejemplo 1:  
  
 [!code-cpp[NVC_MFCWindowing&#7;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_1.cpp)]  
  
### <a name="example"></a>Ejemplo  
 Ejemplo 2:  
  
 [!code-cpp[NVC_MFCWindowing Nº&8;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_2.cpp)]  
  
 [!code-cpp[NVC_MFCWindowing&#9;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_3.cpp)]  
  
##  <a name="a-namegetmdiframea--cmdichildwndgetmdiframe"></a><a name="getmdiframe"></a>CMDIChildWnd::GetMDIFrame  
 Llame a esta función para devolver el marco principal MDI.  
  
```  
CMDIFrameWnd* GetMDIFrame();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a la ventana de marco principal MDI.  
  
### <a name="remarks"></a>Comentarios  
 El marco devuelto es dos padres quitados la `CMDIChildWnd` y es el elemento primario de la ventana de tipo **MDICLIENT** que administra la `CMDIChildWnd` objeto. Llame a la [GetParent](../../mfc/reference/cwnd-class.md#getparent) función de miembro para devolver el `CMDIChildWnd` inmediato de objeto del **MDICLIENT** principal como un objeto temporal `CWnd` puntero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMDIFrameWnd::MDISetMenu](../../mfc/reference/cmdiframewnd-class.md#mdisetmenu).  
  
##  <a name="a-namemdiactivatea--cmdichildwndmdiactivate"></a><a name="mdiactivate"></a>CMDIChildWnd::MDIActivate  
 Llame a esta función miembro para activar una ventana secundaria MDI independientemente de la ventana de marco MDI.  
  
```  
void MDIActivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el marco se activa, también se activará la ventana secundaria que se activó por última vez.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMDIFrameWnd::GetWindowMenuPopup](../../mfc/reference/cmdiframewnd-class.md#getwindowmenupopup).  
  
##  <a name="a-namemdidestroya--cmdichildwndmdidestroy"></a><a name="mdidestroy"></a>CMDIChildWnd::MDIDestroy  
 Llame a esta función miembro para destruir una ventana secundaria MDI.  
  
```  
void MDIDestroy();
```  
  
### <a name="remarks"></a>Comentarios  
 La función miembro quita el título de la ventana secundaria de la ventana de marco y desactiva la ventana secundaria.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#10;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_4.cpp)]  
  
##  <a name="a-namemdimaximizea--cmdichildwndmdimaximize"></a><a name="mdimaximize"></a>CMDIChildWnd::MDIMaximize  
 Llame a esta función miembro para maximizar una ventana secundaria MDI.  
  
```  
void MDIMaximize();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando se maximiza una ventana secundaria, Windows lo modifica para hacer su área cliente rellenar el área de cliente de la ventana de marco. Windows coloca el menú ventana secundaria del Control en la barra de menús del marco para que el usuario puede restaurar o cerrar la ventana secundaria y agrega el título de la ventana secundaria en el título de ventana de marco.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#11;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_5.cpp)]  
  
##  <a name="a-namemdirestorea--cmdichildwndmdirestore"></a><a name="mdirestore"></a>CMDIChildWnd::MDIRestore  
 Llame a esta función miembro para restaurar una ventana secundaria MDI de tamaño maximizado o minimizado.  
  
```  
void MDIRestore();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCWindowing&#12;](../../mfc/reference/codesnippet/cpp/cmdichildwnd-class_6.cpp)]  
  
##  <a name="a-namesethandlesa--cmdichildwndsethandles"></a><a name="sethandles"></a>CMDIChildWnd::SetHandles  
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
 [Ejemplo MDIDOCVW de MFC](../../visual-cpp-samples.md)   
 [Ejemplo de MFC SNAPVW](../../visual-cpp-samples.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CMDIFrameWnd (clase)](../../mfc/reference/cmdiframewnd-class.md)

