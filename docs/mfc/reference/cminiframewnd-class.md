---
title: Clase CMiniFrameWnd | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMiniFrameWnd
dev_langs:
- C++
helpviewer_keywords:
- CMiniFrameWnd class
- mini-frame windows
- toolbars [C++]
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
caps.latest.revision: 21
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
ms.openlocfilehash: 1229f5405c9eeb90abcdc54108ed26e28d94f0e0
ms.lasthandoff: 02/24/2017

---
# <a name="cminiframewnd-class"></a>Clase CMiniFrameWnd
Representa una ventana de marco de altura media, como las que se suelen ver alrededor de las barras de herramientas flotantes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Construye un objeto `CMiniFrameWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMiniFrameWnd::Create](#create)|Crea un `CMiniFrameWnd` objeto después de la construcción.|  
|[CMiniFrameWnd::CreateEx](#createex)|Crea un `CMiniFrameWnd` objeto (con opciones adicionales) después de la construcción.|  
  
## <a name="remarks"></a>Comentarios  
 Estas ventanas de marco reducido se comportan como ventanas de marco normal, excepto que no tiene los botones Minimizar/Maximizar o menús y basta con hacer clic en el menú de sistema para descartar en ellos.  
  
 Para usar un `CMiniFrameWnd` de objeto, defina primero el objeto. A continuación, llame a la [crear](#create) función miembro para mostrar la ventana de marco reducido.  
  
 Para obtener más información sobre cómo usar `CMiniFrameWnd` los objetos, vea el artículo [acoplar y desacoplar barras de herramientas](../../mfc/docking-and-floating-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="a-namecminiframewnda--cminiframewndcminiframewnd"></a><a name="cminiframewnd"></a>CMiniFrameWnd::CMiniFrameWnd  
 Construye un `CMiniFrameWnd` el objeto, pero no crea la ventana.  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Para crear la ventana, llame a [CMiniFrameWnd::Create](#create).  
  
##  <a name="a-namecreatea--cminiframewndcreate"></a><a name="create"></a>CMiniFrameWnd::Create  
 Crea la ventana de marco reducido de Windows y lo adjunta a la `CMiniFrameWnd` objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpClassName`  
 Apunta a una cadena de caracteres terminada en null que los nombres de la clase de Windows. El nombre de clase puede ser cualquier nombre registrado con global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) (función). Si **NULL**, la clase de ventana se registrará automáticamente por el marco de trabajo. MFC proporciona la clase predeterminada de los estilos y atributos siguientes:  
  
-   Conjuntos de bits de estilo **CS_DBLCLKS**, que envía haga doble clic en los mensajes para el procedimiento de ventana cuando el usuario hace doble clic del mouse.  
  
-   Conjuntos de bits de estilo **CS_HREDRAW** y **CS_VREDRAW**, que dirigir el contenido del área de cliente se vuelva a dibujar cuando la ventana cambia de tamaño.  
  
-   Establece el cursor de clase en el estándar de Windows **IDC_ARROW**.  
  
-   Establece el pincel de fondo de la clase **NULL**, por lo que la ventana no se borrará el fondo.  
  
-   Establece el icono de clase en el icono del logotipo de Windows estándar, marca mover.  
  
-   Establece la ventana de tamaño y posición, como se indica en Windows.  
  
 `lpWindowName`  
 Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.  
  
 `dwStyle`  
 Especifica los atributos de estilo de ventana. Estos pueden incluir los estilos de ventana estándar y uno o varios de los siguientes estilos especiales:  
  
- **MFS_MOVEFRAME** permite mover haciendo clic en cualquiera de los bordes de la ventana, no sólo el título en la ventana de marco reducido.  
  
- **MFS_4THICKFRAME** deshabilita el cambio de tamaño de la ventana de marco reducido.  
  
- **MFS_SYNCACTIVE** sincroniza la activación de la ventana de marco reducido para la activación de su ventana primaria.  
  
- **MFS_THICKFRAME** permite que la ventana de marco reducido, deben preverse tan pequeños como permitir que el contenido del área de cliente.  
  
- **MFS_BLOCKSYSMENU** deshabilita el acceso al menú de sistema y el menú de control y los convierte en parte de la leyenda (barra de título).  
  
 Consulte [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los valores de estilo de ventana posible. Es la combinación típica que se utiliza para las ventanas de marco reducido **WS_POPUP | WS_CAPTION | WS_SYSMENU**.  
  
 `rect`  
 Un `RECT` estructura que especifica las dimensiones deseadas de la ventana.  
  
 `pParentWnd`  
 Apunta a la ventana primaria. Utilice **NULL** para ventanas de nivel superior.  
  
 `nID`  
 Si la ventana de marco reducido se crea como una ventana secundaria, este es el identificador del control secundario; en caso contrario, 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 **Crear** inicializa el nombre de clase y el nombre de la ventana de la ventana y registra los valores predeterminados para su estilo y el elemento primario.  
  
##  <a name="a-namecreateexa--cminiframewndcreateex"></a><a name="createex"></a>CMiniFrameWnd::CreateEx  
 Crea un objeto `CMiniFrameWnd`.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    LPCTSTR lpClassName,  
    LPCTSTR lpWindowName,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd = NULL,  
    UINT nID = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido de la `CMiniFrameWnd` va a crear. Aplicar cualquiera de los [estilos de ventana extendidos](../../mfc/reference/extended-window-styles.md) a la ventana.  
  
 `lpClassName`  
 Apunta a una cadena de caracteres terminada en null que los nombres de la clase Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura). El nombre de clase puede ser cualquier nombre registrado con global [AfxRegisterWndClass](http://msdn.microsoft.com/library/62c7d4b1-7a29-4abb-86f7-dec541659db0) función o cualquiera de los nombres de clase de control predefinidos. No debe ser **NULL**.  
  
 `lpWindowName`  
 Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.  
  
 `dwStyle`  
 Especifica los atributos de estilo de ventana. Consulte [estilos de ventana](../../mfc/reference/window-styles.md) y [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los valores posibles.  
  
 `rect`  
 El tamaño y posición de la ventana, en coordenadas de cliente `pParentWnd`.  
  
 `pParentWnd`  
 Señala al objeto de ventana primaria.  
  
 `nID`  
 El identificador de la ventana secundaria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El `CreateEx` los parámetros especifican el **WNDCLASS**, estilo de ventana y posición inicial (opcionalmente) y el tamaño de la ventana. `CreateEx`También especifica la ventana primaria (si existe) e Id.  
  
 Cuando `CreateEx` se ejecuta, Windows envía la [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) mensajes en la ventana.  
  
 Para extender el control de mensajes de forma predeterminada, derive una clase de `CMiniFrameWnd`, agregar un mapa de mensajes a la nueva clase y proporcionan funciones miembro para los mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.  
  
 Reemplazar más **en***mensaje* controladores para agregar más funcionalidad a la clase derivada de mensaje.  
  
 Si el **WS_VISIBLE** estilo se proporciona, Windows envía todos los mensajes que se requiere para activar y mostrar la ventana de la ventana. Si el estilo de ventana especifica una barra de título, el título de ventana que apunta el `lpszWindowName` parámetro se muestra en la barra de título.  
  
 El `dwStyle` parámetro puede ser cualquier combinación de [estilos de ventana](../../mfc/reference/window-styles.md).  
  
 Ya no se admiten las ventanas de herramientas de paleta de estilo antiguas. Se admite el estilo anterior, que no tenía un botón de cierre de "X", cuando se ejecuta una aplicación MFC en versiones anteriores de Windows, pero ya no se admite en Visual C++. NET. Sólo la nueva `WS_EX_TOOLWINDOW` estilo ahora se admite; para obtener una descripción de este estilo, consulte [estilos de ventana extendidos](../../mfc/reference/extended-window-styles.md).  
  
## <a name="see-also"></a>Vea también  
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)

