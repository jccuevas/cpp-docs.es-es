---
title: CMiniFrameWnd (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMiniFrameWnd
- AFXWIN/CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::CMiniFrameWnd
- AFXWIN/CMiniFrameWnd::Create
- AFXWIN/CMiniFrameWnd::CreateEx
dev_langs:
- C++
helpviewer_keywords:
- CMiniFrameWnd [MFC], CMiniFrameWnd
- CMiniFrameWnd [MFC], Create
- CMiniFrameWnd [MFC], CreateEx
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e6abf906d9fa0e5866b28a0c617e68edead8378
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852255"
---
# <a name="cminiframewnd-class"></a>CMiniFrameWnd (clase)
Representa una ventana de marco de altura media, como las que se suelen ver alrededor de las barras de herramientas flotantes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMiniFrameWnd::CMiniFrameWnd](#cminiframewnd)|Construye un objeto `CMiniFrameWnd`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMiniFrameWnd::Create](#create)|Crea un `CMiniFrameWnd` objeto después de la construcción.|  
|[CMiniFrameWnd::CreateEx](#createex)|Crea un `CMiniFrameWnd` objeto (con opciones adicionales) después de la construcción.|  
  
## <a name="remarks"></a>Comentarios  
 Estas ventanas de marco reducido se comportan como ventanas de marco normal, excepto que no tiene los botones Minimizar y maximizar o los menús y basta con hacer clic en el menú del sistema para descartarlas.  
  
 Para usar un `CMiniFrameWnd` de objetos, definir primero el objeto. A continuación, llame a la [crear](#create) función miembro para mostrar la ventana de marco reducido.  
  
 Para obtener más información sobre cómo usar `CMiniFrameWnd` objetos, consulte el artículo [acoplamiento y barras de herramientas flotante](../../mfc/docking-and-floating-toolbars.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cminiframewnd"></a>  CMiniFrameWnd::CMiniFrameWnd  
 Construye un `CMiniFrameWnd` de objeto, pero no crea la ventana.  
  
```  
CMiniFrameWnd();
```  
  
### <a name="remarks"></a>Comentarios  
 Para crear la ventana, llame a [CMiniFrameWnd::Create](#create).  
  
##  <a name="create"></a>  CMiniFrameWnd::Create  
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
 *lpClassName*  
 Apunta a una cadena de caracteres terminada en null que se nombra la clase de Windows. El nombre de clase puede ser cualquier nombre registrado con global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función. Si es NULL, la clase de ventana se registrará automáticamente el marco de trabajo. MFC proporciona la clase predeterminada de los siguientes estilos y atributos:  
  
-   Estilo de conjuntos de bits CS_DBLCLKS, que envía haga doble clic en los mensajes al procedimiento de ventana cuando el usuario hace doble clic del mouse.  
  
-   Establece los bits de estilo CS_HREDRAW y CS_VREDRAW, que dirigen el contenido del área de cliente se vuelva a dibujar cuando la ventana cambia de tamaño.  
  
-   Establece el cursor de la clase a la IDC_ARROW estándar de Windows.  
  
-   Establece el pincel de fondo de la clase con valores NULL, por lo que la ventana no borrará el fondo.  
  
-   Establece el icono de clase en el icono del logotipo de Windows estándar, marca saludando.  
  
-   Establece la ventana de tamaño y posición, como se indica en Windows.  
  
 *lpWindowName*  
 Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.  
  
 *dwStyle*  
 Especifica los atributos de estilo de ventana. Estos pueden incluir los estilos de ventana estándar y uno o varios de los siguientes estilos especiales:  
  
- MFS_MOVEFRAME permite que la ventana de marco reducido va a mover, haga clic en cualquiera de los bordes de la ventana, no solo el título.  
  
- MFS_4THICKFRAME deshabilita el cambio de tamaño de la ventana de marco reducido.  
  
- MFS_SYNCACTIVE sincroniza la activación de la ventana de marco reducido para la activación de su ventana primaria.  
  
- ¿MFS_THICKFRAME permite permiten tener un tamaño tan pequeña como el contenido del área cliente de la ventana de marco reducido.  
  
- MFS_BLOCKSYSMENU deshabilita el acceso al menú del sistema y el menú de control y los convierte en parte de la leyenda (barra de título).  
  
 Consulte [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los valores de estilo de ventana posible. La combinación típica que se utiliza para ventanas de marco reducido es WS_POPUP&#124;WS_CAPTION&#124;WS_SYSMENU.  
  
 *Rect*  
 Un `RECT` estructura que especifica las dimensiones deseadas de la ventana.  
  
 *pParentWnd*  
 Apunta a la ventana primaria. Utilice NULL para ventanas de nivel superior.  
  
 *nID*  
 Si la ventana de marco reducido se crea como una ventana secundaria, este es el identificador del control secundario; en caso contrario, es 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 `Create` Inicializa el nombre de la ventana de la clase y nombre de la ventana y registra los valores predeterminados para su estilo y el elemento primario.  
  
##  <a name="createex"></a>  CMiniFrameWnd::CreateEx  
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
 *dwExStyle*  
 Especifica el estilo extendido de la `CMiniFrameWnd` va a crear. Aplicar cualquiera de los [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles) a la ventana.  
  
 *lpClassName*  
 Apunta a una cadena de caracteres terminada en null que se nombra la clase de Windows (un [WNDCLASS](http://msdn.microsoft.com/library/windows/desktop/ms633576) estructura). El nombre de clase puede ser cualquier nombre registrado con global [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) función o cualquiera de los nombres de clase de control predefinido. No debe ser NULL.  
  
 *lpWindowName*  
 Apunta a una cadena de caracteres terminada en null que contiene el nombre de la ventana.  
  
 *dwStyle*  
 Especifica los atributos de estilo de ventana. Consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) y [CWnd:: Create](../../mfc/reference/cwnd-class.md#create) para obtener una descripción de los valores posibles.  
  
 *Rect*  
 El tamaño y posición de la ventana, en coordenadas de cliente de *pParentWnd*.  
  
 *pParentWnd*  
 Señala al objeto de ventana principal.  
  
 *nID*  
 El identificador de la ventana secundaria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El `CreateEx` los parámetros especifican el WNDCLASS, estilo de ventana y la posición inicial (opcionalmente) y tamaño de la ventana. `CreateEx` También especifica el elemento primario (si existe) y el Id. de la ventana  
  
 Cuando `CreateEx` envíos de Windows que se ejecuta el [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo), [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), y [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate) mensajes en la ventana.  
  
 Para extender el control de mensajes de forma predeterminada, derive una clase de `CMiniFrameWnd`, agregue un mapa de mensajes a la nueva clase y proporcionar funciones de miembro para los mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para una nueva clase.  
  
 Invalidar aún más `On` *mensaje* controladores para agregar más funcionalidad a la clase derivada de mensaje.  
  
 Si se especifica el estilo WS_VISIBLE, Windows envía todos los mensajes necesarios para activar y mostrar la ventana a la ventana. Si el estilo de ventana especifica una barra de título, el título de ventana que apunta el *lpszWindowName* parámetro se muestra en la barra de título.  
  
 El *dwStyle* parámetro puede ser cualquier combinación de [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).  
  
 Ya no se admiten las ventanas de cuadro de herramientas de paleta de estilo antiguas. El estilo anterior, que no tenía un botón de cierre de "X", se admite cuando se ejecuta una aplicación MFC en versiones anteriores de Windows, pero ya no se admite en Visual C++. NET. Ahora se admite el nuevo estilo WS_EX_TOOLWINDOW; Para obtener una descripción de este estilo, consulte [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles).  
  
## <a name="see-also"></a>Vea también  
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)
