---
title: CRichEditCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CRichEditCtrl
- AFXCMN/CRichEditCtrl
- AFXCMN/CRichEditCtrl::CRichEditCtrl
- AFXCMN/CRichEditCtrl::CanPaste
- AFXCMN/CRichEditCtrl::CanRedo
- AFXCMN/CRichEditCtrl::CanUndo
- AFXCMN/CRichEditCtrl::CharFromPos
- AFXCMN/CRichEditCtrl::Clear
- AFXCMN/CRichEditCtrl::Copy
- AFXCMN/CRichEditCtrl::Create
- AFXCMN/CRichEditCtrl::CreateEx
- AFXCMN/CRichEditCtrl::Cut
- AFXCMN/CRichEditCtrl::DisplayBand
- AFXCMN/CRichEditCtrl::EmptyUndoBuffer
- AFXCMN/CRichEditCtrl::FindText
- AFXCMN/CRichEditCtrl::FindWordBreak
- AFXCMN/CRichEditCtrl::FormatRange
- AFXCMN/CRichEditCtrl::GetCharPos
- AFXCMN/CRichEditCtrl::GetDefaultCharFormat
- AFXCMN/CRichEditCtrl::GetEventMask
- AFXCMN/CRichEditCtrl::GetFirstVisibleLine
- AFXCMN/CRichEditCtrl::GetIRichEditOle
- AFXCMN/CRichEditCtrl::GetLimitText
- AFXCMN/CRichEditCtrl::GetLine
- AFXCMN/CRichEditCtrl::GetLineCount
- AFXCMN/CRichEditCtrl::GetModify
- AFXCMN/CRichEditCtrl::GetOptions
- AFXCMN/CRichEditCtrl::GetParaFormat
- AFXCMN/CRichEditCtrl::GetPunctuation
- AFXCMN/CRichEditCtrl::GetRect
- AFXCMN/CRichEditCtrl::GetRedoName
- AFXCMN/CRichEditCtrl::GetSel
- AFXCMN/CRichEditCtrl::GetSelectionCharFormat
- AFXCMN/CRichEditCtrl::GetSelectionType
- AFXCMN/CRichEditCtrl::GetSelText
- AFXCMN/CRichEditCtrl::GetTextLength
- AFXCMN/CRichEditCtrl::GetTextLengthEx
- AFXCMN/CRichEditCtrl::GetTextMode
- AFXCMN/CRichEditCtrl::GetTextRange
- AFXCMN/CRichEditCtrl::GetUndoName
- AFXCMN/CRichEditCtrl::GetWordWrapMode
- AFXCMN/CRichEditCtrl::HideSelection
- AFXCMN/CRichEditCtrl::LimitText
- AFXCMN/CRichEditCtrl::LineFromChar
- AFXCMN/CRichEditCtrl::LineIndex
- AFXCMN/CRichEditCtrl::LineLength
- AFXCMN/CRichEditCtrl::LineScroll
- AFXCMN/CRichEditCtrl::Paste
- AFXCMN/CRichEditCtrl::PasteSpecial
- AFXCMN/CRichEditCtrl::PosFromChar
- AFXCMN/CRichEditCtrl::Redo
- AFXCMN/CRichEditCtrl::ReplaceSel
- AFXCMN/CRichEditCtrl::RequestResize
- AFXCMN/CRichEditCtrl::SetAutoURLDetect
- AFXCMN/CRichEditCtrl::SetBackgroundColor
- AFXCMN/CRichEditCtrl::SetDefaultCharFormat
- AFXCMN/CRichEditCtrl::SetEventMask
- AFXCMN/CRichEditCtrl::SetModify
- AFXCMN/CRichEditCtrl::SetOLECallback
- AFXCMN/CRichEditCtrl::SetOptions
- AFXCMN/CRichEditCtrl::SetParaFormat
- AFXCMN/CRichEditCtrl::SetPunctuation
- AFXCMN/CRichEditCtrl::SetReadOnly
- AFXCMN/CRichEditCtrl::SetRect
- AFXCMN/CRichEditCtrl::SetSel
- AFXCMN/CRichEditCtrl::SetSelectionCharFormat
- AFXCMN/CRichEditCtrl::SetTargetDevice
- AFXCMN/CRichEditCtrl::SetTextMode
- AFXCMN/CRichEditCtrl::SetUndoLimit
- AFXCMN/CRichEditCtrl::SetWordCharFormat
- AFXCMN/CRichEditCtrl::SetWordWrapMode
- AFXCMN/CRichEditCtrl::StopGroupTyping
- AFXCMN/CRichEditCtrl::StreamIn
- AFXCMN/CRichEditCtrl::StreamOut
- AFXCMN/CRichEditCtrl::Undo
dev_langs:
- C++
helpviewer_keywords:
- CRichEditCtrl class, common controls
- CRichEditCtrl class
- formatted text [C++]
ms.assetid: 2be52788-822c-4c27-aafd-2471231e74eb
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 77b8dfb6011831f4e4300096a127f70b26bcc603
ms.lasthandoff: 02/24/2017

---
# <a name="cricheditctrl-class"></a>CRichEditCtrl (clase)
Proporciona la funcionalidad del control Rich Edit.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRichEditCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRichEditCtrl::CRichEditCtrl](#cricheditctrl)|Construye un objeto `CRichEditCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CRichEditCtrl::CanPaste](#canpaste)|Determina si se puede pegar el contenido del Portapapeles en el control de edición enriquecida.|  
|[CRichEditCtrl::CanRedo](#canredo)|Determina si hay acciones en la cola de rehacer del control.|  
|[CRichEditCtrl::CanUndo](#canundo)|Determina si se puede deshacer una operación de edición.|  
|[CRichEditCtrl::CharFromPos](#charfrompos)|Recupera información sobre el carácter más cercano al punto especificado en el área de cliente de un control de edición.|  
|[CRichEditCtrl::Clear](#clear)|Borra la selección actual.|  
|[CRichEditCtrl::Copy](#copy)|Copia la selección actual en el Portapapeles.|  
|[CRichEditCtrl::Create](#create)|Crea el control de edición enriquecida de Windows y lo asocia con esta `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::CreateEx](#createex)|Crea el control de edición enriquecida de Windows con los valores especificados Windows estilos extendidos y lo asocia con esta `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::Cut](#cut)|Corta la selección actual en el Portapapeles.|  
|[CRichEditCtrl::DisplayBand](#displayband)|Muestra una parte del contenido de este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::EmptyUndoBuffer](#emptyundobuffer)|Restablece el indicador de deshacer de este (borra) `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::FindText](#findtext)|Busca texto en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::FindWordBreak](#findwordbreak)|Busca el siguiente salto de word antes o después de la posición de carácter especificado o recupera información sobre el carácter en esa posición.|  
|[CRichEditCtrl::FormatRange](#formatrange)|Da formato a un intervalo de texto para el dispositivo de salida de destino.|  
|[CRichEditCtrl::GetCharPos](#getcharpos)|Determina la ubicación de un carácter dado dentro de este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetDefaultCharFormat](#getdefaultcharformat)|Recupera el carácter predeterminado actual formato atributos en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetEventMask](#geteventmask)|Recupera la máscara de eventos para este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetFirstVisibleLine](#getfirstvisibleline)|Determina la primera línea visible en esta `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetIRichEditOle](#getiricheditole)|Recupera un puntero a la `IRichEditOle` de la interfaz de control este rich edit.|  
|[CRichEditCtrl::GetLimitText](#getlimittext)|Obtiene el límite en la cantidad de texto que un usuario puede escribir en esta `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetLine](#getline)|Recupera una línea de texto de esta `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetLineCount](#getlinecount)|Recupera el número de líneas en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetModify](#getmodify)|Determina si el contenido de este `CRichEditCtrl` objeto han cambiado desde la última.|  
|[CRichEditCtrl::GetOptions](#getoptions)|Recupera las opciones de control de edición enriquecida.|  
|[CRichEditCtrl::GetParaFormat](#getparaformat)|Recupera el formato de atributos de la selección actual en este párrafo `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetPunctuation](#getpunctuation)|Recupera los caracteres de puntuación actual para el control de edición enriquecida. Este mensaje solo está disponible en versiones de idiomas asiáticos del sistema operativo.|  
|[CRichEditCtrl::GetRect](#getrect)|Recupera el rectángulo de formato para este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetRedoName](#getredoname)|Recupera el tipo de la siguiente acción, si existe alguno, en el control de la cola de rehacer.|  
|[CRichEditCtrl::GetSel](#getsel)|Obtiene las posiciones de la selección actual en este la inicial y final `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetSelectionCharFormat](#getselectioncharformat)|Recupera el carácter de formato de los atributos de la selección actual en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetSelectionType](#getselectiontype)|Recupera el tipo de contenido de la selección actual en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::GetSelText](#getseltext)|Obtiene el texto de la selección actual en este `CRichEditCtrl` objeto|  
|[CRichEditCtrl::GetTextLength](#gettextlength)|Recupera la longitud del texto, en caracteres, en este `CRichEditCtrl` objeto. No incluye el carácter nulo de terminación.|  
|[CRichEditCtrl::GetTextLengthEx](#gettextlengthex)|Recupera el número de caracteres o bytes en la vista de edición enriquecida. Acepta una lista de indicadores para determinar el método para determinar la longitud del texto en un control rich edit|  
|[CRichEditCtrl::GetTextMode](#gettextmode)|Recupera el nivel actual de deshacer y de modo de texto de un control rich edit.|  
|[CRichEditCtrl::GetTextRange](#gettextrange)|Recupera el intervalo de texto especificado.|  
|[CRichEditCtrl::GetUndoName](#getundoname)|Recupera el tipo de la siguiente acción de deshacer, si existe.|  
|[CRichEditCtrl::GetWordWrapMode](#getwordwrapmode)|Recupera las opciones de separación de word para el control rich edit y ajuste de línea actual. Este mensaje solo está disponible en versiones de idiomas asiáticos del sistema operativo.|  
|[CRichEditCtrl::HideSelection](#hideselection)|Muestra u oculta la selección actual.|  
|[CRichEditCtrl::LimitText](#limittext)|Limita la cantidad de texto que un usuario puede escribir en el `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::LineFromChar](#linefromchar)|Determina qué línea contiene el carácter especificado.|  
|[CRichEditCtrl::LineIndex](#lineindex)|Recupera el índice de carácter de una línea determinada en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::LineLength](#linelength)|Recupera la longitud de una línea determinada en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::LineScroll](#linescroll)|Desplaza el texto en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::Paste](#paste)|Inserta el contenido del Portapapeles en este control de edición enriquecida.|  
|[CRichEditCtrl::PasteSpecial](#pastespecial)|Inserta el contenido del Portapapeles en el control de edición enriquecida en el formato de datos especificado.|  
|[CRichEditCtrl::PosFromChar](#posfromchar)|Recupera las coordenadas del área cliente de un carácter especificado en un control de edición.|  
|[CRichEditCtrl::Redo](#redo)|Rehace la acción siguiente de la cola de rehacer del control.|  
|[CRichEditCtrl::ReplaceSel](#replacesel)|Reemplaza la selección actual en este `CRichEditCtrl` objeto con el texto especificado.|  
|[CRichEditCtrl::RequestResize](#requestresize)|Esto fuerza `CRichEditCtrl` objeto para enviar notificaciones de cambio de tamaño de solicitud.|  
|[CRichEditCtrl::SetAutoURLDetect](#setautourldetect)|Indica si la detección de dirección URL automática está activa en un control rich edit.|  
|[CRichEditCtrl::SetBackgroundColor](#setbackgroundcolor)|Establece el color de fondo en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetDefaultCharFormat](#setdefaultcharformat)|Establece el carácter predeterminado actual formato atributos en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetEventMask](#seteventmask)|Establece la máscara de eventos de este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetModify](#setmodify)|Establece o borra la marca de modificación de este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetOLECallback](#setolecallback)|Establece la `IRichEditOleCallback` objeto COM para este control de edición enriquecida.|  
|[CRichEditCtrl::SetOptions](#setoptions)|Establece las opciones para este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetParaFormat](#setparaformat)|Establece el formato de atributos de la selección actual en este párrafo `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetPunctuation](#setpunctuation)|Establece los caracteres de puntuación de un control rich edit. Este mensaje solo está disponible en versiones de idiomas asiáticos del sistema operativo.|  
|[CRichEditCtrl::SetReadOnly](#setreadonly)|Establece la opción de sólo lectura para este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetRect](#setrect)|Establece el rectángulo de formato de este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetSel](#setsel)|Establece la selección en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetSelectionCharFormat](#setselectioncharformat)|Establece el carácter de formato de los atributos de la selección actual en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetTargetDevice](#settargetdevice)|Establece el dispositivo de salida de destino de este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetTextMode](#settextmode)|Establece el nivel de deshacer o de modo de texto de un control rich edit. Se produce un error en el mensaje si el control contiene texto.|  
|[CRichEditCtrl::SetUndoLimit](#setundolimit)|Establece el número máximo de acciones que se pueden almacenar en la cola de deshacer.|  
|[CRichEditCtrl::SetWordCharFormat](#setwordcharformat)|Establece el carácter de formato de los atributos de la palabra actual en este `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::SetWordWrapMode](#setwordwrapmode)|Establece las opciones de ajuste automático de línea y de separación de palabras de la amplia el control de edición. Este mensaje solo está disponible en versiones de idiomas asiáticos del sistema operativo.|  
|[CRichEditCtrl::StopGroupTyping](#stopgrouptyping)|Detiene el control de recopilación adicional escribiendo acciones en la acción de deshacer actual. El control almacena la siguiente acción de escritura, si hay alguno, en una acción nueva en la cola de deshacer.|  
|[CRichEditCtrl::StreamIn](#streamin)|Inserta texto de un flujo de entrada en esta `CRichEditCtrl` objeto.|  
|[CRichEditCtrl::StreamOut](#streamout)|Almacena el texto de esta `CRichEditCtrl` objeto en una secuencia de salida.|  
|[CRichEditCtrl::Undo](#undo)|Invierte la última operación de edición.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control rich edit" es una ventana en la que el usuario puede escribir y editar texto. El texto se puede asignar caracteres y el formato de párrafo y puede incluir objetos OLE incrustados. Los controles Rich edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para realizar operaciones de formato disponibles para el usuario.  
  
 Este control común de Windows (y por tanto la `CRichEditCtrl` clase) está disponible sólo para los programas que se ejecutan en versiones de Windows 95 ó 98 y Windows NT 3.51 y posteriores. El `CRichEditCtrl` clase es compatible con las versiones 2.0 y 3.0 de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] control rich edit.  
  
> [!CAUTION]
>  Si está utilizando un control rich edit en un cuadro de diálogo (independientemente de si la aplicación es SDI, MDI o basada en cuadros de diálogo), debe llamar a [AfxInitRichEdit](application-information-and-management.md#afxinitrichedit) una vez antes del cuadro de diálogo se muestra el cuadro. Un lugar típico para llamar a esta función es en el programa `InitInstance` función miembro. No es necesario llamarla cada vez que se muestre el cuadro de diálogo, sólo la primera vez. No es necesario llamar a `AfxInitRichEdit` si está trabajando con `CRichEditView`.  
  
 Para obtener más información sobre el uso de `CRichEditCtrl`, consulte:  
  
- [Controles](../../mfc/controls-mfc.md)  
  
- [Usar CRichEditCtrl](../../mfc/using-cricheditctrl.md)  
  
-   Artículo de Knowledge Base Q259949: INFO: SetCaretPos() es no adecuados con CEdit o controles CRichEditCtrl  
  
 Para obtener un ejemplo del uso de un control rich edit en una aplicación MFC, vea el [WORDPAD](../../visual-cpp-samples.md) aplicación de ejemplo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CRichEditCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="canpaste"></a>CRichEditCtrl::CanPaste  
 Determina si el control rich edit puede pegar el formato de Portapapeles especificado.  
  
```  
BOOL CanPaste(UINT nFormat = 0) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nFormat`  
 El formato de datos del Portapapeles a la consulta. Este parámetro puede ser uno de los formatos de Portapapeles predefinidos o el valor devuelto por [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049).  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el formato del Portapapeles se puede pegar; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si `nFormat` es 0, `CanPaste` intentará cualquier formato actualmente en el Portapapeles.  
  
 Para obtener más información, consulte [EM_CANPASTE](http://msdn.microsoft.com/library/windows/desktop/bb787993) mensaje y [RegisterClipboardFormat](http://msdn.microsoft.com/library/windows/desktop/ms649049) funcionan en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CRichEditCtrl](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_1.cpp)]  
  
##  <a name="canredo"></a>CRichEditCtrl::CanRedo  
 Determina si la cola de rehacer contiene todas las acciones.  
  
```  
BOOL CanRedo() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la cola de rehacer contiene acciones, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para conocer el nombre de la operación en la cola de rehacer, llame a [CRichEditCtrl::GetRedoName](#getredoname). Para rehacer la última operación de deshacer, llame a [rehacer](#redo).  
  
 Para obtener más información, consulte [EM_CANREDO](http://msdn.microsoft.com/library/windows/desktop/bb787995) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="canundo"></a>CRichEditCtrl::CanUndo  
 Determina si se puede deshacer la última operación de edición.  
  
```  
BOOL CanUndo() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la última operación de edición se puede deshacer mediante una llamada a la [deshacer](#undo) función miembro; 0 si no se puede deshacer.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [EM_CANUNDO](http://msdn.microsoft.com/library/windows/desktop/bb775468) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#2;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_2.cpp)]  
  
##  <a name="charfrompos"></a>CRichEditCtrl::CharFromPos  
 Recupera información sobre el carácter en el punto especificado por el parámetro `pt`.  
  
```  
int CharFromPos(CPoint pt) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pt`  
 Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas del punto especificado.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de carácter de base cero del carácter más cercano al punto especificado. Si el punto especificado está más allá del último carácter en el control, el valor devuelto indica el último carácter en el control.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro se trabaja con un control rich edit. Para obtener la información de un control de edición, llame a [CEdit::CharFromPos](../../mfc/reference/cedit-class.md#charfrompos).  
  
 Para obtener más información, consulte [EM_CHARFROMPOS](http://msdn.microsoft.com/library/windows/desktop/bb761566) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="clear"></a>CRichEditCtrl::Clear  
 Elimina (borra) la selección actual (si existe) en el amplio control de edición.  
  
```  
void Clear();
```  
  
### <a name="remarks"></a>Comentarios  
 La eliminación realizada por **borrar** puede deshacer llamando a la [deshacer](#undo) función miembro.  
  
 Para eliminar la selección actual y coloca el contenido eliminado en el Portapapeles, llame a la [cortar](#cut) función miembro.  
  
 Para obtener más información, consulte [WM_CLEAR](http://msdn.microsoft.com/library/windows/desktop/ms649020) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&3;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_3.cpp)]  
  
##  <a name="copy"></a>CRichEditCtrl::Copy  
 Copia la selección actual (si existe) en el control rich edit en el Portapapeles.  
  
```  
void Copy();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [WM_COPY](http://msdn.microsoft.com/library/windows/desktop/ms649022) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl Nº&4;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_4.cpp)]  
  
##  <a name="create"></a>CRichEditCtrl::Create  
 Crea el control de edición enriquecida de Windows y lo asocia con esta `CRichEditCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de edición. Aplicar una combinación de los estilos de ventana que aparecen en la **comentarios** sección más adelante, y [estilos de control de edición](http://msdn.microsoft.com/library/windows/desktop/bb775464), descrita en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `rect`  
 Especifica el tamaño y la posición del control de edición. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o [RECT](../../mfc/reference/rect-structure1.md) estructura.  
  
 `pParentWnd`  
 Especifica la ventana primaria del control de edición (a menudo un [CDialog](../../mfc/reference/cdialog-class.md)). No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador. del control de edición  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la inicialización es correcta; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Construya un `CRichEditCtrl` objeto en dos pasos. En primer lugar, llame a la [CRichEditCtrl](#cricheditctrl) constructor, a continuación, llame a **crear**, que crea el control de edición de Windows y lo adjunta a la `CRichEditCtrl` objeto.  
  
 Cuando se crea un control rich edit con esta función, primero debe cargar la biblioteca de controles comunes necesarios. Para cargar la biblioteca, llame a la función global [AfxInitRichEdit](application-information-and-management.md#afxinitrichedit), que a su vez inicializa la biblioteca de controles comunes. Debe llamar a `AfxInitRichEdit` sólo una vez en el proceso.  
  
 Cuando **crear** se ejecuta, Windows envía la [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize), [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), y [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) mensajes para el control de edición.  
  
 Estos mensajes se controlan de manera predeterminada el [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), y [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) funciones miembro en la `CWnd` clase base. Para extender el control de mensajes de forma predeterminada, derive una clase de `CRichEditCtrl`, agregue un mapa de mensajes a la nueva clase y reemplazar las funciones miembro de controlador de mensajes anteriores. Invalidar `OnCreate`, por ejemplo, para realizar la inicialización necesaria para la nueva clase.  
  
 Aplique el siguiente [estilos de ventana](../../mfc/reference/window-styles.md) a un control de edición.  
  
- **WS_CHILD** siempre.  
  
- **WS_VISIBLE** normalmente.  
  
- **WS_DISABLED** rara vez.  
  
- **WS_GROUP** a controles de grupo.  
  
- **WS_TABSTOP** para incluir el control de edición en el orden de tabulación.  
  
 Para obtener más información acerca de los estilos de ventana, consulte [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#5;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_5.cpp)]  
  
##  <a name="createex"></a>CRichEditCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CRichEditCtrl` objeto.  
  
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
 Especifica el estilo del control de edición. Aplicar una combinación de los estilos de ventana que aparecen en la **comentarios** sección de [crear](#create) y [estilos de control de edición](http://msdn.microsoft.com/library/windows/desktop/bb775464), descrita en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
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
  
##  <a name="cricheditctrl"></a>CRichEditCtrl::CRichEditCtrl  
 Construye un objeto `CRichEditCtrl`.  
  
```  
CRichEditCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Utilice [crear](#create) para construir las ventanas de control rich edit.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl Nº&6;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_6.cpp)]  
  
##  <a name="cut"></a>CRichEditCtrl::Cut  
 Eliminar (cortes) control de edición de la selección actual (si existe) de la amplia y copia el texto eliminado en el Portapapeles.  
  
```  
void Cut();
```  
  
### <a name="remarks"></a>Comentarios  
 La eliminación realizada por **cortar** puede deshacer llamando a la [deshacer](#undo) función miembro.  
  
 Para eliminar la selección actual sin poner el texto eliminado en el Portapapeles, llame a la [borrar](#clear) función miembro.  
  
 Para obtener más información, consulte [WM_CUT](http://msdn.microsoft.com/library/windows/desktop/ms649023) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#7;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_7.cpp)]  
  
##  <a name="displayband"></a>CRichEditCtrl::DisplayBand  
 Muestra una parte del contenido del control rich edit (texto y elementos OLE), formateada anteriormente [FormatRange](#formatrange).  
  
```  
BOOL DisplayBand(LPRECT pDisplayRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDisplayRect`  
 Puntero a un [RECT](../../mfc/reference/rect-structure1.md) o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que especifica el área del dispositivo para mostrar el texto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la presentación del texto con formato se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El texto y los elementos OLE se recortan al área especificado por el puntero `pDisplayRect`.  
  
 Para obtener más información, consulte [EM_DISPLAYBAND](http://msdn.microsoft.com/library/windows/desktop/bb787997) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditCtrl::FormatRange](#formatrange).  
  
##  <a name="emptyundobuffer"></a>CRichEditCtrl::EmptyUndoBuffer  
 (Borrar) restablece el indicador de deshacer del control de edición enriquecida.  
  
```  
void EmptyUndoBuffer();
```  
  
### <a name="remarks"></a>Comentarios  
 Ahora, el control podrá deshacer la última operación de edición. Se establece el indicador de deshacer cada vez que se puede deshacer una operación dentro del control de edición enriquecida.  
  
 El indicador de deshacer se borra automáticamente cada vez que se llama a la [CWnd](../../mfc/reference/cwnd-class.md) función miembro [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
 Para obtener más información, consulte [EM_EMPTYUNDOBUFFER](http://msdn.microsoft.com/library/windows/desktop/bb761568) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl Nº&8;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_8.cpp)]  
  
##  <a name="findtext"></a>CRichEditCtrl::FindText  
 Busca texto en el control de edición enriquecida.  
  
```  
long FindText(
    DWORD dwFlags,  
    FINDTEXTEX* pFindText) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Para obtener una lista de valores posibles, consulte `wParam` en [EM_FINDTEXTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788011) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *pFindText*  
 Puntero a la [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) estructurar dando a los parámetros de la búsqueda y devolver el intervalo donde se encontró la coincidencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Posición de carácter de base cero de la coincidencia siguiente; – 1 si no hay nada más coincidencias.  
  
### <a name="remarks"></a>Comentarios  
 Puede buscar bien hacia arriba o hacia abajo al establecer los parámetros de intervalo apropiado el [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura dentro de la **FINDTEXTEX** estructura.  
  
 Para obtener más información, consulte [EM_FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb788011) mensaje y [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#9;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_9.cpp)]  
  
##  <a name="findwordbreak"></a>CRichEditCtrl::FindWordBreak  
 Busca el siguiente salto de word antes o después de la posición especificada por `nStart`.  
  
```  
DWORD FindWordBreak(
    UINT nCode,  
    DWORD nStart) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nCode`  
 Indica la acción que se realizará. Para obtener una lista de valores posibles, vea la descripción para el parámetro `code` en **EM_FINDWORDBREAK** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `nStart`  
 La posición de carácter de base cero desde el que se va a iniciar.  
  
### <a name="return-value"></a>Valor devuelto  
 Basándose en el parámetro `nCode`. Para obtener más información, consulte [EM_FINDWORDBREAK](http://msdn.microsoft.com/library/windows/desktop/bb788018) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Puede utilizar esta función miembro para recuperar información acerca de un carácter en una posición determinada.  
  
##  <a name="formatrange"></a>CRichEditCtrl::FormatRange  
 Da formato a un intervalo de texto en un control rich edit para un dispositivo específico.  
  
```  
long FormatRange(
    FORMATRANGE* pfr,  
    BOOL bDisplay = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *PFR*  
 Puntero a la [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) estructura que contiene información sobre el dispositivo de salida. **NULL** indica que se puede liberar la información almacenada en caché en el control de edición enriquecida.  
  
 *bDisplay*  
 Indica si se debe representar el texto. Si **FALSE**, simplemente se mide el texto.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del último carácter que se ajusta en la región más uno.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esta llamada es seguida por una llamada a [DisplayBand](#displayband).  
  
 Para obtener más información, consulte [EM_FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb788020) mensaje y [FORMATRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787911) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#10;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_10.cpp)]  
  
##  <a name="getcharpos"></a>CRichEditCtrl::GetCharPos  
 Obtiene la posición (esquina superior izquierda) de un determinado carácter dentro de este `CRichEditCtrl` objeto.  
  
```  
CPoint GetCharPos(long lChar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lChar`  
 Índice de base cero del carácter.  
  
### <a name="return-value"></a>Valor devuelto  
 La ubicación de la esquina superior izquierda del carácter especificado por `lChar`.  
  
### <a name="remarks"></a>Comentarios  
 El carácter se especifica indicando su valor de índice de base cero. Si `lChar` es mayor que el índice del último carácter en esta `CRichEditCtrl` de objeto, el valor devuelto especifica las coordenadas de la posición de carácter inmediatamente después del último carácter en esta `CRichEditCtrl` objeto.  
  
 Para obtener más información, consulte [EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getdefaultcharformat"></a>CRichEditCtrl::GetDefaultCharFormat  
 Obtiene el carácter predeterminado de atributos de este formato `CRichEditCtrl` objeto.  
  
```  
DWORD GetDefaultCharFormat(CHARFORMAT& cf) const;  DWORD GetDefaultCharFormat(CHARFORMAT2& cf) const;  ```  
  
### Parameters  
 `cf`  
 In the first version, a pointer to a **CHARFORMAT** structure holding the default character formatting attributes.  
  
 In the second version, a pointer to a **CHARFORMAT2** structure, which is a Rich Edit 2.0 extension to the **CHARFORMAT** structure, holding the default character formatting attributes.  
  
### Return Value  
 The **dwMask** data member of `cf`. It specified the default character formatting attributes.  
  
### Remarks  
 For more information, see the **EM_GETCHARFORMAT** message and the **CHARFORMAT** and **CHARFORMAT2** structures in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [SetDefaultCharFormat](#setdefaultcharformat).  
  
##  <a name="geteventmask"></a>  CRichEditCtrl::GetEventMask  
 Gets the event mask for this `CRichEditCtrl` object.  
  
```  
GetEventMask() Long const;  
```  
  
### Return Value  
 The event mask for this `CRichEditCtrl` object.  
  
### Remarks  
 The event mask specifies which notification messages the `CRichEditCtrl` object sends to its parent window.  
  
 For more information, see [EM_GETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb788032) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [CRichEditCtrl::SetEventMask](#seteventmask).  
  
##  <a name="getfirstvisibleline"></a>  CRichEditCtrl::GetFirstVisibleLine  
 Determines the topmost visible line in this `CRichEditCtrl` object.  
  
```  
int GetFirstVisibleLine() const;  
```  
  
### Return Value  
 Zero-based index of the uppermost visible line in this `CRichEditCtrl` object.  
  
### Remarks  
 For more information, see [EM_GETFIRSTVISIBLELINE](http://msdn.microsoft.com/library/windows/desktop/bb761574) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#11](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_11.cpp)]  
  
##  <a name="getiricheditole"></a>  CRichEditCtrl::GetIRichEditOle  
 Accesses the **IRichEditOle** interface for this `CRichEditCtrl` object.  
  
```  
IRichEditOle * GetIRichEditOle() const;  
```  
  
### Return Value  
 Pointer to the [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) interface that can be used to access this `CRichEditCtrl` object's OLE functionality; **NULL** if the interface is not accessible.  
  
### Remarks  
 Use this interface to access this `CRichEditCtrl` object's OLE functionality.  
  
 For more information, see [EM_GETOLEINTERFACE](http://msdn.microsoft.com/library/windows/desktop/bb788041) message and [IRichEditOle](http://msdn.microsoft.com/library/windows/desktop/bb774306) interface in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getlimittext"></a>  CRichEditCtrl::GetLimitText  
 Gets the text limit for this `CRichEditCtrl` object.  
  
```  
GetLimitText() Long const;  
```  
  
### Return Value  
 The current text limit, in bytes, for this `CRichEditCtrl` object.  
  
### Remarks  
 The text limit is the maximum amount of text, in bytes, the rich edit control can accept.  
  
 For more information, see [EM_GETLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761582) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#12](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_12.cpp)]  
  
##  <a name="getline"></a>  CRichEditCtrl::GetLine  
 Retrieves a line of text from this `CRichEditCtrl` object.  
  
```  
int GetLine (int nIndex,  
    LPTSTR lpszBuffer) const;  
  
int GetLine (int nIndex,  
    LPTSTR lpszBuffer,  
    int nMaxLength) const;  
```  
  
### Parameters  
 `nIndex`  
 Zero-based index of the line to retrieve.  
  
 `lpszBuffer`  
 Points to the buffer to receive the text. The first word of the buffer must specify the maximum number of bytes that can be copied into the buffer.  
  
 `nMaxLength`  
 Maximum number of characters that can be copied into `lpszBuffer`. The second form of `GetLine` places this value into the first word of the buffer specified by `lpszBuffer`.  
  
### Return Value  
 The number of characters copied into `lpszBuffer`.  
  
### Remarks  
 The copied line does not contain a terminating null character.  
  
> [!NOTE]
>  Because the first word of the buffer stores the number of characters to be copied, make sure that your buffer is at least 4 bytes long.  
  
 For more information, see [EM_GETLINE](http://msdn.microsoft.com/library/windows/desktop/bb761584) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [GetLineCount](#getlinecount).  
  
##  <a name="getlinecount"></a>  CRichEditCtrl::GetLineCount  
 Retrieves the number of lines in the `CRichEditCtrl` object.  
  
```  
int GetLineCount() const;  
```  
  
### Return Value  
 The number of lines in this `CRichEditCtrl` object.  
  
### Remarks  
 For more information, see [EM_GETLINECOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761586) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#13](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_13.cpp)]  
  
##  <a name="getmodify"></a>  CRichEditCtrl::GetModify  
 Determines if the contents of this `CRichEditCtrl` object have been modified.  
  
```  
BOOL GetModify() const;  
```  
  
### Return Value  
 Nonzero if the text in this `CRichEditCtrl` object has been modified; otherwise 0.  
  
### Remarks  
 Windows maintains an internal flag indicating whether the contents of the rich edit control have been changed. This flag is cleared when the edit control is first created and can also be cleared by calling the [SetModify](#setmodify) member function.  
  
 For more information, see [EM_GETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761592) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#14](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_14.cpp)]  
  
##  <a name="getoptions"></a>  CRichEditCtrl::GetOptions  
 Retrieves the options currently set for the rich edit control.  
  
```  
UINT GetOptions() const;  
```  
  
### Return Value  
 A combination of the current option flag values. For a list of these values, see the *fOptions* parameter in the [EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254) message, as described in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getparaformat"></a>  CRichEditCtrl::GetParaFormat  
 Gets the paragraph formatting attributes of the current selection.  
  
```  
DWORD GetParaFormat(PARAFORMAT& pf) const;  DWORD GetParaFormat(PARAFORMAT2& pf) const;  ```  
  
### <a name="parameters"></a>Parámetros  
 `pf`  
 En la primera versión, un puntero a un [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) estructura para contener los atributos de la selección actual de formato de párrafo.  
  
 En la segunda versión, un puntero a un [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) estructura, que es una extensión de Rich Edit 2.0 para la **PARAFORMAT** estructura, que contiene atributos de formato de carácter predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 El **dwMask** miembro de datos de `pf`. Especifica los atributos que son coherentes a lo largo de la selección actual de formato de párrafo.  
  
### <a name="remarks"></a>Comentarios  
 Si se selecciona más de un párrafo, `pf` recibe los atributos del primer párrafo seleccionado. El valor devuelto especifica qué atributos son coherentes en toda la selección.  
  
 Para obtener más información, consulte el [EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182) mensaje y la **PARAFORMAT** y **PARAFORMAT2** las estructuras de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditCtrl::SetParaFormat](#setparaformat).  
  
##  <a name="getpunctuation"></a>CRichEditCtrl::GetPunctuation  
 Obtiene los caracteres de puntuación actual en un control rich edit.  
  
```  
BOOL GetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `fType`  
 El indicador de tipo de puntuación, como se describe en el `fType` parámetro de [EM_GETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774184) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `lpPunc`  
 Un puntero a un [puntuación](http://msdn.microsoft.com/library/windows/desktop/bb787944) estructura, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la operación se realizó correctamente, en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro está disponible con las versiones de idiomas asiáticos del sistema operativo.  
  
##  <a name="getrect"></a>CRichEditCtrl::GetRect  
 Recupera el rectángulo de formato para este `CRichEditCtrl` objeto.  
  
```  
void GetRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md) o un puntero a un [RECT](../../mfc/reference/rect-structure1.md) para recibir el rectángulo de este formato `CRichEditCtrl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El rectángulo de formato es el rectángulo delimitador para el texto. Este valor es independiente del tamaño de la `CRichEditCtrl` objeto.  
  
 Para obtener más información, consulte [EM_GETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761596) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [LimitText](#limittext).  
  
##  <a name="getredoname"></a>CRichEditCtrl::GetRedoName  
 Recupera el tipo de la siguiente acción disponible en la cola de rehacer, si existe.  
  
```  
UNDONAMEID GetRedoName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, `GetRedoName` devuelve el [UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365) tipo de enumeración que indica el tipo de la acción siguiente de la cola de rehacer del control. Si la cola de rehacer está vacía, o si la acción de rehacer en la cola es de tipo desconocido, `GetRedoName` devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Los tipos de acciones que pueden deshacer o rehacer incluyen escribir, eliminar, arrastrar y colocar, cortar y pegar las operaciones. Esta información puede ser útil para las aplicaciones que proporcionan una interfaz de usuario extendida para operaciones de deshacer y rehacer, como un cuadro de lista desplegable de acciones redoable.  
  
##  <a name="getsel"></a>CRichEditCtrl::GetSel  
 Recupera los límites de la selección actual en este `CRichEditCtrl` objeto.  
  
```  
void GetSel(CHARRANGE& cr) const;  
  
void GetSel(
    long& nStartChar,  
    long& nEndChar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `cr`  
 Hacer referencia a un [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura para recibir los límites de la selección actual.  
  
 `nStartChar`  
 Índice de base cero del primer carácter de la selección actual.  
  
 `nEndChar`  
 Índice de base cero del último carácter de la selección actual.  
  
### <a name="remarks"></a>Comentarios  
 Las dos formas de esta función proporcionan formas alternativas de obtener los límites de la selección. Siguen breves descripciones de estas formas:  
  
- **Función miembro GetSel (** `cr` **)** este formulario usa el **CHARRANGE** estructura con su **cpMin** y **cpMax** miembros para devolver los límites.  
  
- **Función miembro GetSel (** `nStartChar` **,** `nEndChar` **)** este formulario devuelve los límites de los parámetros `nStartChar` y `nEndChar`.  
  
 La selección incluye todo lo que si el principio ( **cpMin** o `nStartChar`) es 0 y el extremo ( **cpMax** o `nEndChar`) es – 1.  
  
 Para obtener más información, consulte [EM_EXGETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788001) mensaje y [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#15;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_15.cpp)]  
  
##  <a name="getselectioncharformat"></a>CRichEditCtrl::GetSelectionCharFormat  
 Obtiene el carácter de formato de atributos de la selección actual.  
  
```  
DWORD GetSelectionCharFormat(CHARFORMAT& cf) const;  DWORD GetSelectionCharFormat(CHARFORMAT2& cf) const;  ```  
  
### Parameters  
 `cf`  
 In the first version, a pointer to a [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) structure to receive the character formatting attributes of the current selection.  
  
 In the second version, a pointer to a [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) structure, which is a Rich Edit 2.0 extension to the **CHARFORMAT** structure to receive the character formatting attributes of the current selection.  
  
### Return Value  
 The **dwMask** data member of `cf`. It specifies the character formatting attributes that are consistent throughout the current selection.  
  
### Remarks  
 The `cf` parameter receives the attributes of the first character in the current selection. The return value specifies which attributes are consistent throughout the selection.  
  
 For more information, see the [EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026) message and the **CHARFORMAT** and **CHARFORMAT2** structures in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
  See the example for [SetSelectionCharFormat](#setselectioncharformat).  
  
##  <a name="getselectiontype"></a>  CRichEditCtrl::GetSelectionType  
 Determines the selection type in this `CRichEditCtrl` object.  
  
```  
WORD GetSelectionType() const;  
```  
  
### Return Value  
 Flags indicating the contents of the current selection. A combination of the following flags:  
  
- `SEL_EMPTY` Indicates that there is no current selection.  
  
- `SEL_TEXT` Indicates that the current selection contains text.  
  
- `SEL_OBJECT` Indicates that the current selection contains at least one OLE item.  
  
- `SEL_MULTICHAR` Indicates that the current selection contains more than one character of text.  
  
- `SEL_MULTIOBJECT` Indicates that the current selection contains more than one OLE object.  
  
### Remarks  
 For more information, see [EM_SELECTIONTYPE](http://msdn.microsoft.com/library/windows/desktop/bb774223) in the [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### Example  
 [!code-cpp[NVC_MFC_CRichEditCtrl#16](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_16.cpp)]  
  
##  <a name="getseltext"></a>  CRichEditCtrl::GetSelText  
 Retrieves the text from the current selection in this `CRichEditCtrl` object.  
  
```  
GetSelText(LPSTR lpBuf) Long const;  CString GetSelText() const;  ```  
  
### <a name="parameters"></a>Parámetros  
 `lpBuf`  
 Puntero al búfer que recibe el texto de la selección actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Depende del formulario:  
  
- **Función miembro GetSelText (** `lpBuf` **)** el número de caracteres copiados en `lpBuf`, sin incluir la terminación null.  
  
- **() De la función miembro GetSelText** la cadena que contiene la selección actual.  
  
### <a name="remarks"></a>Comentarios  
 Si utiliza el primer formulario, **función miembro GetSelText (** `lpBuf` **)**, debe asegurarse de que el búfer es lo suficientemente grande como para el texto que se recibirá. Llame a [función miembro GetSel](#getsel) para determinar el número de caracteres de la selección actual.  
  
 Para obtener más información, consulte [EM_GETSELTEXT](http://msdn.microsoft.com/library/windows/desktop/bb774190) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditCtrl::GetSelectionType](#getselectiontype).  
  
##  <a name="gettextlength"></a>CRichEditCtrl::GetTextLength  
 Recupera la longitud del texto, en caracteres, en este `CRichEditCtrl` objeto, sin incluir el carácter nulo de terminación.  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud del texto en este `CRichEditCtrl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [WM_GETTEXTLENGTH](http://msdn.microsoft.com/library/windows/desktop/ms632628) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#17;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_17.cpp)]  
  
##  <a name="gettextlengthex"></a>CRichEditCtrl::GetTextLengthEx  
 Calcula la longitud del texto del control de edición enriquecida.  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Valor que especifica el método que se utilizará para determinar la longitud del texto. Este miembro puede ser uno o varios de los valores enumeran en el miembro flags de [GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915) se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `uCodePage`  
 Página de códigos para la traducción (CP_ACP para página de códigos ANSI, 1200 para Unicode).  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres o bytes en el control de edición. Si se establecen marcas incompatible `dwFlags`, esta función miembro devuelve `E_INVALIDARG`.  
  
### <a name="remarks"></a>Comentarios  
 `GetTextLengthEx`proporciona otras maneras de determinar la longitud del texto. Admite la funcionalidad de Rich Edit 2.0. Consulte [acerca de los controles Rich Edit](http://msdn.microsoft.com/library/windows/desktop/bb787873) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]para obtener más información.  
  
##  <a name="gettextmode"></a>CRichEditCtrl::GetTextMode  
 Recupera el nivel actual de deshacer y de modo de texto de un control rich edit.  
  
```  
UINT GetTextMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un conjunto de marcadores de bits de la [TEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774364) tipo de enumeración, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Los marcadores indican el modo de texto actual y deshacer el nivel del control.  
  
##  <a name="gettextrange"></a>CRichEditCtrl::GetTextRange  
 Obtiene el intervalo de caracteres especificado.  
  
```  
int GetTextRange(
    int nFirst,  
    int nLast,  
    CString& refString) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nFirst`  
 El índice de posición de carácter inmediatamente antes del primer carácter del intervalo.  
  
 `nLast`  
 Posición de carácter inmediatamente después del último carácter del intervalo.  
  
 `refString`  
 Una referencia a un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que va a recibir el texto.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres copiados, sin incluir el carácter nulo de terminación.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [EM_GETTEXTRANGE](http://msdn.microsoft.com/library/windows/desktop/bb774199) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `GetTextRange`admite la funcionalidad de Rich Edit 2.0. Consulte [acerca de los controles Rich Edit](http://msdn.microsoft.com/library/windows/desktop/bb787873) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]para obtener más información.  
  
##  <a name="getundoname"></a>CRichEditCtrl::GetUndoName  
 Recupera el tipo de la siguiente acción disponible en la cola de deshacer, si existe.  
  
```  
UNDONAMEID GetUndoName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si está en la cola de deshacer del control, una acción de deshacer `GetUndoName` devuelve el [UNDONAMEID](http://msdn.microsoft.com/library/windows/desktop/bb774365) tipo de enumeración que indica el tipo de la acción siguiente de la cola. Si la cola de deshacer está vacía, o si la acción de deshacer en la cola es de tipo desconocido, `GetUndoName` devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Los tipos de acciones que pueden deshacer o rehacer incluyen escribir, eliminar, arrastrar y colocar, cortar y pegar las operaciones. Esta información puede ser útil para las aplicaciones que proporcionan una interfaz de usuario extendida para operaciones de deshacer y rehacer, como un cuadro de lista desplegable de acciones que se pueden deshacer.  
  
##  <a name="getwordwrapmode"></a>CRichEditCtrl::GetWordWrapMode  
 Recupera las opciones de separación de word para el control rich edit y ajuste de línea actual.  
  
```  
UINT GetWordWrapMode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ajuste de línea actual y las opciones de separación de palabras. Estas opciones se describen en [EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro está disponible sólo para las versiones de idiomas asiáticos del sistema operativo.  
  
##  <a name="hideselection"></a>CRichEditCtrl::HideSelection  
 Cambia la visibilidad de la selección.  
  
```  
void HideSelection(
    BOOL bHide,  
    BOOL bPerm);
```  
  
### <a name="parameters"></a>Parámetros  
 `bHide`  
 Indica si la selección debe mostrar u ocultar, **TRUE** para ocultar la selección.  
  
 `bPerm`  
 Indica si este cambio en la visibilidad para la selección debe ser permanente.  
  
### <a name="remarks"></a>Comentarios  
 Cuando `bPerm` es **TRUE**, cambia la `ECO_NOHIDESEL` opción de `CRichEditCtrl` objeto. Para obtener una breve descripción de esta opción, consulte [SetOptions](#setoptions). Puede utilizar esta función para establecer todas las opciones para este `CRichEditCtrl` objeto.  
  
 Para obtener más información, consulte [EM_HIDESELECTION](http://msdn.microsoft.com/library/windows/desktop/bb774210) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#18;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_18.cpp)]  
  
##  <a name="limittext"></a>CRichEditCtrl::LimitText  
 Limita la longitud del texto que el usuario puede escribir en un control de edición.  
  
```  
void LimitText(long nChars = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nChars`  
 Especifica la longitud (en bytes) del texto que el usuario puede escribir. Si este parámetro es 0 (el valor predeterminado), la longitud del texto se establece en 64K bytes.  
  
### <a name="remarks"></a>Comentarios  
 Cambiar el límite del texto restringe sólo el texto que el usuario puede escribir. No tiene ningún efecto en cualquier texto ya en el control de edición, ni afecta a la longitud del texto copiado en el control de edición mediante la [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) función miembro en `CWnd`. Si una aplicación usa el `SetWindowText` función colocar más texto en un control de edición a la especificada en la llamada a `LimitText`, el usuario puede eliminar el texto dentro del control de edición. Sin embargo, el límite del texto evitará que el usuario reemplace el texto existente con texto nuevo, a menos que la eliminación de la actual selección hace que el texto quede por debajo del límite de texto.  
  
> [!NOTE]
>  Para el límite de texto, cada elemento OLE se considera como un solo carácter.  
  
 Para obtener más información, consulte [EM_EXLIMITTEXT](http://msdn.microsoft.com/library/windows/desktop/bb788003) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl Nº&19;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_19.cpp)]  
  
##  <a name="linefromchar"></a>CRichEditCtrl::LineFromChar  
 Recupera el número de la línea que contiene el índice de carácter especificado.  
  
```  
long LineFromChar(long nIndex) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nIndex`  
 Contiene el valor de índice de base cero del carácter deseado en el texto del control de edición, o -1. Si `nIndex` es –&1;, especifica la línea actual, es decir, la línea que contiene el símbolo de intercalación.  
  
### <a name="return-value"></a>Valor devuelto  
 El número de línea de base cero de la línea que contiene el índice de carácter especificado por `nIndex`. Si `nIndex` es –&1;, se devuelve el número de la línea que contiene el primer carácter de la selección. Si no hay ninguna selección, se devuelve el número de línea actual.  
  
### <a name="remarks"></a>Comentarios  
 Un índice de carácter es el número de caracteres desde el principio del control de edición enriquecida. Recuento de caracteres, de un elemento OLE se cuenta como un solo carácter.  
  
 Para obtener más información, consulte [EM_EXLINEFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb788005) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#20;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_20.cpp)]  
  
##  <a name="lineindex"></a>CRichEditCtrl::LineIndex  
 Recupera el índice de carácter de una línea dentro de este `CRichEditCtrl` objeto.  
  
```  
int LineIndex(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nLine`  
 Contiene el valor de índice de la línea deseada en el texto del control de edición, o -1. Si `nLine` es –&1;, especifica la línea actual, es decir, la línea que contiene el símbolo de intercalación.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice de carácter de la línea especificada en `nLine` o –&1; si el número de línea especificado es mayor, el número de líneas en el control de edición.  
  
### <a name="remarks"></a>Comentarios  
 El índice de carácter es el número de caracteres desde el principio del control rich edit a la línea especificada.  
  
 Para obtener más información, consulte [EM_LINEINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761611) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[21 NVC_MFC_CRichEditCtrl](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_21.cpp)]  
  
##  <a name="linelength"></a>CRichEditCtrl::LineLength  
 Recupera la longitud de una línea en un control rich edit.  
  
```  
int LineLength(int nLine = -1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nLine`  
 Especifica el índice de carácter de un carácter en la línea cuya longitud se va a recuperar. Si este parámetro es -1, se devuelve la longitud de la línea actual (la línea que contiene el símbolo de intercalación), sin incluir la longitud de cualquier texto dentro de la línea seleccionado. Cuando `LineLength` se llama para un control de edición de la línea, se omite este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Cuando `LineLength` se llama para un control de edición de varias líneas, el valor devuelto es la longitud (en bytes) de la línea especificada por `nLine`. Cuando `LineLength` se llama para un control de edición de la línea, el valor devuelto es la longitud (en bytes) del texto en el control de edición.  
  
### <a name="remarks"></a>Comentarios  
 Utilice la [LineIndex](#lineindex) función miembro para recuperar el índice de carácter para un número de línea dentro de este `CRichEditCtrl` objeto.  
  
 Para obtener más información, consulte [EM_LINELENGTH](http://msdn.microsoft.com/library/windows/desktop/bb761613) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [LineIndex](#lineindex).  
  
##  <a name="linescroll"></a>CRichEditCtrl::LineScroll  
 Desplaza el texto de un control de edición de varias líneas.  
  
```  
void LineScroll(
    int nLines,  
    int nChars = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nLines`  
 Especifica el número de líneas de desplazamiento vertical.  
  
 `nChars`  
 Especifica el número de posiciones de caracteres a desplazarse horizontalmente. Este valor se omite si el control rich edit tiene la **ES_RIGHT** o **ES_CENTER** estilo. [Edición de estilos de](../../mfc/reference/edit-styles.md) se especifican en [crear](#create).  
  
### <a name="remarks"></a>Comentarios  
 No se desplaza verticalmente el control de edición más allá de la última línea de texto en el control de edición. Si la línea actual más el número de líneas especificado por `nLines` supera el número total de líneas en el control de edición, el valor se ajusta para que la última línea del control de edición se desplaza a la parte superior de la ventana de control de edición.  
  
 `LineScroll`puede utilizarse para desplazarse horizontalmente más allá del último carácter de cada línea.  
  
 Para obtener más información, consulte [EM_LINESCROLL](http://msdn.microsoft.com/library/windows/desktop/bb761615) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [GetFirstVisibleLine](#getfirstvisibleline).  
  
##  <a name="paste"></a>CRichEditCtrl::Paste  
 Inserta los datos desde el Portapapeles en el `CRichEditCtrl` en el punto de inserción, la ubicación del símbolo de intercalación.  
  
```  
void Paste();
```  
  
### <a name="remarks"></a>Comentarios  
 Datos se insertan sólo si el Portapapeles contiene datos en un formato reconocido.  
  
 Para obtener más información, consulte [WM_PASTE](http://msdn.microsoft.com/library/windows/desktop/ms649028) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#22;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_22.cpp)]  
  
##  <a name="pastespecial"></a>CRichEditCtrl::PasteSpecial  
 Pega los datos en un formato de Portapapeles específico en esta `CRichEditCtrl` objeto.  
  
```  
void PasteSpecial(
    UINT nClipFormat,  
    DWORD dvAspect = 0,  
    HMETAFILE hMF = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *nClipFormat*  
 Formato del Portapapeles Pegar en esta `CRichEditCtrl` objeto.  
  
 *dvAspect*  
 Aspecto de dispositivo para los datos que se van a recuperar desde el Portapapeles.  
  
 *hMF*  
 Identificador del metarchivo que contiene la vista de iconos de objeto que se va a pegar.  
  
### <a name="remarks"></a>Comentarios  
 El material nuevo se inserta en el punto de inserción, la ubicación del símbolo de intercalación.  
  
 Para obtener más información, consulte [EM_PASTESPECIAL](http://msdn.microsoft.com/library/windows/desktop/bb774214) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[23 de NVC_MFC_CRichEditCtrl #](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_23.cpp)]  
  
##  <a name="posfromchar"></a>CRichEditCtrl::PosFromChar  
 Recupera las coordenadas del área cliente de un carácter especificado en un control de edición.  
  
```  
CPoint PosFromChar(UINT nChar) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nChar`  
 Índice de base cero del carácter.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición de carácter, (x, y). Para un control de edición de la línea, la coordenada y siempre es cero.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [EM_POSFROMCHAR](http://msdn.microsoft.com/library/windows/desktop/bb761631) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="redo"></a>CRichEditCtrl::Redo  
 Rehace la acción siguiente de la cola de rehacer del control.  
  
```  
BOOL Redo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [EM_REDO](http://msdn.microsoft.com/library/windows/desktop/bb774218) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="replacesel"></a>CRichEditCtrl::ReplaceSel  
 Reemplaza la selección actual en este `CRichEditCtrl` el objeto con el texto especificado.  
  
```  
void ReplaceSel(
    LPCTSTR lpszNewText,  
    BOOL bCanUndo = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszNewText`  
 Puntero a una cadena terminada en null que contiene el texto de reemplazo.  
  
 `bCanUndo`  
 Para especificar que se puede deshacer esta función, establezca el valor de este parámetro para **TRUE**. El valor predeterminado es **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Para reemplazar todo el texto en este `CRichEditCtrl` objeto, utilice [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext).  
  
 Si no hay ninguna selección, el texto de reemplazo se inserta en el punto de inserción, es decir, la ubicación actual del símbolo de intercalación.  
  
 Esta función formateará el texto insertado con el formato de carácter existente. Cuando se reemplaza el intervalo de texto completo (mediante una llamada a `SetSel`(0, -1) antes de llamar a `ReplaceSel`), hay un carácter de fin de párrafo que conserva el formato del párrafo anterior, que se hereda en el texto recién insertado.  
  
 Para obtener más información, consulte [EM_REPLACESEL](http://msdn.microsoft.com/library/windows/desktop/bb761633) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [LineIndex](#lineindex).  
  
##  <a name="requestresize"></a>CRichEditCtrl::RequestResize  
 Esto fuerza `CRichEditCtrl` objeto para enviar **EN_REQUESTRESIZE** mensajes de notificación a su ventana primaria.  
  
```  
void RequestResize();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función resulta útil durante [CWnd::OnSize](../../mfc/reference/cwnd-class.md#onsize) de procesamiento para un sin límite `CRichEditCtrl` objeto.  
  
 Para obtener más información, consulte el [EM_REQUESTRESIZE](http://msdn.microsoft.com/library/windows/desktop/bb774220) mensaje y la **controles Rich Edit sin límite** sección de [acerca de los controles Rich Edit](http://msdn.microsoft.com/library/windows/desktop/bb787873) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setautourldetect"></a>CRichEditCtrl::SetAutoURLDetect  
 Establece el control rich edit para detectar automáticamente una dirección URL.  
  
```  
BOOL SetAutoURLDetect(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bEnable`  
 Especifica si el control se establece para detectar automáticamente una dirección URL. Si **TRUE**, está habilitada. Si **FALSE**, está deshabilitado.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si es correcto, de lo contrario es distinto de cero. Por ejemplo, el mensaje puede no debido a memoria insuficiente.  
  
### <a name="remarks"></a>Comentarios  
 Si está habilitada, el control rich edit examinará el texto para determinar si coincide con un formato de dirección URL estándar. Para obtener una lista de estos formatos de dirección URL, vea [EM_AUTOURLDETECT](http://msdn.microsoft.com/library/windows/desktop/bb787991) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
> [!NOTE]
>  No establezca `SetAutoURLDetect` a **TRUE** si usa el control de edición del **CFE_LINK** efecto para el texto que no sea de direcciones URL. `SetAutoURLDetect`Este efecto se habilita para las direcciones URL y deshabilita para todo el texto. Consulte [EN_LINK](http://msdn.microsoft.com/library/windows/desktop/bb787970) para obtener más información acerca de la **CFE_LINK** efecto.  
  
##  <a name="setbackgroundcolor"></a>CRichEditCtrl::SetBackgroundColor  
 Establece el color de fondo de este `CRichEditCtrl` objeto.  
  
```  
COLORREF SetBackgroundColor(
    BOOL bSysColor,  
    COLORREF cr);
```  
  
### <a name="parameters"></a>Parámetros  
 `bSysColor`  
 Indica si el color de fondo debe establecerse en el valor del sistema. Si este valor es **TRUE**, `cr` se omite.  
  
 `cr`  
 El color de fondo solicitada. Sólo se usa si `bSysColor` es **FALSE**.  
  
### <a name="return-value"></a>Valor devuelto  
 El color de fondo anterior de este `CRichEditCtrl` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Se puede establecer el color de fondo para el valor del sistema o en un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor.  
  
 Para obtener más información, consulte [EM_SETBKGNDCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774228) mensaje y [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#24;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_24.cpp)]  
  
##  <a name="setdefaultcharformat"></a>CRichEditCtrl::SetDefaultCharFormat  
 Establece los atributos de texto nuevo en este formato de caracteres `CRichEditCtrl` objeto.  
  
```  
BOOL SetDefaultCharFormat(CHARFORMAT& cf);  
BOOL SetDefaultCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>Parámetros  
 `cf`  
 En la primera versión, un puntero a un [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) estructura que contiene los atributos de formato de carácter predeterminado nuevo.  
  
 En la segunda versión, un puntero a un [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) estructura, que es una extensión de Rich Edit 2.0 para la **CHARFORMAT** estructura, que contiene atributos de formato de carácter predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Sólo los atributos especificados por el **dwMask** miembro de `cf` se cambian por esta función.  
  
 Para obtener más información, consulte el [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) mensaje y la **CHARFORMAT** y **CHARFORMAT2** las estructuras de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#25;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_25.cpp)]  
  
##  <a name="seteventmask"></a>CRichEditCtrl::SetEventMask  
 Establece la máscara de eventos de este `CRichEditCtrl` objeto.  
  
```  
DWORD SetEventMask(DWORD dwEventMask);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwEventMask*  
 La nueva máscara de eventos para este `CRichEditCtrl` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 La máscara de eventos anterior.  
  
### <a name="remarks"></a>Comentarios  
 La máscara de eventos especifica qué mensajes de notificación del `CRichEditCtrl` objeto envía a su ventana primaria.  
  
 Para obtener más información, consulte [EM_SETEVENTMASK](http://msdn.microsoft.com/library/windows/desktop/bb774238) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[26 de NVC_MFC_CRichEditCtrl #](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_26.cpp)]  
  
##  <a name="setmodify"></a>CRichEditCtrl::SetModify  
 Establece o borra la marca modificada para un control de edición.  
  
```  
void SetModify(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bModified`  
 Un valor de **TRUE** indica que se ha modificado el texto y un valor de **FALSE** indica no se modifica. De forma predeterminada, se establece el indicador modificado.  
  
### <a name="remarks"></a>Comentarios  
 El indicador modificado indica si no se ha modificado el texto del control de edición. Se establece automáticamente cuando el usuario cambia el texto. Su valor se puede recuperar con el [GetModify](#getmodify) función miembro.  
  
 Para obtener más información, consulte [EM_SETMODIFY](http://msdn.microsoft.com/library/windows/desktop/bb761651) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [GetModify](#getmodify).  
  
##  <a name="setolecallback"></a>CRichEditCtrl::SetOLECallback  
 Esto da `CRichEditCtrl` objeto un **IRichEditOleCallback** objeto que se va a utilizar para tener acceso a información y recursos relacionados con OLE.  
  
```  
BOOL SetOLECallback(IRichEditOleCallback* pCallback);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCallback`  
 Puntero a un [IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308) objeto que este `CRichEditCtrl` objeto utilizará para obtener información y recursos relacionados con OLE.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esto `CRichEditCtrl` objeto llamará [IUnknown:: AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) para incrementar el recuento de uso para el objeto COM especificado por `pCallback`.  
  
 Para obtener más información, consulte [EM_SETOLECALLBACK](http://msdn.microsoft.com/library/windows/desktop/bb774252) mensaje y [IRichEditOleCallback](http://msdn.microsoft.com/library/windows/desktop/bb774308) de la interfaz en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="setoptions"></a>CRichEditCtrl::SetOptions  
 Establece las opciones para este `CRichEditCtrl` objeto.  
  
```  
void SetOptions(
    WORD wOp,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 *wOp*  
 Indica el tipo de operación. Uno de los siguientes valores:  
  
- `ECOOP_SET`Establecer las opciones a los especificados por `dwFlags`.  
  
- `ECOOP_OR`Combinar las opciones actuales con los especificados por `dwFlags`.  
  
- `ECOOP_AND`Conservar sólo las opciones actuales que también se especifican por `dwFlags`.  
  
- `ECOOP_XOR`Conservar sólo las opciones actuales que están *no* especificado por `dwFlags`.  
  
 `dwFlags`  
 Opciones de edición enriquecidas. Los valores de indicador se muestran en la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Las opciones pueden ser una combinación de los siguientes valores:  
  
- `ECO_AUTOWORDSELECTION`Haga doble clic en la selección automática de palabras.  
  
- `ECO_AUTOVSCROLL`Desplaza el texto automáticamente a la derecha 10 caracteres cuando el usuario escribe un carácter al final de la línea. Cuando el usuario presiona la tecla ENTRAR, el control desplaza todo el texto a la posición cero.  
  
- `ECO_AUTOHSCROLL`Texto de una página se desplaza automáticamente cuando el usuario presiona la tecla ENTRAR en la última línea.  
  
- `ECO_NOHIDESEL`Niega el comportamiento predeterminado para un control de edición. El comportamiento predeterminado oculta la selección cuando el control pierde el foco de entrada y la selección muestra cuando el control recibe el foco de entrada. Si especifica `ECO_NOHIDESEL`, se invierte el texto seleccionado, incluso si el control no tiene el foco.  
  
- `ECO_READONLY`Evita que el usuario escriba o edite texto en el control de edición.  
  
- `ECO_WANTRETURN`Especifica que se inserte un retorno de carro cuando el usuario presiona la tecla ENTRAR mientras escribe texto en un control de edición enriquecida de varias líneas en un cuadro de diálogo. Si no especifica este estilo, presionar la tecla ENTRAR envía un comando a ventana primaria del control rich edit, que imita al hacer clic en el botón predeterminado de la ventana primaria (por ejemplo, el botón Aceptar en un cuadro de diálogo). Este estilo no tiene ningún efecto en una sola línea control de edición.  
  
- `ECO_SAVESEL`Conserva la selección cuando el control pierde el foco. De forma predeterminada, se selecciona todo el contenido del control cuando se recupere el foco.  
  
- `ECO_VERTICAL`Dibuja el texto y los objetos verticalmente. Está disponible para idiomas asiáticos únicamente.  
  
 Para obtener más información, consulte [EM_SETOPTIONS](http://msdn.microsoft.com/library/windows/desktop/bb774254) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl Nº&27;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_27.cpp)]  
  
##  <a name="setparaformat"></a>CRichEditCtrl::SetParaFormat  
 Establece lo atributos de la selección actual en este formato de párrafo `CRichEditCtrl` objeto.  
  
```  
BOOL SetParaFormat(PARAFORMAT& pf);  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>Parámetros  
 `pf`  
 En la primera versión, un puntero a un [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) atributos de formato de párrafo de la estructura que contiene el nuevo valor predeterminado.  
  
 En la segunda versión, un puntero a un [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) estructura, que es una extensión de Rich Edit 2.0 para la **PARAFORMAT** estructura, que contiene atributos de formato de carácter predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Sólo los atributos especificados por el **dwMask** miembro de `pf` se cambian por esta función.  
  
 Para obtener más información, consulte el [EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276) mensaje y la **PARAFORMAT** y **PARAFORMAT2** las estructuras de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#28;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_28.cpp)]  
  
##  <a name="setpunctuation"></a>CRichEditCtrl::SetPunctuation  
 Establece los signos de puntuación en un control rich edit.  
  
```  
BOOL SetPunctuation(
    UINT fType,  
    PUNCTUATION* lpPunc);
```  
  
### <a name="parameters"></a>Parámetros  
 `fType`  
 La marca de puntuación. Para obtener una lista de valores posibles, vea el `fType` parámetro [EM_SETPUNCTUATION](http://msdn.microsoft.com/library/windows/desktop/bb774278) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 `lpPunc`  
 Un puntero a un [puntuación](http://msdn.microsoft.com/library/windows/desktop/bb787944) estructura, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se realiza correctamente, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro está disponible para versiones de idiomas asiáticos sólo del sistema operativo.  
  
##  <a name="setreadonly"></a>CRichEditCtrl::SetReadOnly  
 Cambios del `ECO_READONLY` opción de `CRichEditCtrl` objeto.  
  
```  
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bReadOnly`  
 Indica si este `CRichEditCtrl` objeto debe ser de solo lectura.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una breve descripción de esta opción, consulte [SetOptions](#setoptions). Puede utilizar esta función para establecer todas las opciones para este `CRichEditCtrl` objeto.  
  
 Para obtener más información, consulte [EM_SETREADONLY](http://msdn.microsoft.com/library/windows/desktop/bb761655) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#29;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_29.cpp)]  
  
##  <a name="setrect"></a>CRichEditCtrl::SetRect  
 Establece el rectángulo de formato de este `CRichEditCtrl` objeto.  
  
```  
void SetRect(LPCRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRect`  
 [CRect](../../atl-mfc-shared/reference/crect-class.md) o un puntero a un [RECT](../../mfc/reference/rect-structure1.md) que indica los nuevos límites del rectángulo de formato.  
  
### <a name="remarks"></a>Comentarios  
 El rectángulo de formato es el rectángulo limitador del texto. El rectángulo limitador es independiente del tamaño de la ventana de control de edición enriquecida. Cuando esto `CRichEditCtrl` objeto se crea por primera vez, el rectángulo de formato es el mismo tamaño que el área de cliente de la ventana. Use `SetRect` para que el rectángulo de formato mayor o menor que la ventana de edición enriquecida.  
  
 Para obtener más información, consulte [EM_SETRECT](http://msdn.microsoft.com/library/windows/desktop/bb761657) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl Nº&30;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_30.cpp)]  
  
##  <a name="setsel"></a>CRichEditCtrl::SetSel  
 Establece la selección dentro de este `CRichEditCtrl` objeto.  
  
```  
void SetSel(
    long nStartChar,  
    long nEndChar);  
  
void SetSel(CHARRANGE& cr);
```  
  
### <a name="parameters"></a>Parámetros  
 `nStartChar`  
 Índice de base cero del primer carácter de la selección.  
  
 `nEndChar`  
 Índice de base cero del último carácter de la selección.  
  
 `cr`  
 [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura que contiene los límites de la selección actual.  
  
### <a name="remarks"></a>Comentarios  
 Las dos formas de esta función proporcionan métodos alternativos para establecer los límites de la selección. Siguen breves descripciones de estas formas:  
  
- **Función miembro SetSel (** `cr` **)** este formulario usa el **CHARRANGE** estructura con su **cpMin** y **cpMax** miembros para establecer los límites.  
  
- **Función miembro SetSel (** `nStartChar` **,** `nEndChar` **)** este formulario use los parámetros `nStartChar` y `nEndChar` para establecer los límites.  
  
 El símbolo de intercalación se coloca al final de la selección indicada por el mayor número de inicio ( **cpMin** o `nStartChar`) y final ( **cpMax** o `nEndChar`) índices. Esta función desplaza el contenido de la `CRichEditCtrl` hasta que aparezca el símbolo de intercalación.  
  
 Para seleccionar todo el texto en este `CRichEditCtrl` objeto, llame a `SetSel` con un índice de inicio de 0 y un índice final de – 1.  
  
 Para obtener más información, consulte [EM_EXSETSEL](http://msdn.microsoft.com/library/windows/desktop/bb788007) mensaje y [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [función miembro GetSel](#getsel).  
  
##  <a name="setselectioncharformat"></a>CRichEditCtrl::SetSelectionCharFormat  
 Establece el carácter de atributos de texto de la selección actual en este formato `CRichEditCtrl` objeto.  
  
```  
BOOL SetSelectionCharFormat(CHARFORMAT& cf);  
BOOL SetSelectionCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>Parámetros  
 `cf`  
 En la primera versión, un puntero a un [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) estructura que contiene el nuevo formato de carácter de atributos de la selección actual.  
  
 En la segunda versión, un puntero a un [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) estructura, que es una extensión de Rich Edit 2.0 para la **CHARFORMAT** estructura, que contiene el carácter de nueva formato atributos para la selección actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Sólo los atributos especificados por el **dwMask** miembro de `cf` se cambian por esta función.  
  
 Para obtener más información, consulte el [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) y **CHARFORMAT** y **CHARFORMAT2** las estructuras de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#31;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_31.cpp)]  
  
##  <a name="settargetdevice"></a>CRichEditCtrl::SetTargetDevice  
 Establece el ancho de línea y de dispositivo de destino utilizado en WYSIWYG (lo que ve es lo que se obtiene) en este formato de `CRichEditCtrl` objeto.  
  
```  
BOOL SetTargetDevice(
    HDC hDC,  
    long lLineWidth);

 
BOOL SetTargetDevice(
    CDC& dc,  
    long lLineWidth);
```  
  
### <a name="parameters"></a>Parámetros  
 `hDC`  
 Identificador del contexto de dispositivo para el nuevo dispositivo de destino.  
  
 *lLineWidth*  
 Ancho de línea que se utilizará para dar formato.  
  
 `dc`  
 [CDC](../../mfc/reference/cdc-class.md) para el nuevo dispositivo de destino.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Si esta función se realiza correctamente, el control rich edit posee el dispositivo el contexto se pasa como parámetro. En ese caso, la función de llamada deberá destruir el contexto de dispositivo.  
  
 Para obtener más información, consulte [EM_SETTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/bb774282) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#32;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_32.cpp)]  
  
##  <a name="settextmode"></a>CRichEditCtrl::SetTextMode  
 Establece el nivel de modo o deshacer y rehacer de texto de un control rich edit.  
  
```  
BOOL SetTextMode(UINT fMode);
```  
  
### <a name="parameters"></a>Parámetros  
 *fMode*  
 Especifica la nueva configuración para modo y deshacer nivel parámetros de texto del control. Para obtener una lista de los valores posibles, vea el parámetro de modo de [EM_SETTEXTMODE](http://msdn.microsoft.com/library/windows/desktop/bb774286) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si es correcto, de lo contrario es distinto de cero.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una descripción de los modos de texto, consulte **EM_SETTEXTMODE** en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Esta función miembro produce un error si el control contiene texto. Para asegurarse de que el control está vacío, envíe un [WM_SETTEXT](http://msdn.microsoft.com/library/windows/desktop/ms632644) mensaje con una cadena vacía.  
  
##  <a name="setundolimit"></a>CRichEditCtrl::SetUndoLimit  
 Establece el número máximo de acciones que se pueden almacenar en la cola de deshacer.  
  
```  
UINT SetUndoLimit(UINT nLimit);
```  
  
### <a name="parameters"></a>Parámetros  
 *nLimit*  
 Especifica el número máximo de acciones que se pueden almacenar en la cola de deshacer. Establecer en cero para deshabilitar la opción deshacer.  
  
### <a name="return-value"></a>Valor devuelto  
 El nuevo número máximo de acciones de deshacer para el amplio control de edición.  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, el número máximo de acciones de la cola de deshacer es 100. Si se aumenta este número, debe haber suficiente memoria disponible para alojar al nuevo número. Para mejorar el rendimiento, establecer el límite en el menor valor posible.  
  
##  <a name="setwordcharformat"></a>CRichEditCtrl::SetWordCharFormat  
 Establece los atributos de la palabra seleccionada actualmente en este formato de caracteres `CRichEditCtrl` objeto.  
  
```  
BOOL SetWordCharFormat(CHARFORMAT& cf);  
BOOL SetWordCharFormat(CHARFORMAT2& cf);
```  
  
### <a name="parameters"></a>Parámetros  
 `cf`  
 En la primera versión, un puntero a un [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) los atributos de estructura que contiene el nuevo formato de caracteres de la palabra seleccionada actualmente.  
  
 En la segunda versión, un puntero a un [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) estructura, que es una extensión de Rich Edit 2.0 para la **CHARFORMAT** estructura, que contiene el carácter de nueva formato atributos para la palabra seleccionada actualmente.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Sólo los atributos especificados por el **dwMask** miembro de `cf` se cambian por esta función.  
  
 Para obtener más información, consulte el [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) mensaje y la **CHARFORMAT** y **CHARFORMAT2** las estructuras de la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl Nº&33;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_33.cpp)]  
  
##  <a name="setwordwrapmode"></a>CRichEditCtrl::SetWordWrapMode  
 Establece las opciones de ajuste automático de línea y de separación de palabras de la amplia el control de edición.  
  
```  
UINT SetWordWrapMode(UINT uFlags) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `uFlags`  
 Las opciones para establecer el ajuste de línea y de separación de palabras. Para obtener una lista de opciones posibles, consulte [EM_SETWORDWRAPMODE](http://msdn.microsoft.com/library/windows/desktop/bb774294) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 El ajuste automático de línea actual y la separación de palabras opciones.  
  
### <a name="remarks"></a>Comentarios  
 Este mensaje solo está disponible en versiones de idiomas asiáticos del sistema operativo.  
  
##  <a name="stopgrouptyping"></a>CRichEditCtrl::StopGroupTyping  
 Detiene el control de recopilación adicional escribiendo acciones en la acción de deshacer actual.  
  
```  
void StopGroupTyping();
```  
  
### <a name="remarks"></a>Comentarios  
 El control almacena la siguiente acción de escritura, si hay alguno, en una acción nueva en la cola de deshacer.  
  
 Para obtener más información, consulte [EM_STOPGROUPTYPING](http://msdn.microsoft.com/library/windows/desktop/bb774300) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="streamin"></a>CRichEditCtrl::StreamIn  
 Reemplaza el texto en este `CRichEditCtrl` objeto con el texto de la secuencia de entrada especificada.  
  
```  
long StreamIn(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>Parámetros  
 `nFormat`  
 Marcadores que especifican los formatos de datos de entrada. Vea la sección Comentarios para obtener más información.  
  
 `es`  
 [Estructura EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) estructura que especifica la secuencia de entrada. Vea la sección Comentarios para obtener más información.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de caracteres leídos de la secuencia de entrada.  
  
### <a name="remarks"></a>Comentarios  
 El valor de `nFormat` debe ser uno de los siguientes:  
  
- `SF_TEXT`Indica texto sólo de lectura.  
  
- `SF_RTF`Indica el texto de lectura y el formato.  
  
 Cualquiera de estos valores se pueden combinar con `SFF_SELECTION`. Si `SFF_SELECTION` se especifica, `StreamIn` reemplaza la selección actual con el contenido de la secuencia de entrada. Si no se especifica, `StreamIn` reemplaza todo el contenido de este `CRichEditCtrl` objeto.  
  
 En el **estructura EDITSTREAM** parámetro `es`, especificar una función de devolución de llamada que llena un búfer de texto. Esta función de devolución de llamada se llama varias veces, hasta que se agote el flujo de entrada.  
  
 Para obtener más información, consulte [EM_STREAMIN](http://msdn.microsoft.com/library/windows/desktop/bb774302) mensaje y [estructura EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#34;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_34.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#35;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_35.cpp)]  
  
##  <a name="streamout"></a>CRichEditCtrl::StreamOut  
 Escribe el contenido de este `CRichEditCtrl` objeto al flujo de salida especificado.  
  
```  
long StreamOut(
    int nFormat,  
    EDITSTREAM& es);
```  
  
### <a name="parameters"></a>Parámetros  
 `nFormat`  
 Marcadores que especifican los formatos de datos de salida. Vea la sección Comentarios para obtener más información.  
  
 `es`  
 [Estructura EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) estructura que especifica la secuencia de salida. Vea la sección Comentarios para obtener más información.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de caracteres escritos en la secuencia de salida.  
  
### <a name="remarks"></a>Comentarios  
 El valor de `nFormat` debe ser uno de los siguientes:  
  
- `SF_TEXT`Indica que sólo el texto escrito.  
  
- `SF_RTF`Indica el formato y escribir texto.  
  
- `SF_RTFNOOBJS`Indica escribir texto y formato, reemplazando los elementos OLE con espacios.  
  
- `SF_TEXTIZED`Indica texto escrito y formato por representaciones de texto de elementos OLE.  
  
 Cualquiera de estos valores se pueden combinar con `SFF_SELECTION`. Si `SFF_SELECTION` se especifica, `StreamOut` escribe la selección actual en la secuencia de salida. Si no se especifica, `StreamOut` escribe todo el contenido de este `CRichEditCtrl` objeto.  
  
 En el **estructura EDITSTREAM** parámetro `es`, especificar una función de devolución de llamada que llena un búfer con texto. Esta función de devolución de llamada se llama varias veces, hasta que se agote el flujo de salida.  
  
 Para obtener más información, consulte [EM_STREAMOUT](http://msdn.microsoft.com/library/windows/desktop/bb774304) mensaje y [estructura EDITSTREAM](http://msdn.microsoft.com/library/windows/desktop/bb787891) estructura en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#36;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_36.cpp)]  
  
 [!code-cpp[NVC_MFC_CRichEditCtrl&#37;](../../mfc/reference/codesnippet/cpp/cricheditctrl-class_37.cpp)]  
  
##  <a name="undo"></a>CRichEditCtrl::Undo  
 Deshace la última operación en el control de edición enriquecida.  
  
```  
BOOL Undo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación de deshacer es correcta; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 También se puede deshacer una operación de deshacer. Por ejemplo, puede restaurar el texto eliminado con la primera llamada a **deshacer**. Como no hay ninguna operación de edición que intervienen, puede quitar el texto de nuevo con una segunda llamada a **deshacer**.  
  
 Para obtener más información, consulte [EM_UNDO](http://msdn.microsoft.com/library/windows/desktop/bb761670) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CanUndo](#canundo).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC WORDPAD](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase CEdit](../../mfc/reference/cedit-class.md)   
 [CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)

