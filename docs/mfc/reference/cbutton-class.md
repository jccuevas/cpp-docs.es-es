---
title: Clase CButton | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
dev_langs:
- C++
helpviewer_keywords:
- CButton class
- checkbox buttons
- pushbuttons
- button control [MFC]
- check boxes, button controls
- button objects (CButton)
- radio buttons, CButton class
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
caps.latest.revision: 19
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 03771a3d0dd2297487953089081893a7c892b321
ms.lasthandoff: 04/04/2017

---
# <a name="cbutton-class"></a>Clase CButton
Proporciona la funcionalidad de los controles de botón de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CButton : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CButton::CButton](#cbutton)|Construye un objeto `CButton`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CButton::Create](#create)|Crea el control de botón de Windows y lo adjunta a la `CButton` objeto.|  
|[CButton::DrawItem](#drawitem)|Invalidación para dibujar un dibujado por el propietario `CButton` objeto.|  
|[CButton::GetBitmap](#getbitmap)|Recupera el identificador del mapa de bits establecidos previamente con [SetBitmap](#setbitmap).|  
|[CButton::GetButtonStyle](#getbuttonstyle)|Recupera información sobre el estilo del control de botón.|  
|[CButton::GetCheck](#getcheck)|Recupera el estado de activación de un control de botón.|  
|[CButton::GetCursor](#getcursor)|Recupera el identificador de la imagen del cursor establecido previamente con [SetCursor](#setcursor).|  
|[CButton::GetIcon](#geticon)|Recupera el identificador del icono establecido previamente con [SetIcon](#seticon).|  
|[CButton::GetIdealSize](#getidealsize)|Recupera el tamaño ideal de control de botón.|  
|[CButton::GetImageList](#getimagelist)|Recupera la lista de imágenes del control de botón.|  
|[CButton::GetNote](#getnote)|Recupera el componente de nota del control de vínculo de comando actual.|  
|[CButton::GetNoteLength](#getnotelength)|Recupera la longitud del texto de la nota para el control de vínculo de comando actual.|  
|[CButton::GetSplitGlyph](#getsplitglyph)|Recupera el glifo asociado al control de botón de división actual.|  
|[CButton::GetSplitImageList](#getsplitimagelist)|Recupera la lista de imágenes para el control de botón de expansión actual.|  
|[CButton::GetSplitInfo](#getsplitinfo)|Recupera la información que define el control de botón de expansión actual.|  
|[CButton::GetSplitSize](#getsplitsize)|Recupera el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.|  
|[CButton::GetSplitStyle](#getsplitstyle)|Recupera los estilos de botón de división que definen el control de botón de expansión actual.|  
|[CButton::GetState](#getstate)|Recupera el estado de activación, el estado de resaltado y el estado del foco de un control de botón.|  
|[CButton::GetTextMargin](#gettextmargin)|Recupera el margen de texto del control de botón.|  
|[CButton:: SetBitmap](#setbitmap)|Especifica un mapa de bits que se mostrará en el botón.|  
|[CButton::SetButtonStyle](#setbuttonstyle)|Cambia el estilo de un botón.|  
|[CButton::SetCheck](#setcheck)|Establece el estado de activación de un control de botón.|  
|[CButton::SetCursor](#setcursor)|Especifica una imagen del cursor que se mostrará en el botón.|  
|[CButton::SetDropDownState](#setdropdownstate)|Establece el estado de la lista desplegable del control de botón de división actual.|  
|[CButton::SetIcon](#seticon)|Especifica el icono que se muestra en el botón.|  
|[CButton::SetImageList](#setimagelist)|Establece la lista de imágenes del control de botón.|  
|[CButton::SetNote](#setnote)|Establece la nota en el control de vínculo de comando actual.|  
|[CButton::SetSplitGlyph](#setsplitglyph)|Asocia un glifo especificado con el control de botón de expansión actual.|  
|[CButton::SetSplitImageList](#setsplitimagelist)|Asocia una lista de imágenes con el control de botón de expansión actual.|  
|[CButton::SetSplitInfo](#setsplitinfo)|Especifica la información que define el control de botón de expansión actual.|  
|[CButton::SetSplitSize](#setsplitsize)|Establece el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.|  
|[CButton::SetSplitStyle](#setsplitstyle)|Establece el estilo del control de botón de división actual.|  
|[CButton::SetState](#setstate)|Establece el estado de un control de botón resaltado.|  
|[CButton::SetTextMargin](#settextmargin)|Establece el margen de texto del control de botón.|  
  
## <a name="remarks"></a>Comentarios  
 Un control de botón es una ventana secundaria pequeño, rectangular que se puede hacer clic y desactivar. Botones pueden utilizarse por sí solas o en grupos y o bien se pueden etiquetar o aparecen sin texto. Normalmente un botón cambia de apariencia cuando el usuario hace clic en él.  
  
 Botones típicos son la casilla de verificación, botón de radio y pulsador. A `CButton` objeto puede ser cualquiera de estos elementos, según la [botón estilo](../../mfc/reference/button-styles.md) especificado en su inicialización, mediante la [crear](#create) función miembro.  
  
 Además, el [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md) deriva de la clase `CButton` admite la creación de controles de botón etiquetados con imágenes de mapa de bits en lugar de texto. Un `CBitmapButton` puede tener los mapas de bits independientes para un botón de la, hacia abajo, centrado y deshabilita los Estados.  
  
 Puede crear un control de botón de una plantilla de cuadro de diálogo o directamente en el código. En ambos casos, llame primero al constructor de `CButton` para construir el `CButton` objeto; a continuación, llamar a la **crear** función de miembro para crear las ventanas de control de botón y adjuntarlo a la `CButton` objeto.  
  
 Construcción puede ser un proceso de un paso en una clase derivada de `CButton`. Escribir un constructor para la clase derivada y llamar a **crear** desde dentro del constructor.  
  
 Si desea controlar los mensajes de notificación de Windows enviados mediante un control de botón a su elemento primario (normalmente una clase derivada de [CDialog](../../mfc/reference/cdialog-class.md)), agregar una función de miembro de entrada y el controlador de mensajes de mapa de mensajes para la clase primaria para cada mensaje.  
  
 Cada entrada de mapa de mensajes tiene el formato siguiente:  
  
 **ON_**Notification **(**`id`, `memberFxn`**)**  
  
 donde `id` especifica el identificador de ventana de secundarios del control que envía la notificación y `memberFxn` es el nombre de la función de miembro primario haya terminado de escribir para controlar la notificación.  
  
 Prototipo de función del elemento primario es el siguiente:  
  
 **afx_msg** `void` `memberFxn` **( );**  
  
 Posibles entradas de mapa de mensajes son los siguientes:  
  
|Entrada de mapa|Envía al elemento primario cuando...|  
|---------------|----------------------------|  
|**ON_BN_CLICKED**|El usuario hace clic en un botón.|  
|**ON_BN_DOUBLECLICKED**|El usuario hace doble clic en un botón.|  
  
 Si crea un `CButton` objeto desde un recurso de cuadro de diálogo, la `CButton` objeto se destruye automáticamente cuando el usuario cierra el cuadro de diálogo.  
  
 Si crea un `CButton` de objeto dentro de una ventana, puede que necesite destruirlo. Si crea el `CButton` objeto en el montón mediante el uso de la **nueva** función, se debe llamar a **eliminar** del objeto que se va a destruir cuando el usuario cierra las ventanas de control de botón. Si crea la `CButton` objeto en la pila, o bien está incrustado en el objeto de cuadro de diálogo primario, se destruye automáticamente.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CButton`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cbutton"></a>CButton::CButton  
 Construye un objeto `CButton`.  
  
```  
CButton();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton n.º 1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]  
  
##  <a name="create"></a>CButton::Create  
 Crea el control de botón de Windows y lo adjunta a la `CButton` objeto.  
  
```  
virtual BOOL Create(
    LPCTSTR lpszCaption,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszCaption`  
 Especifica el texto del control de botón.  
  
 `dwStyle`  
 Especifica el estilo del control de botón. Aplicar cualquier combinación de [estilos de botón](../../mfc/reference/button-styles.md) al botón.  
  
 `rect`  
 Especifica el tamaño y la posición del control de botón. Puede ser un `CRect` objeto o un `RECT` estructura.  
  
 `pParentWnd`  
 Especifica la ventana del elemento primario del control de botón, normalmente un `CDialog`. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control de botón  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CButton` objeto en dos pasos. En primer lugar, llame al constructor y, a continuación, llame a **crear**, que crea el control de botón de Windows y lo adjunta a la `CButton` objeto.  
  
 Si el **WS_VISIBLE** estilo se proporciona, Windows envía el control de botón de todos los mensajes necesarios para activar y mostrar el botón.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/window-styles.md) a un control de botón:  
  
- **WS_CHILD** siempre  
  
- **WS_VISIBLE** normalmente  
  
- **WS_DISABLED** rara vez  
  
- **WS_GROUP** a controles de grupo  
  
- **WS_TABSTOP** debe incluir el botón en el orden de tabulación  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton n.º 2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]  
  
##  <a name="drawitem"></a>CButton::DrawItem  
 Lo llama el marco de trabajo cuando ha cambiado la apariencia de un botón dibujado por el propietario.  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpDrawItemStruct`  
 Un puntero largo a una [DRAWITEMSTRUCT](../../mfc/reference/drawitemstruct-structure.md) estructura. La estructura contiene información sobre el elemento que se va a dibujar y el tipo de dibujo necesaria.  
  
### <a name="remarks"></a>Comentarios  
 Tiene un botón dibujado por el propietario del **BS_OWNERDRAW** conjunto de estilo. Reemplace esta función miembro para implementar el dibujo de un dibujado por el propietario `CButton` objeto. La aplicación debe restaurar todos los objetos de interfaz (GDI) de dispositivo de gráficos seleccionados para proporciona el contexto de presentación en `lpDrawItemStruct` antes del miembro función finaliza.  
  
 Consulte también la [BS_](../../mfc/reference/button-styles.md) valores de estilo.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton 3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]  
  
##  <a name="getbitmap"></a>CButton::GetBitmap  
 Llame a esta función miembro para obtener el identificador de un mapa de bits establecido previamente con [SetBitmap](#setbitmap), que está asociado con un botón.  
  
```  
HBITMAP GetBitmap() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador a un mapa de bits. **NULL** si previamente no se especifica ningún mapa de bits.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="getbuttonstyle"></a>CButton::GetButtonStyle  
 Recupera información sobre el estilo del control de botón.  
  
```  
UINT GetButtonStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve los estilos de botón de este `CButton` objeto. Esta función devuelve solo el [BS_](../../mfc/reference/button-styles.md) valores de estilo, no en cualquiera de los demás estilos de ventana.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton Nº 5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="getcheck"></a>CButton::GetCheck  
 Recupera el estado de activación de un botón de radio o la casilla de verificación.  
  
```  
int GetCheck() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto de un control de botón que se creó con la **BS_AUTOCHECKBOX**, **BS_AUTORADIOBUTTON**, **BS_AUTO3STATE**, **BS_CHECKBOX**, **BS_RADIOBUTTON**, o **BS_3STATE** estilo es uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|**BST_UNCHECKED**|Estado de los botones está desactivada.|  
|**BST_CHECKED**|Se comprueba el estado de los botones.|  
|**BST_INDETERMINATE**|Estado de los botones es indeterminado (se aplica sólo si el botón tiene el **BS_3STATE** o **BS_AUTO3STATE** estilo).|  
  
 Si el botón tiene cualquier otro estilo, el valor devuelto es **BST_UNCHECKED**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="getcursor"></a>CButton::GetCursor  
 Llame a esta función miembro para obtener el identificador de un cursor, establecido previamente con [SetCursor](#setcursor), que está asociado con un botón.  
  
```  
HCURSOR GetCursor();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador de una imagen del cursor. **NULL** si previamente no se especifica ningún cursor.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="geticon"></a>CButton::GetIcon  
 Llame a esta función miembro para obtener el identificador de un conjunto de iconos, previamente con [SetIcon](#seticon), que está asociado con un botón.  
  
```  
HICON GetIcon() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador de un icono. **NULL** si previamente se especifica ningún icono.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CButton::GetIdealSize  
 Recupera el tamaño ideal para el control de botón.  
  
```  
BOOL GetIdealSize(SIZE* psize);
```  
  
### <a name="parameters"></a>Parámetros  
 *psize*  
 Un puntero al tamaño actual del botón.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la **BCM_GETIDEALSIZE** de mensajes, como se describe en el [botones](http://msdn.microsoft.com/library/windows/desktop/bb775943) sección de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getimagelist"></a>CButton::GetImageList  
 Llamar a este método para obtener la lista de imágenes desde el control de botón.  
  
```  
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parámetros  
 `pbuttonImagelist`  
 Un puntero a la lista de imágenes de la `CButton` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la **BCM_GETIMAGELIST** de mensajes, como se describe en el [botones](http://msdn.microsoft.com/library/windows/desktop/bb775943) sección de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getnote"></a>CButton::GetNote  
 Recupera el texto de la nota asociado al control de vínculo de comando actual.  
  
```  
CString GetNote() const;  
  
BOOL GetNote(
    LPTSTR lpszNote,   
    UINT* cchNote) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `lpszNote`|Puntero a un búfer, que el llamador es responsable de asignar y desasignar. Si el valor devuelto es `true`, el búfer contiene el texto de la nota que está asociado con el control de vínculo de comando actual; en caso contrario, el búfer se ha modificado.|  
|[in, out] `cchNote`|Un puntero a una variable de entero sin signo.<br /><br /> Cuando se llama a este método, la variable contiene el tamaño del búfer especificado por el `lpszNote` parámetro.<br /><br /> Cuando se devuelve este método, si el valor devuelto es `true` la variable contiene el tamaño de la nota asociada con el control de vínculo de comando actual. Si el valor devuelto es `false`, la variable contiene el tamaño del búfer necesario para contener la nota.|  
  
### <a name="return-value"></a>Valor devuelto  
 En la primera sobrecarga, un [CString](../../atl-mfc-shared/using-cstring.md) objeto que contiene el texto de la nota asociado al control de vínculo de comando actual.  
  
 O bien  
  
 En la segunda sobrecarga, `true` si este método es correcto; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_COMMANDLINK` o `BS_DEFCOMMANDLINK`.  
  
 Este método envía el [BCM_GETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775965) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getnotelength"></a>CButton::GetNoteLength  
 Recupera la longitud del texto de la nota para el control de vínculo de comando actual.  
  
```  
UINT GetNoteLength() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud del texto de nota, de caracteres Unicode de 16 bits, para el control de vínculo de comando actual.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_COMMANDLINK` o `BS_DEFCOMMANDLINK`.  
  
 Este método envía el [BCM_GETNOTELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb775967) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getsplitglyph"></a>CButton::GetSplitGlyph  
 Recupera el glifo asociado al control de botón de división actual.  
  
```  
TCHAR GetSplitGlyph() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El carácter de glifo asociado con el control de botón de expansión actual.  
  
### <a name="remarks"></a>Comentarios  
 Un glifo es la representación física de un carácter en una fuente concreta. Por ejemplo, un control de botón de división se puede decorar con el glifo del carácter de marca de verificación de Unicode (2713).  
  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_GLYPH` marca y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Cuando se devuelve la función de mensaje, este método recupera el glifo de la `himlGlyph` miembro de la estructura.  
  
##  <a name="getsplitimagelist"></a>CButton::GetSplitImageList  
 Recupera el [lista de imágenes](../../mfc/reference/cimagelist-class.md) para el control de botón de expansión actual.  
  
```  
CImageList* GetSplitImageList() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_IMAGE` marca y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Cuando se devuelve la función de mensaje, este método recupera la lista de imágenes desde el `himlGlyph` miembro de la estructura.  
  
##  <a name="getsplitinfo"></a>CButton::GetSplitInfo  
 Recupera los parámetros que determinan cómo Windows quien dibuja el control de botón de expansión actual.  
  
```  
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `pInfo`|Puntero a un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura que recibe información sobre el control de botón de expansión actual. El llamador es responsable de asignar la estructura.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Este método envía el [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getsplitsize"></a>CButton::GetSplitSize  
 Recupera el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.  
  
```  
BOOL GetSplitSize(LPSIZE pSize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `pSize`|Puntero a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que recibe la descripción de un rectángulo.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Cuando se expande el control de botón de expansión, puede mostrar un componente de la lista desplegable, como un control de lista o control de paginación. Este método recupera el rectángulo delimitador que contiene el componente de la lista desplegable.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_SIZE` marca y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Cuando se devuelve la función de mensaje, este método recupera el rectángulo delimitador de la `size` miembro de la estructura.  
  
##  <a name="getsplitstyle"></a>CButton::GetSplitStyle  
 Recupera los estilos de botón de división que definen el control de botón de expansión actual.  
  
```  
UINT GetSplitStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una combinación bit a bit de los estilos de botón de división. Para obtener más información, consulte el `uSplitStyle` miembro de la [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Los estilos de botón de división especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows quien dibuja un icono de botón de división.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_STYLE` marca y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Cuando se devuelve la función de mensaje, este método recupera los estilos de botón de división de la `uSplitStyle` miembro de la estructura.  
  
##  <a name="getstate"></a>CButton::GetState  
 Recupera el estado de un control de botón.  
  
```  
UINT GetState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un campo de bits que contiene la combinación de valores que indican el estado actual de un control de botón. En la tabla siguiente se enumera los valores posibles.  
  
|Estado de los botones|Valor|Descripción|  
|------------------|-----------|-----------------|  
|`BST_UNCHECKED`|0x0000|El estado inicial.|  
|`BST_CHECKED`|0 x 0001|El control de botón está activado.|  
|`BST_INDETERMINATE`|0 x 0002|El estado indeterminado (sólo es posible cuando el control de botón tiene tres estados).|  
|`BST_PUSHED`|0 x 0004|El control de botón está presionado.|  
|`BST_FOCUS`|0 x 0008|El control de botón tiene el foco.|  
  
### <a name="remarks"></a>Comentarios  
 Un control de botón con el `BS_3STATE` o `BS_AUTO3STATE` estilo de botón crea una casilla de verificación que tiene un estado terceros que se denomina al estado indeterminado. El estado indeterminado indica que la casilla de verificación está ni activada ni desactivada.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton n.º 9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="gettextmargin"></a>CButton::GetTextMargin  
 Llamar a este método para obtener el margen de texto de la `CButton` objeto.  
  
```  
BOOL GetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parámetros  
 `pmargin`  
 Un puntero al margen de texto de la `CButton` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el margen de texto.  
  
### <a name="remarks"></a>Comentarios  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la **BCM_GETTEXTMARGIN** de mensajes, como se describe en el [botones](http://msdn.microsoft.com/library/windows/desktop/bb775943) sección de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setbitmap"></a>CButton:: SetBitmap  
 Llame a esta función miembro para asociar un nuevo mapa de bits con el botón.  
  
```  
HBITMAP SetBitmap(HBITMAP hBitmap);
```  
  
### <a name="parameters"></a>Parámetros  
 `hBitmap`  
 El identificador de un mapa de bits.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de un mapa de bits asociado anteriormente con el botón.  
  
### <a name="remarks"></a>Comentarios  
 El mapa de bits se colocarán automáticamente en el botón, el centro de forma predeterminada. Si el mapa de bits es demasiado grande para el botón, se recortará a cada lado. Puede elegir otras opciones de alineación, incluidas las siguientes:  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que utiliza cuatro mapas de bits por cada botón, `SetBitmap` utiliza sólo un mapa de bits por el botón. Cuando se presiona el botón, aparece el mapa de bits de desplazamiento hacia abajo y a la derecha.  
  
 Usted es responsable de liberar el mapa de bits cuando haya terminado con él.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]  
  
##  <a name="setbuttonstyle"></a>CButton::SetButtonStyle  
 Cambia el estilo de un botón.  
  
```  
void SetButtonStyle(
    UINT nStyle,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStyle`  
 Especifica la [botón estilo](../../mfc/reference/button-styles.md).  
  
 `bRedraw`  
 Especifica si el botón volver a dibujar. Un valor distinto de cero, se vuelve a dibujar el botón. Un valor de 0 no volver a dibujar el botón. Se vuelve a dibujar el botón de forma predeterminada.  
  
### <a name="remarks"></a>Comentarios  
 Use la `GetButtonStyle` función miembro para recuperar el estilo de botón. La palabra de orden inferior del estilo de botón completa es el estilo de botón específico.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton Nº 5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]  
  
##  <a name="setcheck"></a>CButton::SetCheck  
 Establece o restablece el estado de activación de un botón de radio o la casilla de verificación.  
  
```  
void SetCheck(int nCheck);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCheck`  
 Especifica el estado de activación. Este parámetro puede ser uno de los siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|**BST_UNCHECKED**|Establecer el estado de los botones que no está activada.|  
|**BST_CHECKED**|Establecer el estado del botón comprobar.|  
|**BST_INDETERMINATE**|Establecer el estado del botón en indeterminado. Este valor puede usarse sólo si el botón tiene el **BS_3STATE** o **BS_AUTO3STATE** estilo.|  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no tiene ningún efecto en un botón de comando.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]  
  
##  <a name="setcursor"></a>CButton::SetCursor  
 Llame a esta función miembro para asociar un nuevo cursor con el botón.  
  
```  
HCURSOR SetCursor(HCURSOR hCursor);
```  
  
### <a name="parameters"></a>Parámetros  
 `hCursor`  
 El identificador de un cursor.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de un cursor anteriormente asociado con el botón.  
  
### <a name="remarks"></a>Comentarios  
 El cursor se colocarán automáticamente en el botón, el centro de forma predeterminada. Si el cursor es demasiado grande para el botón, se recortará a cada lado. Puede elegir otras opciones de alineación, incluidas las siguientes:  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que utiliza cuatro mapas de bits por cada botón, `SetCursor` utiliza solo un cursor por el botón. Cuando se presiona el botón, aparece el cursor de desplazamiento hacia abajo y a la derecha.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]  
  
##  <a name="setdropdownstate"></a>CButton::SetDropDownState  
 Establece el estado de la lista desplegable del control de botón de división actual.  
  
```  
BOOL SetDropDownState(BOOL fDropDown);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `fDropDown`|`true`Para establecer `BST_DROPDOWNPUSHED` estado; en caso contrario, `false`.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Un control de botón de división tiene un estilo de `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON` y consta de un botón y una flecha de lista desplegable a su derecha. Para obtener más información, consulte [estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb775951). Por lo general, el estado de la lista desplegable se establece cuando el usuario hace clic en la flecha de lista desplegable. Utilice este método para establecer mediante programación el estado de la lista desplegable del control. La flecha de lista desplegable se dibuja sombreada para indicar el estado.  
  
 Este método envía el [BCM_SETDROPDOWNSTATE](http://msdn.microsoft.com/library/windows/desktop/bb775973) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_splitButton`, que se usa para obtener acceso mediante programación el control de botón de expansión. Esta variable se usa en el ejemplo siguiente.  
  
 [!code-cpp[NVC_MFC_CButton_s1 n.º 1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el estado del control de botón de división para indicar que se inserta la flecha de lista desplegable.  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]  
  
##  <a name="setelevationrequired"></a>CButton::SetElevationRequired  
 Establece el estado del control de botón actual a `elevation required`, que es necesario para el control mostrar un icono de seguridad con privilegios elevados.  
  
```  
BOOL SetElevationRequired(BOOL fElevationRequired);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `fElevationRequired`|`true`Para establecer `elevation required` estado; en caso contrario, `false`.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Si un control de botón o comando de link requiere el permiso de seguridad con privilegios elevados para realizar una acción, establecer el control `elevation required` estado. Como consecuencia, Windows muestra el icono de escudo de Control de cuentas de usuario (UAC) en el control. Para obtener más información, vea "User Account Control" en [MSDN](http://go.microsoft.com/fwlink/linkid=18507).  
  
 Este método envía el [BCM_SETSHIELD](http://msdn.microsoft.com/library/windows/desktop/bb775979) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="seticon"></a>CButton::SetIcon  
 Llame a esta función miembro para asociar un icono nuevo con el botón.  
  
```  
HICON SetIcon(HICON hIcon);
```  
  
### <a name="parameters"></a>Parámetros  
 `hIcon`  
 El identificador de un icono.  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador de un icono asociado anteriormente con el botón.  
  
### <a name="remarks"></a>Comentarios  
 El icono se colocarán automáticamente en el botón, el centro de forma predeterminada. Si el icono es demasiado grande para el botón, se recortará a cada lado. Puede elegir otras opciones de alineación, incluidas las siguientes:  
  
- **BS_TOP**  
  
- **BS_LEFT**  
  
- **BS_RIGHT**  
  
- **BS_CENTER**  
  
- **BS_BOTTOM**  
  
- **BS_VCENTER**  
  
 A diferencia de [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md), que utiliza cuatro mapas de bits por cada botón, `SetIcon` utiliza un único icono por el botón. Cuando se presiona el botón, aparece el icono de desplazamiento hacia abajo y a la derecha.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton #8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]  
  
##  <a name="setimagelist"></a>CButton::SetImageList  
 Llamar a este método para establecer la lista de imágenes de la `CButton` objeto.  
  
```  
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```  
  
### <a name="parameters"></a>Parámetros  
 `pbuttonImagelist`  
 Un puntero a la nueva lista de imágenes.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **TRUE** se ejecuta correctamente, **FALSE** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la **BCM_SETIMAGELIST** de mensajes, como se describe en el [botones](http://msdn.microsoft.com/library/windows/desktop/bb775943) sección de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setnote"></a>CButton::SetNote  
 Establece el texto de la nota para el control de vínculo de comando actual.  
  
```  
BOOL SetNote(LPCTSTR lpszNote);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `lpszNote`|Puntero a una cadena Unicode que se establece como el texto de la nota para el control de vínculo de comando.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_COMMANDLINK` o `BS_DEFCOMMANDLINK`.  
  
 Este método envía el [BCM_SETNOTE](http://msdn.microsoft.com/library/windows/desktop/bb775977) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_cmdLink`, que se usa para obtener acceso mediante programación el control de vínculo de comando. Esta variable se usa en el ejemplo siguiente.  
  
 [!code-cpp[NVC_MFC_CButton_s1 n.º 1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el texto de la nota para el control de vínculo de comando.  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]  
  
##  <a name="setsplitglyph"></a>CButton::SetSplitGlyph  
 Asocia un glifo especificado con el control de botón de expansión actual.  
  
```  
BOOL SetSplitGlyph(TCHAR chGlyph);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `chGlyph`|Un carácter que especifica el glifo que se va a usar como la flecha de lista desplegable del botón de división.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles que tienen el estilo de botón `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Un glifo es la representación física de un carácter en una fuente concreta. El `chGlyph` no se utiliza como el glifo de parámetro, pero en su lugar se utiliza para seleccionar un glifo de un conjunto de glifos definido por el sistema. El glifo de la flecha de lista desplegable predeterminado especificado por un carácter '6' y parece el triángulo negro abajo hacia (25BC) de caracteres Unicode.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_GLYPH` marca y el `himlGlyph` miembro con el `chGlyph` parámetro y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setsplitimagelist"></a>CButton::SetSplitImageList  
 Asocia un [lista de imágenes](../../mfc/reference/cimagelist-class.md) con el control de botón de expansión actual.  
  
```  
BOOL SetSplitImageList(CImageList* pSplitImageList);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pSplitImageList`|Puntero a un [CImageList](../../mfc/reference/cimagelist-class.md) objeto que se va a asignar para el control de botón de expansión actual.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_IMAGE` marca y el `himlGlyph` miembro con el `pSplitImageList` parámetro y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setsplitinfo"></a>CButton::SetSplitInfo  
 Especifica los parámetros que determinan cómo Windows quien dibuja el control de botón de expansión actual.  
  
```  
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pInfo`|Puntero a un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura que define el control de botón de expansión actual.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Este método envía el [BCM_SETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775981) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_splitButton`, que se usa para obtener acceso mediante programación el control de botón de expansión.  
  
 [!code-cpp[NVC_MFC_CButton_s1 n.º 1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se cambia el glifo que se usa para la flecha de lista desplegable del botón de división. En el ejemplo se sustituye un glifo de triángulo hacia arriba para el glifo de triángulo hacia abajo de forma predeterminada. El glifo que se muestra depende de los caracteres que se especifican en el `himlGlyph` miembro de la `BUTTON_SPLITINFO` estructura. El glifo de triángulo hacia abajo se especifica mediante un carácter ' 6 'y el glifo de triángulo hacia arriba se especifica un carácter ' 5'. Para la comparación, vea el método conveniencia, [CButton::SetSplitGlyph](#setsplitglyph).  
  
 [!code-cpp[NVC_MFC_CButton_s&#1;4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]  
  
##  <a name="setsplitsize"></a>CButton::SetSplitSize  
 Establece el rectángulo delimitador del componente de lista desplegable del control de botón de división actual.  
  
```  
BOOL SetSplitSize(LPSIZE pSize);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `pSize`|Puntero a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que describe un rectángulo delimitador.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Cuando se expande el control de botón de expansión, puede mostrar un componente de la lista desplegable, como un control de lista o control de paginación. Este método especifica el tamaño del rectángulo delimitador que contiene el componente de la lista desplegable.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_SIZE` marca y el `size` miembro con el `pSize` parámetro y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_splitButton`, que se usa para obtener acceso mediante programación el control de botón de expansión. Esta variable se usa en el ejemplo siguiente.  
  
 [!code-cpp[NVC_MFC_CButton_s1 n.º 1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se duplica el tamaño de la flecha de lista desplegable del botón de división.  
  
 [!code-cpp[NVC_MFC_CButton_s1 Nº 5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]  
  
##  <a name="setsplitstyle"></a>CButton::SetSplitStyle  
 Establece el estilo del control de botón de división actual.  
  
```  
BOOL SetSplitStyle(UINT uSplitStyle);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `uSplitStyle`|Una combinación bit a bit de los estilos de botón de división. Para obtener más información, consulte el `uSplitStyle` miembro de la [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; en caso contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Utilice este método solo con controles cuyo estilo de botón es `BS_SPLITBUTTON` o `BS_DEFSPLITBUTTON`.  
  
 Los estilos de botón de división especifican la alineación, la relación de aspecto y el formato gráfico con el que Windows quien dibuja un icono de botón de división. Para obtener más información, consulte el `uSplitStyle` miembro de la [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura.  
  
 Este método inicializa la `mask` miembro de un [BUTTON_SPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775955) estructura con la `BCSIF_STYLE` marca y el `uSplitStyle` miembro con el `uSplitStyle` parámetro y, a continuación, envía la estructura en la [BCM_GETSPLITINFO](http://msdn.microsoft.com/library/windows/desktop/bb775969) mensaje que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_splitButton`, que se usa para obtener acceso mediante programación el control de botón de expansión.  
  
 [!code-cpp[NVC_MFC_CButton_s1 n.º 1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el estilo de la flecha de lista desplegable del botón de división. El `BCSS_ALIGNLEFT` estilo muestra la flecha situada a la izquierda del botón y la `BCSS_STRETCH` estilo conserva las proporciones de la flecha de lista desplegable cuando cambia el tamaño del botón.  
  
 [!code-cpp[NVC_MFC_CButton_s1 3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]  
  
##  <a name="setstate"></a>CButton::SetState  
 Establece si un control de botón está resaltado o no.  
  
```  
void SetState(BOOL bHighlight);
```  
  
### <a name="parameters"></a>Parámetros  
 *bHighlight*  
 Especifica si el botón se resalta. Un valor distinto de cero resalta el botón; un valor de 0, quita cualquier resaltado.  
  
### <a name="remarks"></a>Comentarios  
 Resaltar afecta a la parte exterior de un control de botón. No tiene ningún efecto en el estado de activación de un botón de radio o la casilla de verificación.  
  
 Un control de botón se resalta automáticamente cuando el usuario hace clic en y mantiene presionado el botón primario del mouse. El resaltado se quita cuando el usuario suelta el botón del mouse.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CButton n.º 9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]  
  
##  <a name="settextmargin"></a>CButton::SetTextMargin  
 Llamar a este método para establecer el margen de texto de la `CButton` objeto.  
  
```  
BOOL SetTextMargin(RECT* pmargin);
```  
  
### <a name="parameters"></a>Parámetros  
 `pmargin`  
 Un puntero al margen de texto nuevo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la **BCM_SETTEXTMARGIN** de mensajes, como se describe en el [botones](http://msdn.microsoft.com/library/windows/desktop/bb775943) sección de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CComboBox (clase)](../../mfc/reference/ccombobox-class.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CListBox (clase)](../../mfc/reference/clistbox-class.md)   
 [Clase CScrollBar](../../mfc/reference/cscrollbar-class.md)   
 [Clase CStatic](../../mfc/reference/cstatic-class.md)   
 [Clase CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)   
 [CDialog (clase)](../../mfc/reference/cdialog-class.md)

