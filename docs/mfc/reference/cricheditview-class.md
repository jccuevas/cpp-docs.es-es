---
title: CRichEditView (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
dev_langs:
- C++
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ece09b51dba7be272a208478d48196024189180e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853529"
---
# <a name="cricheditview-class"></a>CRichEditView (clase)
Con [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control rich edit en el contexto de la arquitectura de vista de documento de MFC.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CRichEditView : public CCtrlView  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::CRichEditView](#cricheditview)|Construye un objeto `CRichEditView`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Mueve un cuadro de diálogo para no interferir con la selección actual.|  
|[CRichEditView::CanPaste](#canpaste)|Indica si el Portapapeles contiene datos que se pueden pegar en la vista de edición enriquecida.|  
|[CRichEditView::DoPaste](#dopaste)|Pega un elemento OLE en esta vista de rich edit.|  
|[CRichEditView::FindText](#findtext)|Busca el texto especificado, invocar el cursor de espera.|  
|[CRichEditView::FindTextSimple](#findtextsimple)|Busca el texto especificado.|  
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Recupera el formato de atributos para la selección actual de caracteres.|  
|[CRichEditView::GetDocument](#getdocument)|Recupera un puntero a la que se relaciona [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md).|  
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Recupera el elemento OLE que está activo actualmente en el contexto en la vista de edición enriquecida.|  
|[CRichEditView::GetMargins](#getmargins)|Recupera los márgenes de esta vista de rich edit.|  
|[CRichEditView::GetPageRect](#getpagerect)|Recupera el rectángulo de la página de esta vista de rich edit.|  
|[CRichEditView::GetPaperSize](#getpapersize)|Recupera el tamaño del papel para esta vista de rich edit.|  
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Recupera los atributos para la selección actual de formato de párrafo.|  
|[CRichEditView::GetPrintRect](#getprintrect)|Recupera el rectángulo de impresión para esta vista de rich edit.|  
|[CRichEditView::GetPrintWidth](#getprintwidth)|Recupera el ancho de impresión para esta vista de rich edit.|  
|[CRichEditView:: GetRichEditCtrl](#getricheditctrl)|Recupera el control de edición enriquecida.|  
|[CRichEditView::GetSelectedItem](#getselecteditem)|Recupera el elemento seleccionado de la vista de edición enriquecida.|  
|[CRichEditView::GetTextLength](#gettextlength)|Recupera la longitud del texto en la vista de edición enriquecida.|  
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Recupera el número de caracteres o bytes en la vista de edición enriquecida. Lista expandida de marca para el método para determinar la longitud.|  
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Inserta un archivo como un elemento OLE.|  
|[CRichEditView::InsertItem](#insertitem)|Inserta un nuevo elemento como un elemento OLE.|  
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Indica si el Portapapeles contiene datos en formato de texto o de edición enriquecida.|  
|[CRichEditView::OnCharEffect](#onchareffect)|Alterna el formato de carácter para la selección actual.|  
|[CRichEditView::OnParaAlign](#onparaalign)|Cambia la alineación de párrafos.|  
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Actualiza la interfaz de usuario de comandos para las funciones de miembro público de carácter.|  
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Actualiza la interfaz de usuario de comandos para las funciones de miembro público de párrafo.|  
|[CRichEditView::PrintInsideRect](#printinsiderect)|Da formato al texto especificado dentro del rectángulo especificado.|  
|[CRichEditView::PrintPage](#printpage)|Da formato al texto especificado dentro de la página especificada.|  
|[CRichEditView::SetCharFormat](#setcharformat)|Establece el formato de atributos para la selección actual de caracteres.|  
|[CRichEditView::SetMargins](#setmargins)|Establece los márgenes para realizar un esta completo Editar vista.|  
|[CRichEditView::SetPaperSize](#setpapersize)|Establece el tamaño del papel para esta vista de rich edit.|  
|[CRichEditView::SetParaFormat](#setparaformat)|Establece los atributos para la selección actual de formato de párrafo.|  
|[CRichEditView::TextNotFound](#textnotfound)|Restablece el estado interno de búsqueda del control.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::GetClipboardData](#getclipboarddata)|Recupera un objeto Clipboard para un intervalo en esta vista de rich edit.|  
|[CRichEditView::GetContextMenu](#getcontextmenu)|Recupera un menú contextual para usar en un botón derecho del mouse hacia abajo.|  
|[CRichEditView::IsSelected](#isselected)|Indica si se selecciona el elemento OLE especificado o no.|  
|[CRichEditView::OnFindNext](#onfindnext)|Busca la siguiente repetición de una subcadena.|  
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Actualiza una vista cuando llega el primer adjunto a un documento.|  
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Recupera datos nativos de un elemento OLE.|  
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Establece las características de impresión en el dispositivo específico.|  
|[CRichEditView::OnReplaceAll](#onreplaceall)|Reemplaza todas las apariciones de una cadena determinada con una nueva cadena.|  
|[CRichEditView::OnReplaceSel](#onreplacesel)|Reemplaza la selección actual.|  
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Controla la notificación al usuario que no se encontró el texto solicitado.|  
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Las consultas para ver los datos en el `IDataObject`.|  
|[CRichEditView::WrapChanged](#wrapchanged)|Ajusta el dispositivo de salida de destino para este rich Edit. vista, en función del valor de `m_nWordWrap`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Indica la cantidad de sangría para listas con viñetas.|  
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Indica las restricciones de ajuste de palabra.|  
  
## <a name="remarks"></a>Comentarios  
 Un "control rich edit" es una ventana en la que el usuario puede escribir y editar texto. El texto se puede asignar caracteres y el formato de párrafo y puede incluir objetos OLE incrustados. Los controles Rich edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para realizar operaciones de formato disponibles para el usuario.  
  
 `CRichEditView` mantiene el texto y la característica de formato de texto. `CRichEditDoc` mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem` proporciona acceso de contenedor para el elemento de cliente OLE.  
  
 Este control común de Windows (y por lo tanto, el [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas) está disponible solo para programas que se ejecutan en versiones de Windows 95/98 y Windows NT 3.51 y versiones posteriores.  
  
 Para obtener un ejemplo del uso de una vista de rich edit en una aplicación MFC, vea el [WORDPAD](../../visual-cpp-samples.md) aplicación de ejemplo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CView](../../mfc/reference/cview-class.md)  
  
 [CCtrlView](../../mfc/reference/cctrlview-class.md)  
  
 `CRichEditView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxrich.h  
  
##  <a name="adjustdialogposition"></a>  CRichEditView::AdjustDialogPosition  
 Llame a esta función para mover el cuadro de diálogo determinado para que no oculte la selección actual.  
  
```  
void AdjustDialogPosition(CDialog* pDlg);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDlg*  
 Puntero a un `CDialog` objeto.  
  
##  <a name="canpaste"></a>  CRichEditView::CanPaste  
 Llame a esta función para determinar si el Portapapeles contiene información que se puede pegar en esta vista de rich edit.  
  
```  
BOOL CanPaste() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el Portapapeles contiene datos en un formato que puede aceptar esta vista de rich edit; en caso contrario, es 0.  
  
##  <a name="cricheditview"></a>  CRichEditView::CRichEditView  
 Llame a esta función para crear un `CRichEditView` objeto.  
  
```  
CRichEditView();
```  
  
##  <a name="dopaste"></a>  CRichEditView::DoPaste  
 Llame a esta función para pegar el elemento OLE en *dataobj* este enriquecido edita documento/vista.  
  
```  
void DoPaste(
    COleDataObject& dataobj,  
    CLIPFORMAT cf,  
    HMETAFILEPICT hMetaPict);
```  
  
### <a name="parameters"></a>Parámetros  
 *dataobj*  
 El [COleDataObject](../../mfc/reference/coledataobject-class.md) que contiene los datos que se va a pegar.  
  
 *CF*  
 El formato de Portapapeles deseado.  
  
 *hMetaPict*  
 Metarchivo que representa el elemento que se van a pegar.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función como parte de la implementación predeterminada de [QueryAcceptData](#queryacceptdata).  
  
 Esta función determina el tipo de pegar basándose en los resultados del controlador de pegado especial. Si *cf* es 0, el nuevo elemento usa la representación icónica actual. Si *cf* es distinto de cero y *hMetaPict* no es NULL, se utiliza el nuevo elemento *hMetaPict* para su representación.  
  
##  <a name="findtext"></a>  CRichEditView::FindText  
 Llame a esta función para buscar el texto especificado y establece como la selección actual.  
  
```  
BOOL FindText(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFind*  
 Contiene la cadena de búsqueda.  
  
 *bCase*  
 Indica si la búsqueda distingue mayúsculas de minúsculas.  
  
 *bWord*  
 Indica si la búsqueda debe coincidir con palabras completas, no partes de palabras.  
  
 *bSiguiente*  
 Indica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda es hacia el final del búfer. Si es FALSE, la dirección de búsqueda es hacia el principio del búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el *lpszFind* texto se encuentra; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función muestra el cursor de espera durante la operación de búsqueda.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]  
  
##  <a name="findtextsimple"></a>  CRichEditView::FindTextSimple  
 Llame a esta función para buscar el texto especificado y establece como la selección actual.  
  
```  
BOOL FindTextSimple(
    LPCTSTR lpszFind,  
    BOOL bCase = TRUE,  
    BOOL bWord = TRUE,  
    BOOL bNext = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFind*  
 Contiene la cadena de búsqueda.  
  
 *bCase*  
 Indica si la búsqueda distingue mayúsculas de minúsculas.  
  
 *bWord*  
 Indica si la búsqueda debe coincidir con palabras completas, no partes de palabras.  
  
 *bSiguiente*  
 Indica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda es hacia el final del búfer. Si es FALSE, la dirección de búsqueda es hacia el principio del búfer.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el *lpszFind* texto se encuentra; en caso contrario, 0.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::FindText](#findtext).  
  
##  <a name="getcharformatselection"></a>  CRichEditView::GetCharFormatSelection  
 Llame a esta función para obtener el formato de los atributos de la selección actual de caracteres.  
  
```  
CHARFORMAT2& GetCharFormatSelection();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) estructura que contiene el carácter de formato de los atributos de la selección actual.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte el [EM_GETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb788026) mensaje y el [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) estructura en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="getclipboarddata"></a>  CRichEditView::GetClipboardData  
 El marco de trabajo llama a esta función como parte del procesamiento de [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315).  
  
```  
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,  
    DWORD dwReco,  
    LPDATAOBJECT lpRichDataObj,  
    LPDATAOBJECT* lplpdataobj);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpchrg*  
 Puntero a la [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura que especifica el intervalo de caracteres (y elementos OLE) para copiar en el objeto de datos especificado por *lplpdataobj*.  
  
 *dwReco*  
 Marca de operación del Portapapeles. Puede ser uno de estos valores.  
  
- RECO_COPY copiarla al Portapapeles.  
  
- RECO_CUT Cortar al Portapapeles.  
  
- Operación de arrastre RECO_DRAG (arrastrar y colocar).  
  
- Operación de colocar RECO_DROP (arrastrar y colocar).  
  
- RECO_PASTE pegar desde el Portapapeles.  
  
 *lpRichDataObj*  
 Puntero a un [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) control de edición de objeto que contiene los datos del Portapapeles de la amplia ( [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341)).  
  
 *lplpdataobj*  
 Puntero a la variable de puntero que recibe la dirección de la `IDataObject` objeto que representa el intervalo especificado en el *lpchrg* parámetro. El valor de *lplpdataobj* se omite si se devuelve un error.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT reporting el éxito de la operación. Para obtener más información sobre el valor HRESULT, vea [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor devuelto indica éxito, `IRichEditOleCallback::GetClipboardData` devuelve el `IDataObject` accediendo a *lplpdataobj*; en caso contrario, devuelve el acceso a *lpRichDataObj*. Reemplace esta función para proporcionar sus propios datos del Portapapeles. La implementación predeterminada de esta función devuelve E_NOTIMPL.  
  
 Esto es un avanzado que se puede invalidar.  
  
 Para obtener más información, consulte [IRichEditOle::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774341), [IRichEditOleCallback::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/bb774315), y [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) en el SDK de Windows y vea [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) en el SDK de Windows.  
  
##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu  
 El marco de trabajo llama a esta función como parte del procesamiento de [IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317).  
  
```  
virtual HMENU GetContextMenu(
    WORD seltyp,  
    LPOLEOBJECT lpoleobj,  
    CHARRANGE* lpchrg);
```  
  
### <a name="parameters"></a>Parámetros  
 *seltyp*  
 El tipo de selección. Los valores de tipo de selección se describen en la sección Comentarios.  
  
 *lpoleobj*  
 Puntero a un `OLEOBJECT` estructura que especifica el primer objeto OLE seleccionado si la selección contiene uno o varios elementos OLE. Si la selección no contiene ningún elemento, *lpoleobj* es NULL. El `OLEOBJECT` estructura contiene un puntero a un objeto OLE v-table.  
  
 *lpchrg*  
 Puntero a un [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) estructura que contiene la selección actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Identificador del menú contextual.  
  
### <a name="remarks"></a>Comentarios  
 Esta función es una parte habitual de la derecha del botón del mouse hacia abajo de procesamiento.  
  
 El tipo de selección puede ser cualquier combinación de las marcas siguientes:  
  
- SEL_EMPTY indica que no hay ninguna selección actual.  
  
- SEL_TEXT indica que la selección actual contiene texto.  
  
- SEL_OBJECT indica que la selección actual contiene al menos un elemento OLE.  
  
- SEL_MULTICHAR indica que la selección actual contiene más de un carácter de texto.  
  
- SEL_MULTIOBJECT indica que la selección actual contiene más de un objeto OLE.  
  
 La implementación predeterminada devuelve NULL. Esto es un avanzado que se puede invalidar.  
  
 Para obtener más información, consulte [IRichEditOleCallback::GetContextMenu](http://msdn.microsoft.com/library/windows/desktop/bb774317) y [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) en el SDK de Windows.  
  
 Para obtener más información sobre la `OLEOBJECT` , vea el artículo de estructuras de datos OLE y asignar la estructura de la *OLE Knowledge Base*.  
  
##  <a name="getdocument"></a>  CRichEditView::GetDocument  
 Llame a esta función para obtener un puntero a la `CRichEditDoc` asociado con esta vista.  
  
```  
CRichEditDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) objeto asociado con su `CRichEditView` objeto.  
  
##  <a name="getinplaceactiveitem"></a>  CRichEditView::GetInPlaceActiveItem  
 Llamada a esta función para obtener la OLE de elementos que actualmente se activa en lugar de esto `CRichEditView` objeto.  
  
```  
CRichEditCntrItem* GetInPlaceActiveItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a único, en contexto activo [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto en esta vista de rich edit; NULL si no hay ningún elemento OLE actualmente en estado activo en contexto.  
  
##  <a name="getmargins"></a>  CRichEditView::GetMargins  
 Llame a esta función para recuperar los márgenes actuales que se usan en la impresión.  
  
```  
CRect GetMargins() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los márgenes de impresión, medido en MM_TWIPS.  
  
##  <a name="getpagerect"></a>  CRichEditView::GetPageRect  
 Llame a esta función para obtener las dimensiones de la página usada en la impresión.  
  
```  
CRect GetPageRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los límites de la página usada en la impresión, medido en MM_TWIPS.  
  
### <a name="remarks"></a>Comentarios  
 Este valor se basa en el tamaño del papel.  
  
##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize  
 Llame a esta función para recuperar el tamaño de papel actual.  
  
```  
CSize GetPaperSize() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El tamaño del papel que se usan en la impresión, medido en MM_TWIPS.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]  
  
##  <a name="getparaformatselection"></a>  CRichEditView::GetParaFormatSelection  
 Llame a esta función para obtener los atributos de la selección actual de formato de párrafo.  
  
```  
PARAFORMAT2& GetParaFormatSelection();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) estructura que contiene los atributos de la selección actual de formato de párrafo.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [EM_GETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774182) mensaje y [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) estructura en el SDK de Windows.  
  
##  <a name="getprintrect"></a>  CRichEditView::GetPrintRect  
 Llame a esta función para recuperar los límites del área de impresión dentro del rectángulo de la página.  
  
```  
CRect GetPrintRect() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Los límites del área de imagen utilizado en la impresión, medido en MM_TWIPS.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]  
  
##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth  
 Llame a esta función para determinar el ancho del área de impresión.  
  
```  
int GetPrintWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del área de impresión, medido en MM_TWIPS.  
  
##  <a name="getricheditctrl"></a>  CRichEditView:: GetRichEditCtrl  
 Llame a esta función para recuperar el [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) objeto asociado con el `CRichEditView` objeto.  
  
```  
CRichEditCtrl& GetRichEditCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La `CRichEditCtrl` objeto para esta vista.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::FindText](#findtext).  
  
##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem  
 Llame a esta función para recuperar el elemento OLE (una `CRichEditCntrItem` objeto) seleccionado actualmente en este `CRichEditView` objeto.  
  
```  
CRichEditCntrItem* GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto seleccionado en el `CRichEditView` objeto; NULL si no hay ningún elemento seleccionado en esta vista.  
  
##  <a name="gettextlength"></a>  CRichEditView::GetTextLength  
 Llame a esta función para recuperar la longitud del texto de este `CRichEditView` objeto.  
  
```  
long GetTextLength() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud del texto de este `CRichEditView` objeto.  
  
##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx  
 Llame a esta función miembro para calcular la longitud del texto de este `CRichEditView` objeto.  
  
```  
long GetTextLengthEx(
    DWORD dwFlags,  
    UINT uCodePage = -1) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *dwFlags*  
 Valor que especifica el método que se usará para determinar la longitud del texto. Este miembro puede ser uno o varios de los valores enumeran en el miembro de las marcas de [GETTEXTLENGTHEX](http://msdn.microsoft.com/library/windows/desktop/bb787915) descritos en el SDK de Windows.  
  
 *uCodePage*  
 Página de códigos para la traducción (CP_ACP para página de códigos ANSI, 1200 para Unicode).  
  
### <a name="return-value"></a>Valor devuelto  
 El número de caracteres o bytes en el control de edición. Si se establecen marcas incompatibles *dwFlags*, esta función miembro devuelve E_INVALIDARG.  
  
### <a name="remarks"></a>Comentarios  
 `GetTextLengthEx` proporciona otras maneras de determinar la longitud del texto. Admite la funcionalidad de Rich Edit 2.0. Para obtener más información, consulte [acerca de los controles Rich Edit](http://msdn.microsoft.com/library/windows/desktop/bb787873) en el SDK de Windows.  
  
##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject  
 Llame a esta función para insertar el archivo especificado (como un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto) en una completa vista de edición.  
  
```  
void InsertFileAsObject(LPCTSTR lpszFileName);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFileName*  
 Cadena que contiene el nombre del archivo que se va a insertar.  
  
##  <a name="insertitem"></a>  CRichEditView::InsertItem  
 Llame a esta función para insertar un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto en una vista de edición enriquecida.  
  
```  
HRESULT InsertItem(CRichEditCntrItem* pItem);
```  
  
### <a name="parameters"></a>Parámetros  
 *pItem*  
 Puntero al elemento que se va a insertar.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT que indica el éxito de la inserción.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre el valor HRESULT, vea [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) en el SDK de Windows.  
  
##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat  
 Llame a esta función para determinar si *cf* es un formato de Portapapeles que es texto, texto enriquecido o texto enriquecido con elementos OLE.  
  
```  
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```  
  
### <a name="parameters"></a>Parámetros  
 *CF*  
 El formato del Portapapeles de interés.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si *cf* es un formato de Portapapeles de edición o de texto enriquecido.  
  
##  <a name="isselected"></a>  CRichEditView::IsSelected  
 Llame a esta función para determinar si el elemento OLE especificado está actualmente seleccionado en esta vista.  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pDocItem*  
 Puntero a un objeto en la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el objeto está seleccionado; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si la clase de vista derivada tiene un método diferente para controlar la selección de elementos OLE.  
  
##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent  
 La sangría para los elementos de viñeta en una lista; de forma predeterminada, 720 unidades, que es 1/2 pulgada.  
  
```  
int m_nBulletIndent;  
```  
  
##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap  
 Indica el tipo de ajuste de línea para esta vista de rich edit.  
  
```  
int m_nWordWrap;  
```  
  
### <a name="remarks"></a>Comentarios  
 Uno de los siguientes valores:  
  
- `WrapNone` No indica ningún ajuste automático.  
  
- `WrapToWindow` Indica el ajuste de línea según el ancho de la ventana.  
  
- `WrapToTargetDevice` Indica el ajuste de líneas según las características del dispositivo de destino.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::WrapChanged](#wrapchanged).  
  
##  <a name="onchareffect"></a>  CRichEditView::OnCharEffect  
 Llame a esta función para alternar el formato de los efectos de la selección actual de caracteres.  
  
```  
void OnCharEffect(
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwMask*  
 El formato de los efectos de modificar en la selección actual de caracteres.  
  
 *dwEffect*  
 La lista deseada de los efectos de alternar de formato de caracteres.  
  
### <a name="remarks"></a>Comentarios  
 Cada llamada a esta función se activa o desactiva los efectos de formato especificados para la selección actual.  
  
 Para obtener más información sobre la *dwMask* y *dwEffect* parámetros y sus valores posibles, vea los miembros de datos correspondientes de [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]  
  
##  <a name="onfindnext"></a>  CRichEditView::OnFindNext  
 Lo llama el marco de trabajo al procesar comandos desde el cuadro de diálogo Buscar y reemplazar.  
  
```  
virtual void OnFindNext(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFind*  
 Cadena que se va a buscar.  
  
 *bSiguiente*  
 La dirección de búsqueda: TRUE se indica abajo; Es FALSE, arriba.  
  
 *bCase*  
 Indica si la búsqueda distingue entre mayúsculas y minúsculas.  
  
 *bWord*  
 Indica si la búsqueda es hacer coincidir palabras completas solo o no.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para buscar texto en el `CRichEditView`. Reemplace esta función para modificar las características de búsqueda de la clase de vista derivada.  
  
##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate  
 Lo llama el marco de trabajo después de la vista se adjunta al documento en primer lugar, pero antes de la vista se muestra inicialmente.  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función llama a la [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) función miembro sin información de sugerencia (es decir, usando los valores predeterminados de 0 para el *lHint* parámetro y NULL para el *pHint* parámetro). Reemplace esta función para realizar cualquier inicialización única que requiere información sobre el documento. Por ejemplo, si la aplicación tiene documentos de tamaño fijo, puede usar esta función para inicializar los límites de una vista desplazable según el tamaño del documento. Si la aplicación admite documentos de tamaño variable, use `OnUpdate` actualizar el desplazamiento limita cada hora los cambios del documento.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::m_nWordWrap](#m_nwordwrap).  
  
##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject  
 Utilice esta función para cargar datos nativos de un elemento incrustado.  
  
```  
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpStg*  
 Puntero a un [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se realiza correctamente; en caso contrario, 0;  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, ello mediante la creación de un [COleStreamFile](../../mfc/reference/colestreamfile-class.md) en torno a la `IStorage`. El `COleStreamFile` pueden asociarse a un archivo y [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) se llama para cargar los datos.  
  
 Esto es un avanzado que se puede invalidar.  
  
 Para obtener más información, consulte [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015) en el SDK de Windows.  
  
##  <a name="onparaalign"></a>  CRichEditView::OnParaAlign  
 Llame a esta función para cambiar la alineación del párrafo para los párrafos seleccionados.  
  
```  
void OnParaAlign(WORD wAlign);
```  
  
### <a name="parameters"></a>Parámetros  
 *wAlign*  
 Alineación del párrafo deseado. Uno de los siguientes valores:  
  
- PFA_LEFT alinear los párrafos con el margen izquierdo.  
  
- PFA_RIGHT alinear los párrafos con el margen derecho.  
  
- PFA_CENTER del centro de los párrafos entre los márgenes.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]  
  
##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged  
 Reemplace esta función para cambiar las características de esta vista de rich edit cuando cambia la impresora.  
  
```  
virtual void OnPrinterChanged(const CDC& dcPrinter);
```  
  
### <a name="parameters"></a>Parámetros  
 *dcPrinter*  
 Un [CDC](../../mfc/reference/cdc-class.md) objeto para la nueva impresora.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada establece el tamaño del papel en el físico alto y ancho para el dispositivo de salida (impresora). Si no hay ningún contexto de dispositivo asociado *dcPrinter*, la implementación predeterminada establece el tamaño del papel y 8,5 por 11 pulgadas.  
  
##  <a name="onreplaceall"></a>  CRichEditView::OnReplaceAll  
 Lo llama el marco de trabajo al procesar comandos reemplazar todo en el cuadro de diálogo Reemplazar.  
  
```  
virtual void OnReplaceAll(
    LPCTSTR lpszFind,  
    LPCTSTR lpszReplace,  
    BOOL bCase,  
    BOOL bWord);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFind*  
 El texto que se debe reemplazar.  
  
 *lpszReplace*  
 El texto de reemplazo.  
  
 *bCase*  
 Indica si la búsqueda distingue mayúsculas de minúsculas.  
  
 *bWord*  
 Indica si la búsqueda debe seleccionar palabras completas o no.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para reemplazar todas las apariciones del texto especificado por otra cadena. Reemplace esta función para modificar las características de búsqueda para esta vista.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::FindText](#findtext).  
  
##  <a name="onreplacesel"></a>  CRichEditView::OnReplaceSel  
 Lo llama el marco de trabajo al procesar los comandos de reemplazo en el cuadro de diálogo Reemplazar.  
  
```  
virtual void OnReplaceSel(
    LPCTSTR lpszFind,  
    BOOL bNext,  
    BOOL bCase,  
    BOOL bWord,  
    LPCTSTR lpszReplace);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFind*  
 El texto que se debe reemplazar.  
  
 *bSiguiente*  
 Indica la dirección de la búsqueda: TRUE si está presionada; Es FALSE, arriba.  
  
 *bCase*  
 Indica si la búsqueda distingue mayúsculas de minúsculas.  
  
 *bWord*  
 Indica si la búsqueda debe seleccionar palabras completas o no.  
  
 *lpszReplace*  
 El texto de reemplazo.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función para reemplazar una aparición del texto especificado por otra cadena. Reemplace esta función para modificar las características de búsqueda para esta vista.  
  
##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound  
 Lo llama el marco de trabajo cada vez que se produce un error en una búsqueda.  
  
```  
virtual void OnTextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFind*  
 El texto que no se encontró.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para cambiar la notificación de salida desde un [MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356).  
  
 Para obtener más información, consulte [MessageBeep](http://msdn.microsoft.com/library/windows/desktop/ms680356) en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]  
  
##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect  
 El marco de trabajo llama a esta función para actualizar el comando de la interfaz de usuario para los comandos de efecto de carácter.  
  
```  
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,  
    DWORD dwMask,  
    DWORD dwEffect);
```  
  
### <a name="parameters"></a>Parámetros  
 *pCmdUI*  
 Puntero a un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto.  
  
 *dwMask*  
 Indica el carácter de máscara de formato.  
  
 *dwEffect*  
 Indica el efecto de formato de caracteres.  
  
### <a name="remarks"></a>Comentarios  
 La máscara *dwMask* especifica qué carácter atributos de formato para comprobar. Las marcas de *dwEffect* el formato de atributos para establecer o borrar de caracteres de la lista.  
  
 Para obtener más información sobre la *dwMask* y *dwEffect* parámetros y sus valores posibles, vea los miembros de datos correspondientes de [CHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787881) en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]  
  
##  <a name="onupdateparaalign"></a>  CRichEditView::OnUpdateParaAlign  
 El marco de trabajo llama a esta función para actualizar el comando de la interfaz de usuario para los comandos de efecto del párrafo.  
  
```  
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,  
    WORD wAlign);
```  
  
### <a name="parameters"></a>Parámetros  
 *pCmdUI*  
 Puntero a un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto.  
  
 *wAlign*  
 Para comprobar la alineación del párrafo. Uno de los siguientes valores:  
  
- PFA_LEFT alinear los párrafos con el margen izquierdo.  
  
- PFA_RIGHT alinear los párrafos con el margen derecho.  
  
- PFA_CENTER del centro de los párrafos entre los márgenes.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]  
  
##  <a name="printinsiderect"></a>  CRichEditView::PrintInsideRect  
 Llame a esta función para dar formato a un intervalo de texto en un control rich edit a fin de ajustarse *rectLayout* para el dispositivo especificado por *pDC*.  
  
```  
long PrintInsideRect(
    CDC* pDC,  
    RECT& rectLayout,  
    long nIndexStart,  
    long nIndexStop,  
    BOOL bOutput);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDC*  
 Puntero a un contexto de dispositivo para el área de salida.  
  
 *rectLayout*  
 [RECT](../../mfc/reference/rect-structure1.md) o [CRect](../../atl-mfc-shared/reference/crect-class.md) que define el área de salida.  
  
 *nIndexStart*  
 Índice de base cero del primer carácter que se aplicará el formato.  
  
 *nIndexStop*  
 Índice de base cero del último carácter que se aplicará el formato.  
  
 *bOutput*  
 Indica si se debe representar el texto. Si es FALSE, solo se mide el texto.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del último carácter que se ajusta en el área de salida más uno.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, esta llamada es seguida por una llamada a [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) que genera el resultado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::GetPaperSize](#getpapersize).  
  
##  <a name="printpage"></a>  CRichEditView::PrintPage  
 Llame a esta función para dar formato a un intervalo de texto en un control rich edit para el dispositivo de salida especificado por *pDC*.  
  
```  
long PrintPage(
    CDC* pDC,  
    long nIndexStart,  
    long nIndexStop);
```  
  
### <a name="parameters"></a>Parámetros  
 *pDC*  
 Puntero a un contexto de dispositivo para el resultado de la página.  
  
 *nIndexStart*  
 Índice de base cero del primer carácter que se aplicará el formato.  
  
 *nIndexStop*  
 Índice de base cero del último carácter que se aplicará el formato.  
  
### <a name="return-value"></a>Valor devuelto  
 El índice del último carácter que cabe en la página más uno.  
  
### <a name="remarks"></a>Comentarios  
 El diseño de cada página se controla mediante [GetPageRect](#getpagerect) y [GetPrintRect](#getprintrect). Normalmente, esta llamada es seguida por una llamada a [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) que genera el resultado.  
  
 Tenga en cuenta que los márgenes son con respecto a la página física, no en la página lógica. Por lo tanto, los márgenes de cero a menudo recortar el texto dado que muchas impresoras tienen las áreas que no pueden imprimirse en la página. Para evitar el recorte de texto, debe llamar a [SetMargins](#setmargins) y establezca los márgenes razonables antes de imprimir.  
  
##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData  
 Lo llama el marco para pegar un objeto en la edición enriquecida.  
  
```  
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,  
    CLIPFORMAT* lpcfFormat,  
    DWORD dwReco,  
    BOOL bReally,  
    HGLOBAL hMetaFile);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpdataobj*  
 Puntero a la [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421) a la consulta.  
  
 *lpcfFormat*  
 Puntero en el formato de datos aceptable.  
  
 *dwReco*  
 No usado.  
  
 *bReally*  
 Indica si debe continuar la operación de pegar o no.  
  
 *hMetaFile*  
 Identificador del metarchivo que se usa para dibujar el icono del elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor HRESULT reporting el éxito de la operación.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función para controlar la otra organización de elementos COM en la clase derivada de documento. Esto es un avanzado que se puede invalidar.  
  
 Para obtener más información sobre el valor HRESULT y `IDataObject`, consulte [estructura de códigos de Error COM](http://msdn.microsoft.com/library/windows/desktop/ms690088) y [IDataObject](http://msdn.microsoft.com/library/windows/desktop/ms688421), respectivamente, en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]  
  
##  <a name="setcharformat"></a>  CRichEditView::SetCharFormat  
 Llame a esta función para establecer los atributos de texto nuevo en este formato de caracteres `CRichEditView` objeto.  
  
```  
void SetCharFormat(CHARFORMAT2 cf);
```  
  
### <a name="parameters"></a>Parámetros  
 *CF*  
 [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) estructura que contiene los atributos de formato de carácter predeterminado nuevo.  
  
### <a name="remarks"></a>Comentarios  
 Solo los atributos especificados por el `dwMask` miembro de *cf* se cambian por esta función.  
  
 Para obtener más información, consulte [EM_SETCHARFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774230) mensaje y [CHARFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787883) estructura en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]  
  
##  <a name="setmargins"></a>  CRichEditView::SetMargins  
 Llame a esta función para establecer los márgenes de impresión para esta vista de rich edit.  
  
```  
void SetMargins(const CRect& rectMargin);
```  
  
### <a name="parameters"></a>Parámetros  
 *rectMargin*  
 Los nuevos valores de margen para la impresión, medido en MM_TWIPS.  
  
### <a name="remarks"></a>Comentarios  
 Si [m_nWordWrap](#m_nwordwrap) es `WrapToTargetDevice`, debe llamar a [WrapChanged](#wrapchanged) después de usar esta función para ajustar las características de impresión.  
  
 Tenga en cuenta que usan los márgenes [PrintPage](#printpage) son relativas a la página física, no en la página lógica. Por lo tanto, los márgenes de cero a menudo recortar el texto dado que muchas impresoras tienen las áreas que no pueden imprimirse en la página. Para evitar el recorte de texto, debe llamar a uso `SetMargins` para establecer los márgenes de la impresora razonable antes de imprimir.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::GetPaperSize](#getpapersize).  
  
##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize  
 Llame a esta función para establecer el tamaño del papel para imprimir esta vista de rich edit.  
  
```  
void SetPaperSize(CSize sizePaper);
```  
  
### <a name="parameters"></a>Parámetros  
 *sizePaper*  
 Los nuevos valores de tamaño de papel para la impresión, medido en MM_TWIPS.  
  
### <a name="remarks"></a>Comentarios  
 Si [m_nWordWrap](#m_nwordwrap) es `WrapToTargetDevice`, debe llamar a [WrapChanged](#wrapchanged) después de usar esta función para ajustar las características de impresión.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]  
  
##  <a name="setparaformat"></a>  CRichEditView::SetParaFormat  
 Llame a esta función para establecer lo atributos de la selección actual en este formato de párrafo `CRichEditView` objeto.  
  
```  
BOOL SetParaFormat(PARAFORMAT2& pf);
```  
  
### <a name="parameters"></a>Parámetros  
 *PF*  
 [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) estructura que contiene el nuevo valor predeterminado de atributos de formato de párrafo.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se realiza correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Solo los atributos especificados por el `dwMask` miembro de *pf* se cambian por esta función.  
  
 Para obtener más información, consulte [EM_SETPARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb774276) mensaje y [PARAFORMAT2](http://msdn.microsoft.com/library/windows/desktop/bb787942) estructura en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]  
  
##  <a name="textnotfound"></a>  CRichEditView::TextNotFound  
 Llame a esta función para restablecer el estado interno de búsqueda de la [CRichEditView](../../mfc/reference/cricheditview-class.md) control después de un error de llamada a [FindText](#findtext).  
  
```  
void TextNotFound(LPCTSTR lpszFind);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpszFind*  
 Contiene la cadena de texto que no se encontró.  
  
### <a name="remarks"></a>Comentarios  
 Se recomienda que este método se llama inmediatamente después de las llamadas con error a [FindText](#findtext) para que el estado interno de búsqueda del control se restableció correctamente.  
  
 El *lpszFind* parámetro debe incluir el mismo contenido que la cadena proporcionada a [FindText](#findtext). Después de restablecer el estado de búsqueda interno, llamará este método la [OnTextNotFound](#ontextnotfound) método con la cadena de búsqueda proporcionado.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CRichEditView::FindText](#findtext).  
  
##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged  
 Llame a esta función cuando han cambiado las características de impresión ( [SetMargins](#setmargins) o [SetPaperSize](#setpapersize)).  
  
```  
virtual void WrapChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función para modificar el modo de vista de edición de la amplia responde a los cambios en el reemplazo [m_nWordWrap](#m_nwordwrap) o las características de impresión ( [OnPrinterChanged](#onprinterchanged)).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC WORDPAD](../../visual-cpp-samples.md)   
 [CCtrlView (clase)](../../mfc/reference/cctrlview-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRichEditDoc (clase)](../../mfc/reference/cricheditdoc-class.md)   
 [CRichEditCntrItem (clase)](../../mfc/reference/cricheditcntritem-class.md)
