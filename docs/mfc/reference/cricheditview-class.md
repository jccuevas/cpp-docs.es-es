---
title: CRichEditView (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: c8eba16779b837b33912006a2ff3b7cdfa73f1e6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502629"
---
# <a name="cricheditview-class"></a>CRichEditView (clase)

Con [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control Rich Edit en el contexto de la arquitectura de la vista del documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditView::CRichEditView](#cricheditview)|Construye un objeto `CRichEditView`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Mueve un cuadro de diálogo para que no oculte la selección actual.|
|[CRichEditView::CanPaste](#canpaste)|Indica si el Portapapeles contiene datos que se pueden pegar en la vista de edición enriquecida.|
|[CRichEditView::DoPaste](#dopaste)|Pega un elemento OLE en esta vista de edición enriquecida.|
|[CRichEditView::FindText](#findtext)|Busca el texto especificado e invoca el cursor de espera.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Busca el texto especificado.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Recupera los atributos de formato de caracteres de la selección actual.|
|[CRichEditView::GetDocument](#getdocument)|Recupera un puntero a la [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)relacionada.|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Recupera el elemento OLE actualmente activo en contexto en la vista de edición enriquecida.|
|[CRichEditView::GetMargins](#getmargins)|Recupera los márgenes para esta vista de edición enriquecida.|
|[CRichEditView::GetPageRect](#getpagerect)|Recupera el rectángulo de página para esta vista de edición enriquecida.|
|[CRichEditView::GetPaperSize](#getpapersize)|Recupera el tamaño de papel para esta vista de edición enriquecida.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Recupera los atributos de formato de párrafo para la selección actual.|
|[CRichEditView::GetPrintRect](#getprintrect)|Recupera el rectángulo de impresión para esta vista de edición enriquecida.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Recupera el ancho de impresión para esta vista de edición enriquecida.|
|[CRichEditView::GetRichEditCtrl](#getricheditctrl)|Recupera el control Rich Edit.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Recupera el elemento seleccionado de la vista de edición enriquecida.|
|[CRichEditView::GetTextLength](#gettextlength)|Recupera la longitud del texto en la vista de edición enriquecida.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Recupera el número de caracteres o bytes de la vista de edición enriquecida. Lista de marcas expandida para el método de determinación de la longitud.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Inserta un archivo como un elemento OLE.|
|[CRichEditView::InsertItem](#insertitem)|Inserta un nuevo elemento como elemento OLE.|
|[CRichEditView::IsRichEditFormat](#isricheditformat)|Indica si el Portapapeles contiene datos en un formato de edición o texto enriquecido.|
|[CRichEditView::OnCharEffect](#onchareffect)|Alterna el formato de caracteres de la selección actual.|
|[CRichEditView::OnParaAlign](#onparaalign)|Cambia la alineación de los párrafos.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Actualiza la interfaz de usuario de comandos para las funciones miembro públicas de caracteres.|
|[CRichEditView::OnUpdateParaAlign](#onupdateparaalign)|Actualiza la interfaz de usuario de comandos para las funciones miembro públicas de párrafo.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Da formato al texto especificado dentro del rectángulo especificado.|
|[CRichEditView::PrintPage](#printpage)|Da formato al texto especificado en la página especificada.|
|[CRichEditView::SetCharFormat](#setcharformat)|Establece los atributos de formato de caracteres de la selección actual.|
|[CRichEditView::SetMargins](#setmargins)|Establece los márgenes para esta vista de edición enriquecida.|
|[CRichEditView::SetPaperSize](#setpapersize)|Establece el tamaño de papel para esta vista de edición enriquecida.|
|[CRichEditView::SetParaFormat](#setparaformat)|Establece los atributos de formato de párrafo para la selección actual.|
|[CRichEditView::TextNotFound](#textnotfound)|Restablece el estado de búsqueda interno del control.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Recupera un objeto Clipboard para un intervalo en esta vista de Rich Edit.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Recupera un menú contextual para utilizarlo en un botón secundario del mouse.|
|[CRichEditView::IsSelected](#isselected)|Indica si el elemento OLE especificado está seleccionado o no.|
|[CRichEditView::OnFindNext](#onfindnext)|Busca la siguiente repetición de una subcadena.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Actualiza una vista la primera vez que se adjunta a un documento.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Recupera datos nativos de un elemento OLE.|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Establece las características de impresión en el dispositivo especificado.|
|[CRichEditView::OnReplaceAll](#onreplaceall)|Reemplaza todas las apariciones de una cadena determinada por una nueva cadena.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Reemplaza la selección actual.|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|Controla la notificación del usuario de que no se encontró el texto solicitado.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Consultas para ver los datos de `IDataObject`.|
|[CRichEditView::WrapChanged](#wrapchanged)|Ajusta el dispositivo de salida de destino para esta vista de edición enriquecida, en función del `m_nWordWrap`valor de.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Indica la cantidad de sangría de las listas de viñetas.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Indica las restricciones de ajuste de palabras.|

## <a name="remarks"></a>Comentarios

Un "control Rich Edit" es una ventana en la que el usuario puede escribir y editar texto. El texto puede tener asignado un formato de carácter y de párrafo, y puede incluir objetos OLE incrustados. Los controles Rich Edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario.

`CRichEditView`mantiene el texto y la característica de formato del texto. `CRichEditDoc`mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem`proporciona acceso de contenedor al elemento de cliente OLE.

Este control común de Windows (y, por tanto, la clase [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas) solo está disponible para programas que se ejecutan en Windows 95/98 y en las versiones 3,51 y posteriores de Windows NT.

Para obtener un ejemplo del uso de una vista de edición enriquecida en una aplicación MFC, vea la aplicación de ejemplo de [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrich. h

##  <a name="adjustdialogposition"></a>CRichEditView:: AdjustDialogPosition

Llame a esta función para desplace el cuadro de diálogo especificado de forma que no oculte la selección actual.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parámetros

*pDlg*<br/>
Puntero a un `CDialog` objeto.

##  <a name="canpaste"></a>CRichEditView:: CanPaste

Llame a esta función para determinar si el Portapapeles contiene información que se puede pegar en esta vista de edición enriquecida.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el Portapapeles contiene datos en un formato que puede aceptar esta vista de Rich Edit. de lo contrario, es 0.

##  <a name="cricheditview"></a>CRichEditView:: CRichEditView

Llame a esta función para crear `CRichEditView` un objeto.

```
CRichEditView();
```

##  <a name="dopaste"></a>CRichEditView::D oPaste

Llame a esta función para pegar el elemento OLE de *dataobj* en esta vista o documento de edición enriquecida.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parámetros

*dataobj*<br/>
[COleDataObject](../../mfc/reference/coledataobject-class.md) que contiene los datos que se van a pegar.

*cf*<br/>
Formato de Portapapeles deseado.

*hMetaPict*<br/>
Metarchivo que representa el elemento que se va a pegar.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función como parte de la implementación predeterminada de [QueryAcceptData](#queryacceptdata).

Esta función determina el tipo de pegado en función de los resultados del controlador para pegado especial. Si *CF* es 0, el nuevo elemento usa la representación de iconos actual. Si *CF* es distinto de cero y *HMETAPICT* no es null, el nuevo elemento usa *hMetaPict* para su representación.

##  <a name="findtext"></a>  CRichEditView::FindText

Llame a esta función para buscar el texto especificado y establézcalo como la selección actual.

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Contiene la cadena que se va a buscar.

*bCase*<br/>
Indica si la búsqueda distingue entre mayúsculas y minúsculas.

*bWord*<br/>
Indica si la búsqueda solo debe coincidir con palabras completas, no partes de palabras.

*bNext*<br/>
Indica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda está hacia el final del búfer. Si es FALSE, la dirección de búsqueda está hacia el principio del búfer.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el texto *lpszFind* ; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función muestra el cursor de espera durante la operación de búsqueda.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>CRichEditView:: FindTextSimple

Llame a esta función para buscar el texto especificado y establézcalo como la selección actual.

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Contiene la cadena que se va a buscar.

*bCase*<br/>
Indica si la búsqueda distingue entre mayúsculas y minúsculas.

*bWord*<br/>
Indica si la búsqueda solo debe coincidir con palabras completas, no partes de palabras.

*bNext*<br/>
Indica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda está hacia el final del búfer. Si es FALSE, la dirección de búsqueda está hacia el principio del búfer.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el texto *lpszFind* ; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: FindText](#findtext).

##  <a name="getcharformatselection"></a>CRichEditView:: GetCharFormatSelection

Llame a esta función para obtener los atributos de formato de caracteres de la selección actual.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Valor devuelto

Estructura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) que contiene los atributos de formato de caracteres de la selección actual.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea el mensaje [EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) y la estructura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>CRichEditView:: GetClipboardData

El marco de trabajo llama a esta función como parte del procesamiento de [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>Parámetros

*lpchrg*<br/>
Puntero a la estructura [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) que especifica el intervalo de caracteres (y elementos OLE) que se va a copiar en el objeto de datos especificado por *lplpdataobj*.

*dwReco*<br/>
Marca de operación del portapapeles. Puede ser uno de estos valores.

- RECO_COPY copiar en el portapapeles.

- RECO_CUT cortar en el portapapeles.

- Operación de arrastrar RECO_DRAG (arrastrar y colocar).

- Operación Drop RECO_DROP (arrastrar y colocar).

- RECO_PASTE pegar desde el portapapeles.

*lpRichDataObj*<br/>
Puntero a un objeto [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) que contiene los datos del Portapapeles del control Rich Edit ( [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Puntero a la variable de puntero que recibe la dirección del `IDataObject` objeto que representa el intervalo especificado en el parámetro *lpchrg* . El valor de *lplpdataobj* se omite si se devuelve un error.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT que informa de que la operación se ha realizado correctamente. Para obtener más información sobre HRESULT, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si el valor devuelto indica Success `IRichEditOleCallback::GetClipboardData` , `IDataObject` devuelve el al que tiene acceso *lplpdataobj*; de lo contrario, devuelve el que tiene acceso a *lpRichDataObj*. Invalide esta función para proporcionar sus propios datos del portapapeles. La implementación predeterminada de esta función devuelve E_NOTIMPL.

Se trata de un reemplazable avanzado.

Para obtener más información, vea [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)y [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) en el Windows SDK y vea [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) en el Windows SDK.

##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu

El marco de trabajo llama a esta función como parte del procesamiento de [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parámetros

*seltyp*<br/>
Tipo de selección. Los valores de tipo de selección se describen en la sección Comentarios.

*lpoleobj*<br/>
Puntero a una `OLEOBJECT` estructura que especifica el primer objeto OLE seleccionado si la selección contiene uno o varios elementos OLE. Si la selección no contiene ningún elemento, *lpoleobj* es NULL. La `OLEOBJECT` estructura contiene un puntero a una tabla v de objeto OLE.

*lpchrg*<br/>
Puntero a una estructura [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) que contiene la selección actual.

### <a name="return-value"></a>Valor devuelto

Identificador del menú contextual.

### <a name="remarks"></a>Comentarios

Esta función es una parte típica del procesamiento correcto del botón del mouse.

El tipo de selección puede ser cualquier combinación de las marcas siguientes:

- SEL_EMPTY indica que no hay ninguna selección actual.

- SEL_TEXT indica que la selección actual contiene texto.

- SEL_OBJECT indica que la selección actual contiene al menos un elemento OLE.

- SEL_MULTICHAR indica que la selección actual contiene más de un carácter de texto.

- SEL_MULTIOBJECT indica que la selección actual contiene más de un objeto OLE.

La implementación predeterminada devuelve NULL. Se trata de un reemplazable avanzado.

Para obtener más información, vea [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) y [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) en el Windows SDK.

##  <a name="getdocument"></a>CRichEditView:: GetDocument

Llame a esta función para obtener un puntero al `CRichEditDoc` objeto asociado a esta vista.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) asociado `CRichEditView` al objeto.

##  <a name="getinplaceactiveitem"></a>CRichEditView:: GetInPlaceActiveItem

Llame a esta función para obtener el elemento OLE actualmente activado en su lugar en este `CRichEditView` objeto.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) activo único en contexto en esta vista de edición enriquecida. Es NULL si no hay ningún elemento OLE actualmente en el estado activo en contexto.

##  <a name="getmargins"></a>CRichEditView:: GetMargins

Llame a esta función para recuperar los márgenes actuales usados en la impresión.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Valor devuelto

Los márgenes utilizados en la impresión, medidos en MM_TWIPS.

##  <a name="getpagerect"></a>CRichEditView:: GetPageRect

Llame a esta función para obtener las dimensiones de la página utilizada en la impresión.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Valor devuelto

Los límites de la página utilizada en la impresión, medidos en MM_TWIPS.

### <a name="remarks"></a>Comentarios

Este valor se basa en el tamaño del papel.

##  <a name="getpapersize"></a>  CRichEditView::GetPaperSize

Llame a esta función para recuperar el tamaño de papel actual.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valor devuelto

Tamaño del papel usado en la impresión, medido en MM_TWIPS.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>CRichEditView:: GetParaFormatSelection

Llame a esta función para obtener los atributos de formato de párrafo de la selección actual.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Valor devuelto

Estructura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) que contiene los atributos de formato de párrafo de la selección actual.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) Message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) Structure en el Windows SDK.

##  <a name="getprintrect"></a>CRichEditView:: GetPrintRect

Llame a esta función para recuperar los límites del área de impresión dentro del rectángulo de la página.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Valor devuelto

Límites del área de imagen utilizada en la impresión, medida en MM_TWIPS.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>  CRichEditView::GetPrintWidth

Llame a esta función para determinar el ancho del área de impresión.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Valor devuelto

Ancho del área de impresión, medido en MM_TWIPS.

##  <a name="getricheditctrl"></a>CRichEditView:: GetRichEditCtrl

Llame a esta función para recuperar el objeto [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) asociado `CRichEditView` al objeto.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

`CRichEditCtrl` Objeto de esta vista.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: FindText](#findtext).

##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem

Llame a esta función para recuperar el elemento OLE ( `CRichEditCntrItem` un objeto) seleccionado actualmente en `CRichEditView` este objeto.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un objeto [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) seleccionado en el `CRichEditView` objeto; Es NULL si no hay ningún elemento seleccionado en esta vista.

##  <a name="gettextlength"></a>CRichEditView:: GetTextLength

Llame a esta función para recuperar la longitud del texto de este `CRichEditView` objeto.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Valor devuelto

Longitud del texto de este `CRichEditView` objeto.

##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx

Llame a esta función miembro para calcular la longitud del texto de este `CRichEditView` objeto.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Valor que especifica el método que se va a utilizar para determinar la longitud del texto. Este miembro puede ser uno o varios de los valores enumerados en el miembro flags de [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) descrito en el Windows SDK.

*uCodePage*<br/>
Página de códigos para traducción (CP_ACP para la página de códigos ANSI, 1200 para Unicode).

### <a name="return-value"></a>Valor devuelto

Número de caracteres o bytes en el control de edición. Si se establecieron marcas incompatibles en *dwFlags*, esta función miembro devuelve E_INVALIDARG.

### <a name="remarks"></a>Comentarios

`GetTextLengthEx`proporciona formas adicionales de determinar la longitud del texto. Admite la funcionalidad Rich Edit 2,0. Para obtener más información, vea acerca de los [controles Rich Edit](/windows/win32/Controls/about-rich-edit-controls) en el Windows SDK.

##  <a name="insertfileasobject"></a>  CRichEditView::InsertFileAsObject

Llame a esta función para insertar el archivo especificado (como un objeto [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) ) en una vista de edición enriquecida.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que contiene el nombre del archivo que se va a insertar.

##  <a name="insertitem"></a>  CRichEditView::InsertItem

Llame a esta función para insertar un objeto [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) en una vista de edición enriquecida.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT que indica el éxito de la inserción.

### <a name="remarks"></a>Comentarios

Para obtener más información sobre HRESULT, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

##  <a name="isricheditformat"></a>  CRichEditView::IsRichEditFormat

Llame a esta función para determinar si *CF* es un formato de Portapapeles que es texto, texto enriquecido o texto enriquecido con elementos OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parámetros

*cf*<br/>
Formato de interés del portapapeles.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si *CF* es un formato de edición o portapapeles de texto enriquecido.

##  <a name="isselected"></a>CRichEditView:: IsSelected

Llame a esta función para determinar si el elemento OLE especificado está seleccionado actualmente en esta vista.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parámetros

*pDocItem*<br/>
Puntero a un objeto de la vista.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto está seleccionado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Invalide esta función si la clase de vista derivada tiene un método diferente para controlar la selección de elementos OLE.

##  <a name="m_nbulletindent"></a>  CRichEditView::m_nBulletIndent

Sangría para los elementos de viñeta de una lista; de forma predeterminada, 720 unidades, que es de 1/2 pulgadas.

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>  CRichEditView::m_nWordWrap

Indica el tipo de ajuste de palabra para esta vista de edición enriquecida.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Comentarios

Uno de los siguientes valores:

- `WrapNone`Indica que no hay ajuste automático de palabras.

- `WrapToWindow`Indica el ajuste de palabras basado en el ancho de la ventana.

- `WrapToTargetDevice`Indica el ajuste de palabras en función de las características del dispositivo de destino.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: WrapChanged](#wrapchanged).

##  <a name="onchareffect"></a>CRichEditView:: OnCharEffect

Llame a esta función para alternar los efectos de formato de caracteres de la selección actual.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parámetros

*dwMask*<br/>
Efectos de formato de caracteres que se van a modificar en la selección actual.

*dwEffect*<br/>
Lista deseada de efectos de formato de caracteres que se van a alternar.

### <a name="remarks"></a>Comentarios

Cada llamada a esta función alterna los efectos de formato especificados para la selección actual.

Para obtener más información sobre los parámetros *dwMask* y *dwEffect* y sus valores posibles, vea los miembros de datos correspondientes de [Charformat](/windows/win32/api/richedit/ns-richedit-_charformat) en el Windows SDK.

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

*lpszFind*<br/>
Cadena que se va a buscar.

*bNext*<br/>
Dirección en la que se va a buscar: TRUE indica Down; FALSE, arriba.

*bCase*<br/>
Indica si la búsqueda debe distinguir entre mayúsculas y minúsculas.

*bWord*<br/>
Indica si la búsqueda solo debe coincidir con palabras completas.

### <a name="remarks"></a>Comentarios

Llame a esta función para buscar texto dentro `CRichEditView`de. Invalide esta función para modificar las características de búsqueda de la clase de vista derivada.

##  <a name="oninitialupdate"></a>  CRichEditView::OnInitialUpdate

Lo llama el marco de trabajo después de adjuntar la vista por primera vez al documento, pero antes de que se muestre inicialmente la vista.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función llama a la función miembro [CView:: ALUpdate](../../mfc/reference/cview-class.md#onupdate) sin información de sugerencia (es decir, con los valores predeterminados de 0 para el parámetro *lHint* y null para el parámetro *pHint* ). Invalide esta función para realizar cualquier inicialización única que requiera información sobre el documento. Por ejemplo, si la aplicación tiene documentos de tamaño fijo, puede usar esta función para inicializar los límites de desplazamiento de una vista en función del tamaño del documento. Si la aplicación admite documentos de tamaño variable, use `OnUpdate` para actualizar los límites de desplazamiento cada vez que cambie el documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: m_nWordWrap](#m_nwordwrap).

##  <a name="onpastenativeobject"></a>  CRichEditView::OnPasteNativeObject

Utilice esta función para cargar datos nativos de un elemento incrustado.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parámetros

*lpStg*<br/>
Puntero a un objeto [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario, 0;

### <a name="remarks"></a>Comentarios

Normalmente, esto se haría creando un [COleStreamFile](../../mfc/reference/colestreamfile-class.md) alrededor de `IStorage`. Se puede adjuntar a un archivo y a [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize) llamado para cargar los datos. `COleStreamFile`

Se trata de un reemplazable avanzado.

Para obtener más información, consulte [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) en el Windows SDK.

##  <a name="onparaalign"></a>CRichEditView:: OnParaAlign

Llame a esta función para cambiar la alineación de los párrafos seleccionados.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parámetros

*wAlign*<br/>
Alineación de párrafo deseada. Uno de los siguientes valores:

- PFA_LEFT alinea los párrafos con el margen izquierdo.

- PFA_RIGHT alinea los párrafos con el margen derecho.

- PFA_CENTER Centre los párrafos entre los márgenes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>  CRichEditView::OnPrinterChanged

Invalide esta función para cambiar las características de esta vista de edición enriquecida cuando cambie la impresora.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parámetros

*dcPrinter*<br/>
Objeto [CDC](../../mfc/reference/cdc-class.md) para la nueva impresora.

### <a name="remarks"></a>Comentarios

La implementación predeterminada establece el tamaño de papel en el alto y el ancho físicos del dispositivo de salida (impresora). Si no hay ningún contexto de dispositivo asociado a *dcPrinter*, la implementación predeterminada establece el tamaño de papel en 8,5 por 11 pulgadas.

##  <a name="onreplaceall"></a>CRichEditView:: OnReplaceAll

Lo llama el marco de trabajo al procesar reemplazar todos los comandos desde el cuadro de diálogo reemplazar.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que se va a reemplazar.

*lpszReplace*<br/>
Texto de reemplazo.

*bCase*<br/>
Indica si la búsqueda distingue entre mayúsculas y minúsculas.

*bWord*<br/>
Indica si la búsqueda debe seleccionar palabras completas o no.

### <a name="remarks"></a>Comentarios

Llame a esta función para reemplazar todas las apariciones de un texto determinado por otra cadena. Invalide esta función para modificar las características de búsqueda de esta vista.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: FindText](#findtext).

##  <a name="onreplacesel"></a>CRichEditView:: OnReplaceSel

Lo llama el marco de trabajo al procesar los comandos reemplazar desde el cuadro de diálogo reemplazar.

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que se va a reemplazar.

*bNext*<br/>
Indica la dirección de la búsqueda: TRUE está inactivo; FALSE, arriba.

*bCase*<br/>
Indica si la búsqueda distingue entre mayúsculas y minúsculas.

*bWord*<br/>
Indica si la búsqueda debe seleccionar palabras completas o no.

*lpszReplace*<br/>
Texto de reemplazo.

### <a name="remarks"></a>Comentarios

Llame a esta función para reemplazar una aparición de algún texto determinado por otra cadena. Invalide esta función para modificar las características de búsqueda de esta vista.

##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound

Lo llama el marco de trabajo cada vez que se produce un error en una búsqueda.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Texto que no se encontró.

### <a name="remarks"></a>Comentarios

Invalide esta función para cambiar la notificación de salida de un [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Para obtener más información, vea [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>  CRichEditView::OnUpdateCharEffect

El marco de trabajo llama a esta función para actualizar la interfaz de usuario de comandos para los comandos de efecto de caracteres.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a un objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) .

*dwMask*<br/>
Indica la máscara de formato de caracteres.

*dwEffect*<br/>
Indica el efecto de formato de caracteres.

### <a name="remarks"></a>Comentarios

Mask *dwMask* especifica los atributos de formato de caracteres que se van a comprobar. Las marcas *dwEffect* muestran los atributos de formato de caracteres que se van a establecer o borrar.

Para obtener más información sobre los parámetros *dwMask* y *dwEffect* y sus valores posibles, vea los miembros de datos correspondientes de [Charformat](/windows/win32/api/richedit/ns-richedit-_charformat) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>CRichEditView:: OnUpdateParaAlign

El marco de trabajo llama a esta función para actualizar la interfaz de usuario de comandos para los comandos de efecto de párrafo.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a un objeto [CCmdUI](../../mfc/reference/ccmdui-class.md) .

*wAlign*<br/>
Alineación del párrafo que se va a comprobar. Uno de los siguientes valores:

- PFA_LEFT alinea los párrafos con el margen izquierdo.

- PFA_RIGHT alinea los párrafos con el margen derecho.

- PFA_CENTER Centre los párrafos entre los márgenes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>CRichEditView::P rintInsideRect

Llame a esta función para dar formato a un intervalo de texto en un control Rich Edit para que quepa en *rectLayout* para el dispositivo especificado por *pDC*.

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo para el área de salida.

*rectLayout*<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect) o [CRect](../../atl-mfc-shared/reference/crect-class.md) , que define el área de salida.

*nIndexStart*<br/>
Índice de base cero del primer carácter al que se va a dar formato.

*nIndexStop*<br/>
Índice de base cero del último carácter al que se va a dar formato.

*bOutput*<br/>
Indica si se debe representar el texto. Si es FALSE, el texto se mide simplemente.

### <a name="return-value"></a>Valor devuelto

Índice del último carácter que cabe en el área de salida más uno.

### <a name="remarks"></a>Comentarios

Normalmente, esta llamada va seguida de una llamada a [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) que genera el resultado.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: GetPaperSize](#getpapersize).

##  <a name="printpage"></a>CRichEditView::P rintPage

Llame a esta función para dar formato a un intervalo de texto en un control Rich Edit para el dispositivo de salida especificado por *pDC*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo para la salida de la página.

*nIndexStart*<br/>
Índice de base cero del primer carácter al que se va a dar formato.

*nIndexStop*<br/>
Índice de base cero del último carácter al que se va a dar formato.

### <a name="return-value"></a>Valor devuelto

Índice del último carácter que cabe en la página más uno.

### <a name="remarks"></a>Comentarios

El diseño de cada página está controlado por [GetPageRect](#getpagerect) y [GetPrintRect](#getprintrect). Normalmente, esta llamada va seguida de una llamada a [CRichEditCtrl::D isplayband](../../mfc/reference/cricheditctrl-class.md#displayband) que genera el resultado.

Tenga en cuenta que los márgenes son relativos a la página física, no a la página lógica. Por lo tanto, los márgenes de cero suelen recortar el texto, ya que muchas impresoras tienen áreas no imprimibles en la página. Para evitar recortar el texto, debe llamar a [SetMargins](#setmargins) y establecer márgenes razonables antes de imprimir.

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

Lo llama el marco de trabajo para pegar un objeto en la edición enriquecida.

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>Parámetros

*lpdataobj*<br/>
Puntero al [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) que se va a consultar.

*lpcfFormat*<br/>
Puntero al formato de datos aceptable.

*dwReco*<br/>
No se utiliza.

*bReally*<br/>
Indica si la operación de pegar debe continuar o no.

*hMetaFile*<br/>
Identificador del metarchivo que se usa para dibujar el icono del elemento.

### <a name="return-value"></a>Valor devuelto

Valor HRESULT que informa de que la operación se ha realizado correctamente.

### <a name="remarks"></a>Comentarios

Invalide esta función para administrar una organización diferente de elementos COM en la clase de documento derivada. Se trata de un reemplazable avanzado.

Para obtener más información sobre HRESULT `IDataObject`y, vea [estructura de los códigos de error com](/windows/win32/com/structure-of-com-error-codes) y [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), respectivamente, en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>CRichEditView:: SetCharFormat

Llame a esta función para establecer los atributos de formato de caracteres para el `CRichEditView` nuevo texto de este objeto.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parámetros

*cf*<br/>
Estructura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) que contiene los nuevos atributos de formato de caracteres predeterminados.

### <a name="remarks"></a>Comentarios

Esta función solo cambia los atributos `dwMask` especificados por el miembro de *CF* .

Para obtener más información, consulte [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) Message and [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) Structure en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>CRichEditView:: SetMargins

Llame a esta función para establecer los márgenes de impresión para esta vista de edición enriquecida.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parámetros

*rectMargin*<br/>
Nuevos valores de margen para la impresión, medidos en MM_TWIPS.

### <a name="remarks"></a>Comentarios

Si [m_nWordWrap](#m_nwordwrap) es `WrapToTargetDevice`, debe llamar a [WrapChanged](#wrapchanged) después de usar esta función para ajustar las características de impresión.

Tenga en cuenta que los márgenes utilizados por [PrintPage](#printpage) son relativos a la página física, no a la página lógica. Por lo tanto, los márgenes de cero suelen recortar el texto, ya que muchas impresoras tienen áreas no imprimibles en la página. Para evitar el recorte del texto, debe llamar `SetMargins` a use para establecer los márgenes de impresora razonables antes de imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: GetPaperSize](#getpapersize).

##  <a name="setpapersize"></a>  CRichEditView::SetPaperSize

Llame a esta función para establecer el tamaño del papel para imprimir esta vista de edición enriquecida.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parámetros

*sizePaper*<br/>
Los nuevos valores de tamaño de papel para la impresión, medidos en MM_TWIPS.

### <a name="remarks"></a>Comentarios

Si [m_nWordWrap](#m_nwordwrap) es `WrapToTargetDevice`, debe llamar a [WrapChanged](#wrapchanged) después de usar esta función para ajustar las características de impresión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>CRichEditView:: SetParaFormat

Llame a esta función para establecer los atributos de formato de párrafo para la selección `CRichEditView` actual de este objeto.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parámetros

*pf*<br/>
Estructura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) que contiene los nuevos atributos de formato de párrafo predeterminados.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función solo cambia los atributos `dwMask` especificados por el miembro de *PF* .

Para obtener más información, consulte [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) Message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) Structure en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>  CRichEditView::TextNotFound

Llame a esta función para restablecer el estado de búsqueda interno del control [CRichEditView](../../mfc/reference/cricheditview-class.md) después de una llamada errónea a [FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Contiene la cadena de texto que no se encontró.

### <a name="remarks"></a>Comentarios

Se recomienda llamar a este método inmediatamente después de las llamadas erróneas a [FindText](#findtext) para que el estado de búsqueda interno del control se restablezca correctamente.

El parámetro *lpszFind* debe incluir el mismo contenido que la cadena proporcionada a [FindText](#findtext). Después de restablecer el estado de búsqueda interna, este método llamará al método [OnTextNotFound](#ontextnotfound) con la cadena de búsqueda proporcionada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView:: FindText](#findtext).

##  <a name="wrapchanged"></a>  CRichEditView::WrapChanged

Llame a esta función cuando las características de impresión hayan cambiado ( [SetMargins](#setmargins) o [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Comentarios

Invalide esta función para modificar el modo en que la vista de edición enriquecida responde a los cambios de [m_nWordWrap](#m_nwordwrap) o de las características de impresión ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Vea también

[WORDPAD de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView (clase)](../../mfc/reference/cctrlview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc (clase)](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem (clase)](../../mfc/reference/cricheditcntritem-class.md)
