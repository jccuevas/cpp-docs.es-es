---
title: CComboBoxEx (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComboBoxEx
- AFXCMN/CComboBoxEx
- AFXCMN/CComboBoxEx::CComboBoxEx
- AFXCMN/CComboBoxEx::Create
- AFXCMN/CComboBoxEx::CreateEx
- AFXCMN/CComboBoxEx::DeleteItem
- AFXCMN/CComboBoxEx::GetComboBoxCtrl
- AFXCMN/CComboBoxEx::GetEditCtrl
- AFXCMN/CComboBoxEx::GetExtendedStyle
- AFXCMN/CComboBoxEx::GetImageList
- AFXCMN/CComboBoxEx::GetItem
- AFXCMN/CComboBoxEx::HasEditChanged
- AFXCMN/CComboBoxEx::InsertItem
- AFXCMN/CComboBoxEx::SetExtendedStyle
- AFXCMN/CComboBoxEx::SetImageList
- AFXCMN/CComboBoxEx::SetItem
- AFXCMN/CComboBoxEx::SetWindowTheme
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes, CComboBoxEx class
- Windows common controls [C++], extended combo boxes
- common controls [C++], extended combo boxes
- combo boxes [C++], CComboBoxEx class
- Internet Explorer 4.0 common controls
- CComboBoxEx class
ms.assetid: 33ca960a-2409-478c-84a4-a2ee8ecfe8f7
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: e88ed701111b49e3a5d3b32868bfad8e77206086
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomboboxex-class"></a>CComboBoxEx (clase)
Extiende el control de cuadro combinado proporcionando compatibilidad con las listas de imágenes.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CComboBoxEx : public CComboBox  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComboBoxEx::CComboBoxEx](#ccomboboxex)|Construye un objeto `CComboBoxEx`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComboBoxEx::Create](#create)|Crea el cuadro combinado y lo adjunta a la `CComboBoxEx` objeto.|  
|[CComboBoxEx::CreateEx](#createex)|Crea un cuadro combinado con los estilos extendidos de Windows especificados y lo adjunta a un **ComboBoxEx** objeto.|  
|[CComboBoxEx::DeleteItem](#deleteitem)|Quita un elemento de un **ComboBoxEx** control.|  
|[CComboBoxEx::GetComboBoxCtrl](#getcomboboxctrl)|Recupera un puntero al control de cuadro combinado secundarios.|  
|[CComboBoxEx::GetEditCtrl](#geteditctrl)|Recupera el identificador de la parte del control de edición de un **ComboBoxEx** control.|  
|[CComboBoxEx::GetExtendedStyle](#getextendedstyle)|Recupera los estilos extendidos que se usan para un **ComboBoxEx** control.|  
|[CComboBoxEx::GetImageList](#getimagelist)|Recupera un puntero a la lista de imágenes asignada a un **ComboBoxEx** control.|  
|[CComboBoxEx:: GetItem](#getitem)|Recupera información de artículos un determinado **ComboBoxEx** elemento.|  
|[CComboBoxEx::HasEditChanged](#haseditchanged)|Determina si el usuario ha cambiado el contenido de la **ComboBoxEx** editar control escribiendo.|  
|[CComboBoxEx:: InsertItem](#insertitem)|Inserta un nuevo elemento en una **ComboBoxEx** control.|  
|[CComboBoxEx::SetExtendedStyle](#setextendedstyle)|Establece los estilos extendidos dentro de un **ComboBoxEx** control.|  
|[CComboBoxEx:: SetImageList](#setimagelist)|Establece una lista de imágenes para un **ComboBoxEx** control.|  
|[CComboBoxEx:: SetItem](#setitem)|Establece los atributos de un elemento en un **ComboBoxEx** control.|  
|[CComboBoxEx::SetWindowTheme](#setwindowtheme)|Establece el estilo visual el total combinado de control de cuadro.|  
  
## <a name="remarks"></a>Comentarios  
 Mediante el uso de `CComboBoxEx` para crear controles de cuadro de cuadro combinado, ya no necesita implementar su propio código de dibujo de la imagen. En su lugar, utilice `CComboBoxEx` para el acceso a las imágenes de una lista de imágenes.  
  
## <a name="image-list-support"></a>Compatibilidad con listas de imágenes  
 En un cuadro combinado estándar, el propietario del cuadro combinado es responsable de dibujar una imagen mediante la creación del cuadro combinado como un control dibujado por el propietario. Al usar `CComboBoxEx`, no es necesario establecer los estilos de dibujo **CBS_OWNERDRAWFIXED** y **CBS_HASSTRINGS** porque ya que están implícitas. De lo contrario, debe escribir código para realizar operaciones de dibujo. Un `CComboBoxEx` control admite hasta tres imágenes por artículo: uno para un estado seleccionado, uno para un estado no seleccionado y otro para una imagen de superposición.  
  
## <a name="styles"></a>Estilos  
 `CComboBoxEx`es compatible con los estilos **CBS_SIMPLE**, **CBS_DROPDOWN**, **CBS_DROPDOWNLIST**, y **WS_CHILD**. Se omiten todos los demás estilos pasados al crear la ventana de control. Después de crea la ventana, puede proporcionar estilos de cuadro otro combinado llamando el `CComboBoxEx` función miembro [SetExtendedStyle](#setextendedstyle). Con estos estilos, puede:  
  
-   Búsquedas de cadenas de conjunto en la lista distinga mayúsculas de minúsculas.  
  
-   Crear un control de cuadro combinado que usa la barra diagonal ('/'), barra diagonal inversa ('\\') y el período ('. ') caracteres como delimitadores de palabras. Esto permitirá a los usuarios saltar palabras, usando el método abreviado de teclado CTRL + FLECHA.  
  
-   Establezca al cuadro combinado del control de cuadro para mostrar o no una imagen. Si no se muestra ninguna imagen, el cuadro combinado puede quitar la sangría de texto que se adapta a una imagen.  
  
-   Crear un control de cuadro combinado estrecha, incluidos tamaño por lo que se recorta el cuadro combinado más amplio que contiene.  
  
 Estos indicadores de estilo se describen más detalladamente en [utilizar CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## <a name="item-retention-and-callback-item-attributes"></a>Retención de elementos y atributos del elemento de devolución de llamada  
 Información de elemento, como índices de los elementos y las imágenes, los valores de sangría y cadenas de texto, se almacena en la estructura de Win32 [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. La estructura también contiene a miembros que corresponden a las marcas de devolución de llamada.  
  
 Para obtener información conceptual detallada, vea [utilizar CComboBoxEx](../../mfc/using-ccomboboxex.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CComboBox](../../mfc/reference/ccombobox-class.md)  
  
 `CComboBoxEx`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="ccomboboxex"></a>CComboBoxEx::CComboBoxEx  
 Llame a esta función miembro para crear un `CComboBoxEx` objeto.  
  
```  
CComboBoxEx();
```  
  
##  <a name="create"></a>CComboBoxEx::Create  
 Crea el cuadro combinado y lo adjunta a la `CComboBoxEx` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica la combinación de estilos de cuadro combinado aplicados al cuadro combinado. Consulte **comentarios** a continuación para obtener más información acerca de los estilos.  
  
 `rect`  
 Una referencia a un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que es la posición y el tamaño del cuadro combinado.  
  
 `pParentWnd`  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto de la ventana primaria del cuadro combinado (normalmente un `CDialog`). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del cuadro combinado  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el objeto se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CComboBoxEx` objeto en dos pasos:  
  
1.  Llame a [CComboBoxEx](#ccomboboxex) para construir un `CComboBoxEx` objeto.  
  
2.  Llame a esta función miembro, que crea el cuadro combinado de Windows extendido y lo adjunta a la `CComboBoxEx` objeto.  
  
 Cuando se llama a **crear**, MFC inicializa los controles comunes.  
  
 Cuando se crea el cuadro combinado, puede especificar uno o todos los siguientes estilos de cuadro combinado:  
  
- **CBS_SIMPLE**  
  
- **CBS_DROPDOWN**  
  
- **CBS_DROPDOWNLIST**  
  
- **CBS_AUTOHSCROLL**  
  
- **WS_CHILD**  
  
 Se omiten todos los demás estilos pasados al crear la ventana. El **ComboBoxEx** control también admite los estilos extendidos que proporcionan características adicionales. Estos estilos se describen en [ComboBoxEx controlar estilos extendidos](http://msdn.microsoft.com/library/windows/desktop/bb775742), en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Establecer estos estilos mediante una llamada a [SetExtendedStyle](#setextendedstyle).  
  
 Si desea utilizar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de **crear**.  
  
##  <a name="createex"></a>CComboBoxEx::CreateEx  
 Llame a esta función para crear un control de cuadro combinado extendido (una ventana secundaria) y asociarla con el `CComboBoxEx` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `dwStyle`  
 Estilo del control de cuadro combinado. Consulte [crear](#create) para obtener una lista de estilos.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente `pParentWnd`.  
  
 `pParentWnd`  
 Puntero a la ventana que es principal el control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Utilice `CreateEx` en lugar de **crear** para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
 `CreateEx`crea el control con los estilos extendidos de Windows especificados por `dwExStyle`. Debe establecer los estilos extendidos específicos a un control de cuadro combinado extendido mediante [SetExtendedStyle](#setextendedstyle). Por ejemplo, utilice `CreateEx` para establecer estos estilos como **WS_EX_CONTEXTHELP**, pero usar `SetExtendedStyle` para establecer estos estilos como **CBES_EX_CASESENSITIVE**. Para obtener más información, consulte los estilos que se describen en el tema [estilos extendidos de Control ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775742) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="deleteitem"></a>CComboBoxEx::DeleteItem  
 Quita un elemento de un **ComboBoxEx** control.  
  
```  
int DeleteItem(int iIndex);
```  
  
### <a name="parameters"></a>Parámetros  
 `iIndex`  
 Índice de base cero del elemento que se va a quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos que quedan en el control. Si `iIndex` no es válido, la función devuelve **CB_ERR**.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa la funcionalidad del mensaje [CBEM_DELETEITEM](http://msdn.microsoft.com/library/windows/desktop/bb775768), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Cuando se llama a DeleteItem, un [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje con **CBEN_DELETEITEM se** se enviará una notificación a la ventana primaria.  
  
##  <a name="getcomboboxctrl"></a>CComboBoxEx::GetComboBoxCtrl  
 Llame a esta función miembro para obtener un puntero a un control de cuadro combinado en un `CComboBoxEx` objeto.  
  
```  
CComboBox* GetComboBoxCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CComboBox` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El `CComboBoxEx` control consta de una ventana primaria, que encapsula un `CComboBox`.  
  
 La `CComboBox` objeto al que señala el valor devuelto es un objeto temporal y se destruye durante el tiempo de procesamiento inactivo siguiente.  
  
##  <a name="geteditctrl"></a>CComboBoxEx::GetEditCtrl  
 Llame a esta función miembro para obtener un puntero al control de edición de un cuadro combinado.  
  
```  
CEdit* GetEditCtrl();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CEdit](../../mfc/reference/cedit-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Un `CComboBoxEx` control utiliza un cuadro de edición cuando se crea con el **CBS_DROPDOWN** estilo.  
  
 La `CEdit` objeto al que señala el valor devuelto es un objeto temporal y se destruye durante el tiempo de procesamiento inactivo siguiente.  
  
##  <a name="getextendedstyle"></a>CComboBoxEx::GetExtendedStyle  
 Llame a esta función miembro para obtener los estilos extendidos utilizados para un `CComboBoxEx` control.  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `DWORD` valor que contiene los estilos extendidos que se usan para el control de cuadro combinado.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [estilos extendidos de Control ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775742) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de estos estilos.  
  
##  <a name="getimagelist"></a>CComboBoxEx::GetImageList  
 Llame a esta función miembro para obtener un puntero a la lista de imágenes que se usa un `CComboBoxEx` control.  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto. Si se produce un error, esta función miembro devuelve **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 La `CImageList` objeto al que señala el valor devuelto es un objeto temporal y se destruye durante el tiempo de procesamiento inactivo siguiente.  
  
##  <a name="getitem"></a>CComboBoxEx:: GetItem  
 Recupera información de artículos un determinado **ComboBoxEx** elemento.  
  
```  
BOOL GetItem(COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCBItem`  
 Un puntero a un [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) estructura que recibirá la información del artículo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa la funcionalidad del mensaje [CBEM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775779), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="haseditchanged"></a>CComboBoxEx::HasEditChanged  
 Determina si el usuario ha cambiado el contenido de la **ComboBoxEx** editar control escribiendo.  
  
```  
BOOL HasEditChanged();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el usuario ha escrito en el cuadro de edición del control; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa la funcionalidad del mensaje [CBEM_HASEDITCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb775782), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="insertitem"></a>CComboBoxEx:: InsertItem  
 Inserta un nuevo elemento en una **ComboBoxEx** control.  
  
```  
int InsertItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCBItem`  
 Un puntero a un [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) estructura que recibirá la información del artículo. Esta estructura contiene valores de indicador de devolución de llamada para el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice donde se insertó el nuevo elemento si es correcto; de lo contrario, devuelve-1.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se llama a `InsertItem`, [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583) mensaje con [CBEN_INSERTITEM se](http://msdn.microsoft.com/library/windows/desktop/bb775764) se enviará una notificación a la ventana primaria.  
  
##  <a name="setextendedstyle"></a>CComboBoxEx::SetExtendedStyle  
 Llame a esta función miembro para establecer los estilos extendidos utilizados para un cuadro combinado extendido de control.  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,  
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExMask`  
 Un `DWORD` valor que indica qué estilos en `dwExStyles` a verse afectado. Sólo los estilos extendidos en `dwExMask` se van a cambiar. Todos los demás estilos se conservará tal cual. Si este parámetro es cero, entonces todos los estilos en `dwExStyles` se verá afectado.  
  
 `dwExStyles`  
 Un `DWORD` estilos extendidos para establecer el control de control de valor que contiene el cuadro combinado.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `DWORD` valor que contiene los estilos extendidos utilizados previamente para el control.  
  
### <a name="remarks"></a>Comentarios  
 Consulte [estilos extendidos de Control ComboBoxEx](http://msdn.microsoft.com/library/windows/desktop/bb775742) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de estos estilos.  
  
 Para crear un cuadro combinado extendido control con los estilos extendidos de windows, use [CreateEx](#createex).  
  
##  <a name="setimagelist"></a>CComboBoxEx:: SetImageList  
 Establece una lista de imágenes para un **ComboBoxEx** control.  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>Parámetros  
 `pImageList`  
 Un puntero a un `CImageList` objeto que contiene las imágenes que se utilizan con el `CComboBoxEx` control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto que contiene las imágenes utilizadas anteriormente por el `CComboBoxEx` control. **NULL** si previamente se ha establecido ninguna lista de imágenes.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa la funcionalidad del mensaje [CBEM_SETIMAGELIST](http://msdn.microsoft.com/library/windows/desktop/bb775787), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Si cambia el alto del control de edición predeterminado, llame a la función de Win32 [SetWindowPos](http://msdn.microsoft.com/library/windows/desktop/ms633545) para cambiar el tamaño de su control después de llamar a `SetImageList`, o no se mostrarán correctamente.  
  
 La `CImageList` objeto al que señala el valor devuelto es un objeto temporal y se destruye durante el tiempo de procesamiento inactivo siguiente.  
  
##  <a name="setitem"></a>CComboBoxEx:: SetItem  
 Establece los atributos de un elemento en un **ComboBoxEx** control.  
  
```  
BOOL SetItem(const COMBOBOXEXITEM* pCBItem);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCBItem`  
 Un puntero a un [COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) estructura que recibirá la información del artículo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa la funcionalidad del mensaje [CBEM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb775788), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setwindowtheme"></a>CComboBoxEx::SetWindowTheme  
 Establece el estilo visual el total combinado de control de cuadro.  
  
```  
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```  
  
### <a name="parameters"></a>Parámetros  
 `pszSubAppName`  
 Un puntero a una cadena Unicode que contiene el estilo visual de cuadro combinado extendido para establecer.  
  
### <a name="return-value"></a>Valor devuelto  
 No se utiliza el valor devuelto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [CBEM_SETWINDOWTHEME](http://msdn.microsoft.com/library/windows/desktop/bb775790) de mensajes, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Este ejemplo de MFC](../../visual-cpp-samples.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)

