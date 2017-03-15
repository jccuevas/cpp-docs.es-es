---
title: CToolBar (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CToolBar
dev_langs:
- C++
helpviewer_keywords:
- Windows toolbar common controls [C++]
- control bars [C++], CToolBar class
- toolbars [C++], CToolBar class
- buttons [C++], MFC toolbars
- bitmaps [C++], button controls
- CToolBar class
- Windows common controls [C++], CToolBar class
ms.assetid: e868da26-5e07-4607-9651-e2f863ad9059
caps.latest.revision: 26
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
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: d7fea85426eef09f3694bd26e037acaaccc63f01
ms.lasthandoff: 02/24/2017

---
# <a name="ctoolbar-class"></a>CToolBar (clase)
Barras de control que tienen una fila de botones de mapas de bits y separadores opcionales.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CToolBar : public CControlBar  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CToolBar::CToolBar](#ctoolbar)|Construye un objeto `CToolBar`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CToolBar::CommandToIndex](#commandtoindex)|Devuelve el índice de un botón con el identificador de comando especificado.|  
|[CToolBar:: Create](#create)|Crea la barra de herramientas de Windows y lo adjunta a la `CToolBar` objeto.|  
|[CToolBar:: CreateEx](#createex)|Crea un `CToolBar` objeto estilos adicionales para el objeto incrustado `CToolBarCtrl` objeto.|  
|[CToolBar::GetButtonInfo](#getbuttoninfo)|Recupera el identificador, el estilo y el número de la imagen de un botón.|  
|[CToolBar:: GetButtonStyle](#getbuttonstyle)|Recupera el estilo de un botón.|  
|[CToolBar::GetButtonText](#getbuttontext)|Recupera el texto que aparecerá en un botón.|  
|[CToolBar::GetItemID](#getitemid)|Devuelve el identificador de comando de un botón o un separador en el índice especificado.|  
|[CToolBar::GetItemRect](#getitemrect)|Recupera el rectángulo de presentación para el elemento en el índice especificado.|  
|[CToolBar:: GetToolBarCtrl](#gettoolbarctrl)|Permite el acceso directo al control subyacente común.|  
|[CToolBar::LoadBitmap](#loadbitmap)|Carga el mapa de bits que contiene imágenes de mapa de bits del botón.|  
|[CToolBar::LoadToolBar](#loadtoolbar)|Carga un recurso de barra de herramientas creado con el editor de recursos.|  
|[CToolBar::SetBitmap](#setbitmap)|Establece una imagen de mapa de bits.|  
|[CToolBar:: SetButtonInfo](#setbuttoninfo)|Establece el identificador, el estilo y el número de la imagen de un botón.|  
|[CToolBar::SetButtons](#setbuttons)|Botón de conjuntos de estilos y un índice de imágenes de botón en el mapa de bits.|  
|[CToolBar::SetButtonStyle](#setbuttonstyle)|Establece el estilo de un botón.|  
|[CToolBar::SetButtonText](#setbuttontext)|Establece el texto que aparecerá en un botón.|  
|[CToolBar::SetHeight](#setheight)|Establece el alto de la barra de herramientas.|  
|[CToolBar::SetSizes](#setsizes)|Establece el tamaño de los botones y sus mapas de bits.|  
  
## <a name="remarks"></a>Comentarios  
 Los botones pueden actuar como botones de comando, botones de casilla de verificación o botones de radio. `CToolBar`los objetos son normalmente incrustados miembros de objetos de ventana de marco derivados de la clase [CFrameWnd](../../mfc/reference/cframewnd-class.md) o [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md).  
  
 [CToolBar:: GetToolBarCtrl](#gettoolbarctrl), una función miembro nueva para MFC 4.0, permite aprovechar la compatibilidad del control común de Windows para la personalización de la barra de herramientas y una funcionalidad adicional. `CToolBar`las funciones de miembro proporcionan la mayor parte de la funcionalidad de los controles comunes de Windows; Sin embargo, cuando se llama a `GetToolBarCtrl`, puede dar a las barras de herramientas aún más las características de las barras de herramientas de Windows 95 ó 98. Cuando se llama a `GetToolBarCtrl`, devolverá una referencia a un `CToolBarCtrl` objeto. Consulte [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) para obtener más información sobre el diseño de las barras de herramientas con controles comunes de Windows. Para obtener información general sobre los controles comunes, consulte [controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Visual C++ proporciona dos métodos para crear una barra de herramientas. Para crear un recurso de barra de herramientas mediante el Editor de recursos, siga estos pasos:  
  
1.  Crear un recurso de la barra de herramientas.  
  
2.  Construir la `CToolBar` objeto.  
  
3.  Llame a la [crear](#create) (o [CreateEx](#createex)) (función) para crear la barra de herramientas de Windows y adjuntarlo a la `CToolBar` objeto.  
  
4.  Llame a [LoadToolBar](#loadtoolbar) para cargar el recurso de la barra de herramientas.  
  
 De lo contrario, siga estos pasos:  
  
1.  Construir la `CToolBar` objeto.  
  
2.  Llame a la [crear](#create) (o [CreateEx](#createex)) (función) para crear la barra de herramientas de Windows y adjuntarlo a la `CToolBar` objeto.  
  
3.  Llame a [LoadBitmap](#loadbitmap) para cargar el mapa de bits que contiene las imágenes de botón de barra de herramientas.  
  
4.  Llame a [SetButtons](#setbuttons) para establecer el estilo de botón y asociar cada botón con una imagen del mapa de bits.  
  
 Todas las imágenes de botón en la barra de herramientas proceden de un mapa de bits, que debe contener una imagen para cada botón. Todas las imágenes deben tener el mismo tamaño; el valor predeterminado es 16 píxeles de ancho y alto de 15 píxeles. Imágenes deben estar en paralelo en el mapa de bits.  
  
 El `SetButtons` función toma un puntero a una matriz de identificadores de control y un entero que especifica el número de elementos de la matriz. La función Id. de cada botón establece en el valor del elemento correspondiente de la matriz y asigna un índice de imagen, que especifica la posición de la imagen del botón en el mapa de bits de cada botón. Si un elemento de matriz tiene el valor **ID_SEPARATOR**, no se asigna ningún índice de la imagen.  
  
 Normalmente, el orden de las imágenes de mapa de bits es el orden en que se dibujan en la pantalla, pero puede usar el [SetButtonInfo](#setbuttoninfo) función para cambiar la relación entre el orden de la imagen y el orden de dibujo.  
  
 Todos los botones de una barra de herramientas tienen el mismo tamaño. El valor predeterminado es 24 x 22 píxeles, de acuerdo con *instrucciones de la interfaz de Windows para el diseño de Software de*. Espacio adicional entre las dimensiones de la imagen y el botón se usa para formar un borde alrededor de la imagen.  
  
 Cada botón tiene una imagen. Los distintos Estados de botón y se generan los estilos (presionado, arriba, abajo, deshabilitado, disabled hacia abajo e indeterminado) desde que una imagen. Aunque los mapas de bits pueden ser cualquier color, puede conseguir los mejores resultados con imágenes en negro y tonalidades de gris.  
  
> [!WARNING]
> `CToolBar`admite mapas de bits con un máximo de 16 colores. Cuando se carga una imagen en un editor de la barra de herramientas, Visual Studio convierte la imagen en un mapa de bits de 16 colores, si es necesario y muestra un mensaje de advertencia si la imagen se ha convertido. Si utiliza una imagen con más de 16 colores (mediante un editor externo para editar la imagen), la aplicación podría tener un comportamiento inesperado.  
  
 Botones de barra de herramientas imitan botones de comando de forma predeterminada. Sin embargo, también pueden imitar los botones de barra de herramientas, botones de casilla de verificación o botones de radio. Botones de casilla de verificación tienen tres estados: activado, borrados e indeterminado. Botones de radio tienen sólo dos estados: activada y desactivada.  
  
 Para establecer un botón individual o el estilo del separador sin que apunta a una matriz, llame a [GetButtonStyle](#getbuttonstyle) para recuperar el estilo y, a continuación, llame a [SetButtonStyle](#setbuttonstyle) en lugar de `SetButtons`. `SetButtonStyle`es muy útil cuando desea cambiar el estilo de un botón en tiempo de ejecución.  
  
 Para asignar texto que aparecerá en un botón, llame a [GetButtonText](#getbuttontext) para recuperar el texto para que aparezcan en el botón y, a continuación, llame a [SetButtonText](#setbuttontext) para establecer el texto.  
  
 Para crear un botón de casilla de verificación, asignar el estilo **TBBS_CHECKBOX** o use un `CCmdUI` del objeto `SetCheck` función miembro en un `ON_UPDATE_COMMAND_UI` controlador. Llamar a `SetCheck` un botón de comando se convierte en un botón de casilla de verificación. Pasar `SetCheck` un argumento de 0 para no está activada, 1 para activado o 2 para indeterminado.  
  
 Para crear un botón de radio, llame a un [CCmdUI](../../mfc/reference/ccmdui-class.md) del objeto [SetRadio](../../mfc/reference/ccmdui-class.md#setradio) función miembro desde un `ON_UPDATE_COMMAND_UI` controlador. Pasar `SetRadio` un argumento de 0 para distinto de cero para activada o desactivada. Para proporcionar un comportamiento mutuamente exclusivos de un grupo de radio, debe tener `ON_UPDATE_COMMAND_UI` controladores para todos los botones del grupo.  
  
 Para obtener más información sobre el uso de `CToolBar`, vea el artículo [implementación de la barra de herramientas de MFC](../../mfc/mfc-toolbar-implementation.md) y [Nota técnica 31: barras de Control](../../mfc/tn031-control-bars.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CControlBar](../../mfc/reference/ccontrolbar-class.md)  
  
 `CToolBar`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxext.h  
  
##  <a name="a-namecommandtoindexa--ctoolbarcommandtoindex"></a><a name="commandtoindex"></a>CToolBar::CommandToIndex  
 Esta función miembro devuelve el índice de la primera barra de herramientas botón, comenzando en la posición 0, cuyo identificador de comando coincida con `nIDFind`.  
  
```  
int CommandToIndex(UINT nIDFind) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIDFind`  
 Id. de comando de un botón de barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del botón, o –&1; si no hay ningún botón tiene el identificador de comando especificado.  
  
##  <a name="a-namecreatea--ctoolbarcreate"></a><a name="create"></a>CToolBar:: Create  
 Esta función miembro crea una barra de herramientas de Windows (una ventana secundaria) y lo asocia a la `CToolBar` objeto.  
  
```  
virtual BOOL Create(
    CWnd* pParentWnd,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_TOP,  
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la ventana principal de la barra de herramientas.  
  
 `dwStyle`  
 El estilo de barra de herramientas. Estilos de barra de herramientas adicionales compatibles son:  
  
- `CBRS_TOP`Barra de control está en la parte superior de la ventana de marco.  
  
- `CBRS_BOTTOM`Barra de control está en la parte inferior de la ventana de marco.  
  
- `CBRS_NOALIGN`Barra de control no se cambia de posición cuando se cambia el elemento primario.  
  
- `CBRS_TOOLTIPS`Barra de control muestra información sobre herramientas.  
  
- **CBRS_SIZE_DYNAMIC** barra de controles es dinámica.  
  
- **CBRS_SIZE_FIXED** barra de controles es fijo.  
  
- **CBRS_FLOATING** barra de controles está flotando.  
  
- `CBRS_FLYBY`Barra de estado muestra información acerca del botón.  
  
- **CBRS_HIDE_INPLACE** no se muestra la barra de Control al usuario.  
  
 `nID`  
 Identificador de ventana secundaria. de la barra de herramientas  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 También establece el alto de la barra de herramientas a un valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#179;](../../mfc/codesnippet/cpp/ctoolbar-class_1.cpp)]  
  
##  <a name="a-namecreateexa--ctoolbarcreateex"></a><a name="createex"></a>CToolBar:: CreateEx  
 Llame a esta función para crear una barra de herramientas de Windows (una ventana secundaria) y asociarla con el `CToolBar` objeto.  
  
```  
virtual BOOL CreateEx(
    CWnd* pParentWnd,  
    DWORD dwCtrlStyle = TBSTYLE_FLAT,  
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_ALIGN_TOP,  
    CRect rcBorders = CRect(
    0, 
    0, 
    0, 
    0), 
    UINT nID = AFX_IDW_TOOLBAR);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la ventana principal de la barra de herramientas.  
  
 `dwCtrlStyle`  
 Estilos adicionales para la creación de los datos incrustados [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) objeto. De forma predeterminada, este valor se establece en **TBSTYLE_FLAT**. Para obtener una lista completa de los estilos de barra de herramientas, consulte `dwStyle`.  
  
 `dwStyle`  
 El estilo de barra de herramientas. Consulte [Control de barra de herramientas y estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb760439) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de estilos apropiados.  
  
 *rcBorders*  
 Un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que define el ancho de los bordes de ventana de la barra de herramientas. Estos límites se establecen en 0,0,0,0 de forma predeterminada, lo que resulta en una ventana de la barra de herramientas sin bordes.  
  
 `nID`  
 Identificador de ventana secundaria. de la barra de herramientas  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 También establece el alto de la barra de herramientas a un valor predeterminado.  
  
 Utilice `CreateEx`, en lugar de [crear](#create), cuando determinados estilos deben estar presentes durante la creación del control de barra de herramientas incrustada. Por ejemplo, establecer `dwCtrlStyle` a **TBSTYLE_FLAT | TBSTYLE_TRANSPARENT** para crear una barra de herramientas que se parece a las barras de herramientas de Internet Explorer 4.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#180;](../../mfc/codesnippet/cpp/ctoolbar-class_2.cpp)]  
  
##  <a name="a-namectoolbara--ctoolbarctoolbar"></a><a name="ctoolbar"></a>CToolBar::CToolBar  
 Esta función miembro construye una `CToolBar` del objeto y establece los tamaños predeterminados.  
  
```  
CToolBar();
```  
  
### <a name="remarks"></a>Comentarios  
 Llame a la [crear](#create) función de miembro para crear la ventana de la barra de herramientas.  
  
##  <a name="a-namegetbuttoninfoa--ctoolbargetbuttoninfo"></a><a name="getbuttoninfo"></a>CToolBar::GetButtonInfo  
 Esta función miembro recupera el Id. de control, el estilo y el índice de la imagen del botón de barra de herramientas o separador en la ubicación especificada por *nIndex.*  
  
```  
void GetButtonInfo(
    int nIndex,  
    UINT& nID,  
    UINT& nStyle,  
    int& iImage) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del botón de barra de herramientas o separador es cuya información va a recuperar.  
  
 `nID`  
 Hacer referencia a un **UINT** que se establece en el identificador de comando del botón.  
  
 `nStyle`  
 Hacer referencia a un **UINT** que se establece el estilo del botón.  
  
 `iImage`  
 Referencia a un entero que se establece en el índice de la imagen del botón del mapa de bits.  
  
### <a name="remarks"></a>Comentarios  
 Estos valores se asignan a las variables de referencia `nID`, `nStyle`, y `iImage`. El índice de imagen es la posición de la imagen del mapa de bits que contiene imágenes para los botones de barra de herramientas. Es la primera imagen en la posición 0.  
  
 Si `nIndex` especifica un separador, `iImage` se establece en el ancho del separador en píxeles.  
  
##  <a name="a-namegetbuttonstylea--ctoolbargetbuttonstyle"></a><a name="getbuttonstyle"></a>CToolBar:: GetButtonStyle  
 Llame a esta función miembro para recuperar el estilo de un botón o un separador de barra de herramientas.  
  
```  
UINT GetButtonStyle(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 El índice del estilo de botón o el separador de barra de herramientas que desea recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El estilo del botón o el separador especificado por `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 Estilo de un botón determina la apariencia del botón y cómo responde a la entrada del usuario. Consulte [SetButtonStyle](#setbuttonstyle) para obtener ejemplos de estilos de botón.  
  
##  <a name="a-namegetbuttontexta--ctoolbargetbuttontext"></a><a name="getbuttontext"></a>CToolBar::GetButtonText  
 Llame a esta función miembro para recuperar el texto que aparece en un botón.  
  
```  
CString GetButtonText(int nIndex) const;  
  
void GetButtonText(
    int nIndex,  
    CString& rString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del texto que se va a recuperar.  
  
 `rString`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto que se va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` objeto que contiene el texto del botón.  
  
### <a name="remarks"></a>Comentarios  
 La segunda forma de este miembro de función llena un `CString` objeto con el texto de la cadena.  
  
##  <a name="a-namegetitemida--ctoolbargetitemid"></a><a name="getitemid"></a>CToolBar::GetItemID  
 Esta función miembro devuelve el identificador de comando del botón o el separador especificado por `nIndex`.  
  
```  
UINT GetItemID(int nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del elemento cuyo identificador se va a recuperar.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de comando del botón o el separador especificado por `nIndex`.  
  
### <a name="remarks"></a>Comentarios  
 Devuelven separadores **ID_SEPARATOR**.  
  
##  <a name="a-namegetitemrecta--ctoolbargetitemrect"></a><a name="getitemrect"></a>CToolBar::GetItemRect  
 Esta función miembro se llena la `RECT` estructura cuya dirección se encuentra en `lpRect` con las coordenadas del botón o el separador especificado por `nIndex`.  
  
```  
virtual void GetItemRect(
    int nIndex,  
    LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del producto (botón o el separador) cuyas coordenadas del rectángulo que se va a recuperar.  
  
 `lpRect`  
 Dirección de la [RECT](../../mfc/reference/rect-structure1.md) estructura que contiene las coordenadas del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Las coordenadas están en píxeles con respecto a la esquina superior izquierda de la barra de herramientas.  
  
 Use `GetItemRect` para obtener las coordenadas de un separador que desea reemplazar con un cuadro combinado u otro control.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CToolBar::SetSizes](#setsizes).  
  
##  <a name="a-namegettoolbarctrla--ctoolbargettoolbarctrl"></a><a name="gettoolbarctrl"></a>CToolBar:: GetToolBarCtrl  
 Esta función miembro permite el acceso directo al control subyacente común.  
  
```  
CToolBarCtrl& GetToolBarCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Referencia a un objeto `CToolBarCtrl`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `GetToolBarCtrl` para aprovechar la funcionalidad del control común de barra de herramientas de Windows y para aprovechar la compatibilidad con [CToolBarCtrl](../../mfc/reference/ctoolbarctrl-class.md) proporciona para la personalización de la barra de herramientas.  
  
 Para obtener más información acerca del uso de controles comunes, vea el artículo [controles](../../mfc/controls-mfc.md) y [controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocViewSDI&#15;](../../mfc/codesnippet/cpp/ctoolbar-class_3.cpp)]  
  
##  <a name="a-nameloadbitmapa--ctoolbarloadbitmap"></a><a name="loadbitmap"></a>CToolBar::LoadBitmap  
 Llame a esta función miembro para cargar el mapa de bits especificado por `lpszResourceName` o `nIDResource`.  
  
```  
BOOL LoadBitmap(LPCTSTR lpszResourceName);  
BOOL LoadBitmap(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszResourceName`  
 Puntero al nombre del recurso de mapa de bits que se va a cargar.  
  
 `nIDResource`  
 Id. de recurso de mapa de bits que se va a cargar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits debe contener una imagen para cada botón de barra de herramientas. Si las imágenes no son del tamaño estándar (16 píxeles de ancho y alto de 15 píxeles), llamada [SetSizes](#setsizes) para establecer el tamaño de botón y sus imágenes.  
  
> [!WARNING]
> `CToolBar`admite mapas de bits con un máximo de 16 colores. Cuando se carga una imagen en un editor de la barra de herramientas, Visual Studio convierte la imagen en un mapa de bits de 16 colores, si es necesario y muestra un mensaje de advertencia si la imagen se ha convertido. Si utiliza una imagen con más de 16 colores (mediante un editor externo para editar la imagen), la aplicación podría tener un comportamiento inesperado.  
  
##  <a name="a-nameloadtoolbara--ctoolbarloadtoolbar"></a><a name="loadtoolbar"></a>CToolBar::LoadToolBar  
 Llame a esta función miembro para la carga de la barra de herramientas especificado por `lpszResourceName` o `nIDResource`.  
  
```  
BOOL LoadToolBar(LPCTSTR lpszResourceName);  
BOOL LoadToolBar(UINT nIDResource);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszResourceName`  
 Puntero al nombre del recurso de la barra de herramientas que se va a cargar.  
  
 `nIDResource`  
 Id. de recurso de la barra de herramientas que se va a cargar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [editor de la barra de herramientas](../../windows/toolbar-editor.md) en para obtener más información acerca de cómo crear un recurso de la barra de herramientas.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CToolBar:: CreateEx](#createex).  
  
##  <a name="a-namesetbitmapa--ctoolbarsetbitmap"></a><a name="setbitmap"></a>CToolBar::SetBitmap  
 Llame a esta función miembro para establecer la imagen de mapa de bits de la barra de herramientas.  
  
```  
BOOL SetBitmap(HBITMAP hbmImageWell);
```  
  
### <a name="parameters"></a>Parámetros  
 *hbmImageWell*  
 Identificador de una imagen de mapa de bits que está asociada a una barra de herramientas.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Por ejemplo, llamar a `SetBitmap` para cambiar la imagen de mapa de bits después de que el usuario realiza una acción en un documento que cambia la acción de un botón.  
  
##  <a name="a-namesetbuttoninfoa--ctoolbarsetbuttoninfo"></a><a name="setbuttoninfo"></a>CToolBar:: SetButtonInfo  
 Llame a esta función miembro para establecer el identificador de comando, estilo y número de la imagen del botón.  
  
```  
void SetButtonInfo(
    int nIndex,  
    UINT nID,  
    UINT nStyle,  
    int iImage);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice de base cero del botón o el separador cuya información se va a establecer.  
  
 `nID`  
 El valor al que se establece el identificador de comando del botón.  
  
 `nStyle`  
 El nuevo estilo de botón. Se admiten los siguientes estilos de botón:  
  
- **TBBS_BUTTON** pushbutton estándar (predeterminado)  
  
- **TBBS_SEPARATOR** separador  
  
- **TBBS_CHECKBOX** botón de casilla de verificación automático  
  
- **TBBS_GROUP** marca el inicio de un grupo de botones  
  
- **TBBS_CHECKGROUP** marca el inicio de un grupo de botones de casilla de verificación  
  
- **TBBS_DROPDOWN** crea un botón de lista desplegable.  
  
- **TBBS_AUTOSIZE** ancho del botón se calcularán basándose en el texto del botón, no en el tamaño de la imagen.  
  
- **TBBS_NOPREFIX** el texto del botón no tendrá un prefijo de acelerador asociado a él.  
  
 `iImage`  
 Nuevo índice de la imagen del botón del mapa de bits.  
  
### <a name="remarks"></a>Comentarios  
 Para establecer los separadores que tienen el estilo **TBBS_SEPARATOR**, esta función establece el ancho del separador en píxeles, para el valor almacenado en `iImage`.  
  
> [!NOTE]
>  También puede establecer los Estados del botón mediante la `nStyle` parámetro; sin embargo, porque los Estados del botón se controlan mediante el [ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4) controlador, cualquier estado establecido en `SetButtonInfo` se perderá durante el siguiente procesamiento en inactividad. Consulte [cómo actualizar objetos de la interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: barras de Control](../../mfc/tn031-control-bars.md) para obtener más información.  
  
 Para obtener información sobre las imágenes de mapa de bits y botones, consulte la [CToolBar](../../mfc/reference/ctoolbar-class.md) información general y [CToolBar::LoadBitmap](#loadbitmap).  
  
##  <a name="a-namesetbuttonsa--ctoolbarsetbuttons"></a><a name="setbuttons"></a>CToolBar::SetButtons  
 Esta función miembro establece el identificador de comando de cada botón de barra de herramientas en el valor especificado por el elemento correspondiente de la matriz `lpIDArray`.  
  
```  
BOOL SetButtons(
    const UINT* lpIDArray,  
    int nIDCount);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpIDArray`  
 Puntero a una matriz de identificadores de comando. Puede ser **NULL** asignar botones vacía.  
  
 `nIDCount`  
 Número de elementos de la matriz señalada por `lpIDArray`.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si un elemento de la matriz tiene el valor **ID_SEPARATOR**, se crea un separador en la posición correspondiente de la barra de herramientas. Esta función también establece el estilo de cada botón en **TBBS_BUTTON** y el estilo de cada separador a **TBBS_SEPARATOR**y asigna un índice de imágenes para cada botón. El índice de imagen especifica la posición de la imagen del botón del mapa de bits.  
  
 No es necesario tener en cuenta los separadores del mapa de bits porque esta función no asignar índices de imágenes para los separadores. Si la barra de herramientas tiene botones en posiciones 0, 1 y 3 y un separador en la posición 2, las imágenes en las posiciones 0, 1 y 2 en el mapa de bits se asignan a los botones situados en posiciones 0, 1 y 3, respectivamente.  
  
 Si `lpIDArray` es **NULL**, esta función asigna espacio para el número de elementos especificado por `nIDCount`. Utilice [SetButtonInfo](#setbuttoninfo) para establecer los atributos de cada elemento.  
  
##  <a name="a-namesetbuttonstylea--ctoolbarsetbuttonstyle"></a><a name="setbuttonstyle"></a>CToolBar::SetButtonStyle  
 Llame a esta función miembro para establecer el estilo de un botón o un separador o agrupar los botones.  
  
```  
void SetButtonStyle(
    int nIndex,  
    UINT nStyle);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del botón o el separador cuya información se va a establecer.  
  
 `nStyle`  
 El estilo de botón. Se admiten los siguientes estilos de botón:  
  
- **TBBS_BUTTON** pushbutton estándar (predeterminado)  
  
- **TBBS_SEPARATOR** separador  
  
- **TBBS_CHECKBOX** botón de casilla de verificación automático  
  
- **TBBS_GROUP** marca el inicio de un grupo de botones  
  
- **TBBS_CHECKGROUP** marca el inicio de un grupo de botones de casilla de verificación  
  
- **TBBS_DROPDOWN** crea un botón de lista desplegable  
  
- **TBBS_AUTOSIZE** ancho del botón se calcularán basándose en el texto del botón, no en el tamaño de la imagen  
  
- **TBBS_NOPREFIX** el texto del botón no tendrá asociado un prefijo de Acelerador  
  
### <a name="remarks"></a>Comentarios  
 Estilo de un botón determina la apariencia del botón y cómo responde a la entrada del usuario.  
  
 Antes de llamar a `SetButtonStyle`, llame a la [GetButtonStyle](#getbuttonstyle) función miembro para recuperar el estilo de botón o el separador.  
  
> [!NOTE]
>  También puede establecer los Estados del botón mediante la `nStyle` parámetro; sin embargo, porque los Estados del botón se controlan mediante el [ON_UPDATE_COMMAND_UI](http://msdn.microsoft.com/library/c4de3c21-2d2e-4b89-a4ce-d0c0e2d9edc4) controlador, cualquier estado establecido en `SetButtonStyle` se perderá durante el siguiente procesamiento en inactividad. Consulte [cómo actualizar objetos de la interfaz de usuario](../../mfc/how-to-update-user-interface-objects.md) y [TN031: barras de Control](../../mfc/tn031-control-bars.md) para obtener más información.  
  
##  <a name="a-namesetbuttontexta--ctoolbarsetbuttontext"></a><a name="setbuttontext"></a>CToolBar::SetButtonText  
 Llame a esta función para establecer el texto en un botón.  
  
```  
BOOL SetButtonText(
    int nIndex,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Índice del botón cuyo texto se va a establecer.  
  
 `lpszText`  
 Señala el texto que se va a establecer en un botón.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CToolBar:: GetToolBarCtrl](#gettoolbarctrl).  
  
##  <a name="a-namesetheighta--ctoolbarsetheight"></a><a name="setheight"></a>CToolBar::SetHeight  
 Esta función miembro establece el alto de la barra de herramientas para el valor, en píxeles, que se especifica en `cyHeight`.  
  
```  
void SetHeight(int cyHeight);
```  
  
### <a name="parameters"></a>Parámetros  
 `cyHeight`  
 El alto en píxeles de la barra de herramientas.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a [SetSizes](#setsizes), utilizar esta función miembro para invalidar el alto de la barra de herramientas estándar. Si el alto es demasiado pequeño, se recortará los botones en la parte inferior.  
  
 Si no se llama a esta función, el marco de trabajo usa el tamaño del botón para determinar el alto de la barra de herramientas.  
  
##  <a name="a-namesetsizesa--ctoolbarsetsizes"></a><a name="setsizes"></a>CToolBar::SetSizes  
 Llame a esta función miembro para establecer los botones de la barra de herramientas en el tamaño, en píxeles, que se especifica en *sizeButton*.  
  
```  
void SetSizes(
    SIZE sizeButton,  
    SIZE sizeImage);
```  
  
### <a name="parameters"></a>Parámetros  
 *sizeButton*  
 El tamaño en píxeles de cada botón.  
  
 `sizeImage`  
 El tamaño en píxeles de cada imagen.  
  
### <a name="remarks"></a>Comentarios  
 El `sizeImage` parámetro debe contener el tamaño, en píxeles, de las imágenes de mapa de bits de la barra de herramientas. Las dimensiones en *sizeButton* debe ser suficiente para contener la imagen más 7 píxeles adicionales de ancho y 6 adicional de alto. Esta función también establece el alto de la barra de herramientas para ajustarse a los botones.  
  
 Llame a esta función miembro sólo para las barras de herramientas que no siguen *instrucciones de la interfaz de Windows para el diseño de Software* recomendaciones tamaños de imagen y botón.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCListView Nº&8;](../../atl/reference/codesnippet/cpp/ctoolbar-class_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CTRLBARS de ejemplo de MFC](../../visual-cpp-samples.md)   
 [DLGCBR32 de ejemplo MFC](../../visual-cpp-samples.md)   
 [Ejemplo MFC DOCKTOOL](../../visual-cpp-samples.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CToolBarCtrl (clase)](../../mfc/reference/ctoolbarctrl-class.md)   
 [CControlBar (clase)](../../mfc/reference/ccontrolbar-class.md)

