---
title: Clase CRichEditView
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
ms.openlocfilehash: 2d832f3cc07d39ace9e679901c5344a376cea03c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318638"
---
# <a name="cricheditview-class"></a>Clase CRichEditView

Con [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control de edición enriquecida en el contexto de la arquitectura de vista de documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRichEditView::CrichEditView](#cricheditview)|Construye un objeto `CRichEditView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRichEditView::AdjustDialogPosition](#adjustdialogposition)|Mueve un cuadro de diálogo para que no oscurezca la selección actual.|
|[CRichEditView::CanPaste](#canpaste)|Indica si el Portapapeles contiene datos que se pueden pegar en la vista de edición enriquecida.|
|[CRichEditView::DoPaste](#dopaste)|Pega un elemento OLE en esta vista de edición enriquecida.|
|[CRichEditView::FindText](#findtext)|Busca el texto especificado, invocando el cursor de espera.|
|[CRichEditView::FindTextSimple](#findtextsimple)|Busca el texto especificado.|
|[CRichEditView::GetCharFormatSelection](#getcharformatselection)|Recupera los atributos de formato de caracteres para la selección actual.|
|[CRichEditView::GetDocument](#getdocument)|Recupera un puntero al [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)relacionado .|
|[CRichEditView::GetInPlaceActiveItem](#getinplaceactiveitem)|Recupera el elemento OLE que está activo actualmente en la vista de edición enriquecida.|
|[CRichEditView::GetMargins](#getmargins)|Recupera los márgenes de esta vista de edición enriquecida.|
|[CRichEditView::GetPageRect](#getpagerect)|Recupera el rectángulo de página para esta vista de edición enriquecida.|
|[CRichEditView::GetPaperSize](#getpapersize)|Recupera el tamaño de papel de esta vista de edición enriquecida.|
|[CRichEditView::GetParaFormatSelection](#getparaformatselection)|Recupera los atributos de formato de párrafo para la selección actual.|
|[CRichEditView::GetPrintRect](#getprintrect)|Recupera el rectángulo de impresión para esta vista de edición enriquecida.|
|[CRichEditView::GetPrintWidth](#getprintwidth)|Recupera el ancho de impresión de esta vista de edición enriquecida.|
|[CrichEditView::GetRichEditCtrl](#getricheditctrl)|Recupera el control rich edit.|
|[CRichEditView::GetSelectedItem](#getselecteditem)|Recupera el elemento seleccionado de la vista de edición enriquecida.|
|[CRichEditView::GetTextLength](#gettextlength)|Recupera la longitud del texto en la vista de edición enriquecida.|
|[CRichEditView::GetTextLengthEx](#gettextlengthex)|Recupera el número de caracteres o bytes en la vista de edición enriquecida. Lista de indicadores ampliada para el método de determinación de la longitud.|
|[CRichEditView::InsertFileAsObject](#insertfileasobject)|Inserta un archivo como un elemento OLE.|
|[CRichEditView::InsertItem](#insertitem)|Inserta un nuevo elemento como un elemento OLE.|
|[CrichEditView::IsRichEditFormat](#isricheditformat)|Indica si el Portapapeles contiene datos en un formato de texto o edición enriquecida.|
|[CrichEditView::OnCharEffect](#onchareffect)|Alterna el formato de caracteres para la selección actual.|
|[CrichEditView::OnParaalign](#onparaalign)|Cambia la alineación de los párrafos.|
|[CRichEditView::OnUpdateCharEffect](#onupdatechareffect)|Actualiza la interfaz de usuario de comandos para las funciones miembro públicas de caracteres.|
|[CrichEditView::OnUpdateParaalign](#onupdateparaalign)|Actualiza la interfaz de usuario de comandos para las funciones miembro públicas de párrafo.|
|[CRichEditView::PrintInsideRect](#printinsiderect)|Da formato al texto especificado dentro del rectángulo especificado.|
|[CRichEditView::PrintPage](#printpage)|Da formato al texto especificado dentro de la página especificada.|
|[CRichEditView::SetCharFormat](#setcharformat)|Establece los atributos de formato de caracteres para la selección actual.|
|[CRichEditView::SetMargins](#setmargins)|Establece los márgenes de esta vista de edición enriquecida.|
|[CRichEditView::SetPaperSize](#setpapersize)|Establece el tamaño de papel para esta vista de edición enriquecida.|
|[CRichEditView::SetParaformat](#setparaformat)|Establece los atributos de formato de párrafo para la selección actual.|
|[CrichEditView::TextNotFound](#textnotfound)|Restablece el estado de búsqueda interno del control.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CRichEditView::GetClipboardData](#getclipboarddata)|Recupera un objeto Portapapeles para un rango en esta vista de edición enriquecida.|
|[CRichEditView::GetContextMenu](#getcontextmenu)|Recupera un menú contextual para usarlo con el botón derecho del ratón hacia abajo.|
|[CRichEditView::IsSelected](#isselected)|Indica si el elemento OLE especificado está seleccionado o no.|
|[CrichEditView::OnFindNext](#onfindnext)|Busca la siguiente aparición de una subcadena.|
|[CRichEditView::OnInitialUpdate](#oninitialupdate)|Actualiza una vista cuando se adjunta por primera vez a un documento.|
|[CRichEditView::OnPasteNativeObject](#onpastenativeobject)|Recupera datos nativos de un elemento OLE.|
|[CRichEditView::OnPrinterChanged](#onprinterchanged)|Establece las características de impresión en el dispositivo especificado.|
|[CrichEditView::OnReplaceAll](#onreplaceall)|Reemplaza todas las apariciones de una cadena determinada con una nueva cadena.|
|[CRichEditView::OnReplaceSel](#onreplacesel)|Reemplaza la selección actual.|
|[CrichEditView::OnTextNotFound](#ontextnotfound)|Controla la notificación de usuario de que no se ha encontrado el texto solicitado.|
|[CRichEditView::QueryAcceptData](#queryacceptdata)|Consultas para ver los `IDataObject`datos en el archivo .|
|[CRichEditView::WrapChanged](#wrapchanged)|Ajusta el dispositivo de salida de destino para esta `m_nWordWrap`vista de edición enriquecida, en función del valor de .|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRichEditView::m_nBulletIndent](#m_nbulletindent)|Indica la cantidad de sangría para las listas de viñetas.|
|[CRichEditView::m_nWordWrap](#m_nwordwrap)|Indica las restricciones de ajuste de palabras.|

## <a name="remarks"></a>Observaciones

Un "control de edición enriquecido" es una ventana en la que el usuario puede introducir y editar texto. Al texto se le puede asignar formato de carácter y párrafo, y puede incluir objetos OLE incrustados. Los controles de edición enriquecidos proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de la interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario.

`CRichEditView`mantiene el texto y la característica de formato del texto. `CRichEditDoc`mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem`proporciona acceso del lado contenedor al elemento de cliente OLE.

Este control común de Windows (y, por lo tanto, [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y clases relacionadas) solo está disponible para los programas que se ejecutan en Windows 95/98 y Windows NT versiones 3.51 y posteriores.

Para obtener un ejemplo del uso de una vista de edición enriquecida en una aplicación MFC, vea la aplicación de ejemplo [WORDPAD.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrich.h

## <a name="cricheditviewadjustdialogposition"></a><a name="adjustdialogposition"></a>CRichEditView::AdjustDialogPosition

Llame a esta función para mover el cuadro de diálogo especificado para que no oscurezca la selección actual.

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>Parámetros

*pDlg*<br/>
Puntero a `CDialog` un objeto.

## <a name="cricheditviewcanpaste"></a><a name="canpaste"></a>CRichEditView::CanPaste

Llame a esta función para determinar si el Portapapeles contiene información que se puede pegar en esta vista de edición enriquecida.

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el Portapapeles contiene datos en un formato que esta vista de edición enriquecida puede aceptar; de lo contrario, 0.

## <a name="cricheditviewcricheditview"></a><a name="cricheditview"></a>CRichEditView::CrichEditView

Llame a esta `CRichEditView` función para crear un objeto.

```
CRichEditView();
```

## <a name="cricheditviewdopaste"></a><a name="dopaste"></a>CRichEditView::DoPaste

Llame a esta función para pegar el elemento OLE en *dataobj* en este documento de edición enriquecida/vista.

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>Parámetros

*dataobj*<br/>
El [COleDataObject](../../mfc/reference/coledataobject-class.md) que contiene los datos que se va a pegar.

*Cf*<br/>
El formato de Portapapeles deseado.

*hMetaPict*<br/>
El metarchivo que representa el elemento que se va a pegar.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función como parte de la implementación predeterminada de [QueryAcceptData](#queryacceptdata).

Esta función determina el tipo de pegado en función de los resultados del controlador para Pegado especial. Si *cf* es 0, el nuevo elemento utiliza la representación icónica actual. Si *cf* es distinto de cero y *hMetaPict* no es NULL, el nuevo elemento utiliza *hMetaPict* para su representación.

## <a name="cricheditviewfindtext"></a><a name="findtext"></a>CRichEditView::FindText

Llame a esta función para buscar el texto especificado y establecerlo como la selección actual.

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
Indica si la búsqueda distingue mayúsculas de minúsculas.

*bWord*<br/>
Indica si la búsqueda debe coincidir solo con palabras enteras, no con partes de palabras.

*bSiguiente*<br/>
Indica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda es hacia el final del búfer. Si FALSE, la dirección de búsqueda es hacia el principio del búfer.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el texto *lpszFind;* de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función muestra el cursor de espera durante la operación de búsqueda.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

## <a name="cricheditviewfindtextsimple"></a><a name="findtextsimple"></a>CRichEditView::FindTextSimple

Llame a esta función para buscar el texto especificado y establecerlo como la selección actual.

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
Indica si la búsqueda distingue mayúsculas de minúsculas.

*bWord*<br/>
Indica si la búsqueda debe coincidir solo con palabras enteras, no con partes de palabras.

*bSiguiente*<br/>
Indica la dirección de la búsqueda. Si es TRUE, la dirección de búsqueda es hacia el final del búfer. Si FALSE, la dirección de búsqueda es hacia el principio del búfer.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encuentra el texto *lpszFind;* de lo contrario 0.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetcharformatselection"></a><a name="getcharformatselection"></a>CRichEditView::GetCharFormatSelection

Llame a esta función para obtener los atributos de formato de caracteres de la selección actual.

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>Valor devuelto

Estructura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) que contiene los atributos de formato de caracteres de la selección actual.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea el [mensaje EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat) y la estructura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewgetclipboarddata"></a><a name="getclipboarddata"></a>CRichEditView::GetClipboardData

El marco de trabajo llama a esta función como parte del procesamiento de [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata).

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

- RECO_COPY Copiar en el Portapapeles.

- RECO_CUT Cortar al Portapapeles.

- RECO_DRAG Operación de arrastrar (arrastrar y soltar).

- RECO_DROP operación Drop (arrastrar y soltar).

- RECO_PASTE Pegar desde el Portapapeles.

*lpRichDataObj*<br/>
Puntero a un objeto [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) que contiene los datos del Portapapeles del control rich edit [(IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)).

*lplpdataobj*<br/>
Puntero a la variable de puntero `IDataObject` que recibe la dirección del objeto que representa el intervalo especificado en el parámetro *lpchrg.* El valor de *lplpdataobj* se omite si se devuelve un error.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT que informa del éxito de la operación. Para obtener más información sobre HRESULT, vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si el valor devuelto `IRichEditOleCallback::GetClipboardData` indica `IDataObject` que se ha realizado correctamente, devuelve el valor al que accede *lplpdataobj*; de lo contrario, devuelve el que tiene acceso *lpRichDataObj*. Reemplace esta función para proporcionar sus propios datos del Portapapeles. La implementación predeterminada de esta función devuelve E_NOTIMPL.

Este es un avanzado reemplazable.

Para obtener más información, vea [IRichEditOle::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata), [IRichEditOleCallback::GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)y [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) en el Windows SDK y vea [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) en el Windows SDK.

## <a name="cricheditviewgetcontextmenu"></a><a name="getcontextmenu"></a>CRichEditView::GetContextMenu

El marco de trabajo llama a esta función como parte del procesamiento de [IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu).

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>Parámetros

*seltyp*<br/>
El tipo de selección. Los valores de tipo de selección se describen en la sección Comentarios.

*lpoleobj*<br/>
Puntero a `OLEOBJECT` una estructura que especifica el primer objeto OLE seleccionado si la selección contiene uno o varios elementos OLE. Si la selección no contiene elementos, *lpoleobj* es NULL. La `OLEOBJECT` estructura contiene un puntero a una tabla v de objeto OLE.

*lpchrg*<br/>
Puntero a una estructura [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) que contiene la selección actual.

### <a name="return-value"></a>Valor devuelto

Controle el menú contextual.

### <a name="remarks"></a>Observaciones

Esta función es una parte típica del procesamiento del botón derecho del ratón hacia abajo.

El tipo de selección puede ser cualquier combinación de los siguientes indicadores:

- SEL_EMPTY Indica que no hay ninguna selección actual.

- SEL_TEXT Indica que la selección actual contiene texto.

- SEL_OBJECT Indica que la selección actual contiene al menos un elemento OLE.

- SEL_MULTICHAR Indica que la selección actual contiene más de un carácter de texto.

- SEL_MULTIOBJECT Indica que la selección actual contiene más de un objeto OLE.

La implementación predeterminada devuelve NULL. Este es un avanzado reemplazable.

Para obtener más información, vea [IRichEditOleCallback::GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) y [CHARRANGE](/windows/win32/api/richedit/ns-richedit-charrange) en el Windows SDK.

## <a name="cricheditviewgetdocument"></a><a name="getdocument"></a>CRichEditView::GetDocument

Llame a esta función `CRichEditDoc` para obtener un puntero a la asociada con esta vista.

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md) `CRichEditView` objeto asociado al objeto.

## <a name="cricheditviewgetinplaceactiveitem"></a><a name="getinplaceactiveitem"></a>CRichEditView::GetInPlaceActiveItem

Llame a esta función para obtener el elemento `CRichEditView` OLE que está activado actualmente en su lugar en este objeto.

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al único objeto [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) activo en su lugar en esta vista de edición enriquecida; NULL si no hay ningún elemento OLE actualmente en el estado activo en el lugar.

## <a name="cricheditviewgetmargins"></a><a name="getmargins"></a>CRichEditView::GetMargins

Llame a esta función para recuperar los márgenes actuales utilizados en la impresión.

```
CRect GetMargins() const;
```

### <a name="return-value"></a>Valor devuelto

Los márgenes utilizados en la impresión, medidos en MM_TWIPS.

## <a name="cricheditviewgetpagerect"></a><a name="getpagerect"></a>CRichEditView::GetPageRect

Llame a esta función para obtener las dimensiones de la página utilizada en la impresión.

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>Valor devuelto

Los límites de la página utilizada en la impresión, medidos en MM_TWIPS.

### <a name="remarks"></a>Observaciones

Este valor se basa en el tamaño del papel.

## <a name="cricheditviewgetpapersize"></a><a name="getpapersize"></a>CRichEditView::GetPaperSize

Llame a esta función para recuperar el tamaño de papel actual.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valor devuelto

El tamaño del papel utilizado en la impresión, medido en MM_TWIPS.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

## <a name="cricheditviewgetparaformatselection"></a><a name="getparaformatselection"></a>CRichEditView::GetParaFormatSelection

Llame a esta función para obtener los atributos de formato de párrafo de la selección actual.

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>Valor devuelto

Estructura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) que contiene los atributos de formato de párrafo de la selección actual.

### <a name="remarks"></a>Observaciones

Para obtener más información, vea [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) mensaje y la estructura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) en el Windows SDK.

## <a name="cricheditviewgetprintrect"></a><a name="getprintrect"></a>CRichEditView::GetPrintRect

Llame a esta función para recuperar los límites del área de impresión dentro del rectángulo de página.

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>Valor devuelto

Los límites del área de imagen utilizada en la impresión, medidos en MM_TWIPS.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

## <a name="cricheditviewgetprintwidth"></a><a name="getprintwidth"></a>CRichEditView::GetPrintWidth

Llame a esta función para determinar el ancho del área de impresión.

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>Valor devuelto

La anchura del área de impresión, medida en MM_TWIPS.

## <a name="cricheditviewgetricheditctrl"></a><a name="getricheditctrl"></a>CrichEditView::GetRichEditCtrl

Llame a esta función para recuperar el `CRichEditView` [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) objeto asociado con el objeto.

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>Valor devuelto

El `CRichEditCtrl` objeto de esta vista.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::FindText](#findtext).

## <a name="cricheditviewgetselecteditem"></a><a name="getselecteditem"></a>CRichEditView::GetSelectedItem

Llame a esta función para `CRichEditCntrItem` recuperar el elemento `CRichEditView` OLE (un objeto) seleccionado actualmente en este objeto.

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) `CRichEditView` objeto seleccionado en el objeto; NULL si no se selecciona ningún elemento en esta vista.

## <a name="cricheditviewgettextlength"></a><a name="gettextlength"></a>CRichEditView::GetTextLength

Llame a esta función para recuperar `CRichEditView` la longitud del texto en este objeto.

```
long GetTextLength() const;
```

### <a name="return-value"></a>Valor devuelto

La longitud del texto `CRichEditView` en este objeto.

## <a name="cricheditviewgettextlengthex"></a><a name="gettextlengthex"></a>CRichEditView::GetTextLengthEx

Llame a esta función miembro para `CRichEditView` calcular la longitud del texto en este objeto.

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Valor que especifica el método que se utilizará para determinar la longitud del texto. Este miembro puede ser uno o varios de los valores enumerados en el miembro flags de [GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex) descrito en el Windows SDK.

*uCodePage*<br/>
Página de códigos para traducción (CP_ACP para ansi página de códigos, 1200 para Unicode).

### <a name="return-value"></a>Valor devuelto

El número de caracteres o bytes en el control de edición. Si se establecieron marcas incompatibles en *dwFlags*, esta función miembro devuelve E_INVALIDARG.

### <a name="remarks"></a>Observaciones

`GetTextLengthEx`proporciona formas adicionales de determinar la longitud del texto. Es compatible con la funcionalidad Rich Edit 2.0. Para obtener más información, consulte Acerca de los controles de [edición enriquecidos](/windows/win32/Controls/about-rich-edit-controls) en el Windows SDK.

## <a name="cricheditviewinsertfileasobject"></a><a name="insertfileasobject"></a>CRichEditView::InsertFileAsObject

Llame a esta función para insertar el archivo especificado (como un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto) en una vista de edición enriquecida.

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Cadena que contiene el nombre del archivo que se va a insertar.

## <a name="cricheditviewinsertitem"></a><a name="insertitem"></a>CRichEditView::InsertItem

Llame a esta función para insertar un [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto en una vista de edición enriquecida.

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>Parámetros

*pItem*<br/>
Puntero al elemento que se va a insertar.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT que indica el éxito de la inserción.

### <a name="remarks"></a>Observaciones

Para obtener más información sobre HRESULT, vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes) en el Windows SDK.

## <a name="cricheditviewisricheditformat"></a><a name="isricheditformat"></a>CrichEditView::IsRichEditFormat

Llame a esta función para determinar si *cf* es un formato de Portapapeles que es texto, texto enriquecido o texto enriquecido con elementos OLE.

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>Parámetros

*Cf*<br/>
El formato del Portapapeles de interés.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si *cf* es una edición enriquecida o un formato de portapapeles de texto.

## <a name="cricheditviewisselected"></a><a name="isselected"></a>CRichEditView::IsSelected

Llame a esta función para determinar si el elemento OLE especificado está seleccionado actualmente en esta vista.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parámetros

*pDocItem*<br/>
Puntero a un objeto de la vista.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se selecciona el objeto; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Invalide esta función si la clase de vista derivada tiene un método diferente para controlar la selección de elementos OLE.

## <a name="cricheditviewm_nbulletindent"></a><a name="m_nbulletindent"></a>CRichEditView::m_nBulletIndent

La sangría para los elementos de viñeta en una lista; por defecto, 720 unidades, que es de 1/2 pulgada.

```
int m_nBulletIndent;
```

## <a name="cricheditviewm_nwordwrap"></a><a name="m_nwordwrap"></a>CRichEditView::m_nWordWrap

Indica el tipo de ajuste de palabras para esta vista de edición enriquecida.

```
int m_nWordWrap;
```

### <a name="remarks"></a>Observaciones

Uno de los valores siguientes:

- `WrapNone`Indica que no hay ajuste automático de palabras.

- `WrapToWindow`Indica el ajuste de palabras en función del ancho de la ventana.

- `WrapToTargetDevice`Indica el ajuste de palabras en función de las características del dispositivo de destino.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::WrapChanged](#wrapchanged).

## <a name="cricheditviewonchareffect"></a><a name="onchareffect"></a>CrichEditView::OnCharEffect

Llame a esta función para alternar los efectos de formato de caracteres para la selección actual.

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parámetros

*dwMask*<br/>
Los efectos de formato de caracteres que se modifican en la selección actual.

*dwEffect*<br/>
La lista deseada de efectos de formato de caracteres para alternar.

### <a name="remarks"></a>Observaciones

Cada llamada a esta función alterna los efectos de formato especificados para la selección actual.

Para obtener más información sobre los parámetros *dwMask* y *dwEffect* y sus valores potenciales, consulte los miembros de datos correspondientes de [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

## <a name="cricheditviewonfindnext"></a><a name="onfindnext"></a>CrichEditView::OnFindNext

Llamado por el marco de trabajo al procesar comandos desde el cuadro de diálogo Buscar/Reemplazar.

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Cadena que hay que buscar.

*bSiguiente*<br/>
La dirección de búsqueda: TRUE indica hacia abajo; FALSE, arriba.

*bCase*<br/>
Indica si la búsqueda debe distinguir entre mayúsculas y minúsculas.

*bWord*<br/>
Indica si la búsqueda debe coincidir solo con palabras enteras o no.

### <a name="remarks"></a>Observaciones

Llame a esta función `CRichEditView`para buscar texto dentro del archivo . Reemplace esta función para modificar las características de búsqueda de la clase de vista derivada.

## <a name="cricheditviewoninitialupdate"></a><a name="oninitialupdate"></a>CRichEditView::OnInitialUpdate

Llamado por el marco de trabajo después de que la vista se adjunta primero al documento, pero antes de que se muestre inicialmente la vista.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a la [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate) función miembro sin información de sugerencia (es decir, utilizando los valores predeterminados de 0 para el *lHint* parámetro y NULL para el *pHint* parámetro). Reemplace esta función para realizar cualquier inicialización única que requiera información sobre el documento. Por ejemplo, si la aplicación tiene documentos de tamaño fijo, puede usar esta función para inicializar los límites de desplazamiento de una vista en función del tamaño del documento. Si la aplicación admite documentos `OnUpdate` de tamaño variable, úselos para actualizar los límites de desplazamiento cada vez que cambie el documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::m_nWordWrap](#m_nwordwrap).

## <a name="cricheditviewonpastenativeobject"></a><a name="onpastenativeobject"></a>CRichEditView::OnPasteNativeObject

Utilice esta función para cargar datos nativos desde un elemento incrustado.

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>Parámetros

*lpStg*<br/>
Puntero a un objeto [IStorage.](/windows/win32/api/objidl/nn-objidl-istorage)

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario, 0;

### <a name="remarks"></a>Observaciones

Normalmente, esto se haría mediante la creación `IStorage`de un [COleStreamFile](../../mfc/reference/colestreamfile-class.md) alrededor del archivo . Se `COleStreamFile` puede adjuntar a un archivo y [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) llamado para cargar los datos.

Este es un avanzado reemplazable.

Para obtener más información, consulte [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) en el Windows SDK.

## <a name="cricheditviewonparaalign"></a><a name="onparaalign"></a>CrichEditView::OnParaalign

Llame a esta función para cambiar la alineación de párrafos para los párrafos seleccionados.

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>Parámetros

*wAlign*<br/>
Alineación de párrafo sin formato deseado. Uno de los valores siguientes:

- PFA_LEFT Alinee los párrafos con el margen izquierdo.

- PFA_RIGHT Alinee los párrafos con el margen derecho.

- PFA_CENTER Centrar los párrafos entre los márgenes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

## <a name="cricheditviewonprinterchanged"></a><a name="onprinterchanged"></a>CRichEditView::OnPrinterChanged

Reemplace esta función para cambiar las características de esta vista de edición enriquecida cuando cambie la impresora.

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>Parámetros

*dcPrinter*<br/>
Un objeto [CDC](../../mfc/reference/cdc-class.md) para la nueva impresora.

### <a name="remarks"></a>Observaciones

La implementación predeterminada establece el tamaño del papel en la altura física y la anchura del dispositivo de salida (impresora). Si no hay ningún contexto de dispositivo asociado con *dcPrinter*, la implementación predeterminada establece el tamaño del papel en 8,5 por 11 pulgadas.

## <a name="cricheditviewonreplaceall"></a><a name="onreplaceall"></a>CrichEditView::OnReplaceAll

Llamado por el marco de trabajo al procesar Reemplazar todo comandos desde el Reemplazar cuadro de diálogo.

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
El texto que se va a reemplazar.

*lpszReplace*<br/>
Texto de sustitución.

*bCase*<br/>
Indica si la búsqueda distingue mayúsculas de minúsculas.

*bWord*<br/>
Indica si la búsqueda debe seleccionar palabras enteras o no.

### <a name="remarks"></a>Observaciones

Llame a esta función para reemplazar todas las apariciones de un texto determinado con otra cadena. Reemplace esta función para modificar las características de búsqueda de esta vista.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::FindText](#findtext).

## <a name="cricheditviewonreplacesel"></a><a name="onreplacesel"></a>CRichEditView::OnReplaceSel

Llamado por el marco de trabajo al procesar Reemplazar comandos desde el Reemplazar cuadro de diálogo.

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
El texto que se va a reemplazar.

*bSiguiente*<br/>
Indica la dirección de la búsqueda: TRUE está inactivo; FALSE, arriba.

*bCase*<br/>
Indica si la búsqueda distingue mayúsculas de minúsculas.

*bWord*<br/>
Indica si la búsqueda debe seleccionar palabras enteras o no.

*lpszReplace*<br/>
Texto de sustitución.

### <a name="remarks"></a>Observaciones

Llame a esta función para reemplazar una aparición de un texto determinado con otra cadena. Reemplace esta función para modificar las características de búsqueda de esta vista.

## <a name="cricheditviewontextnotfound"></a><a name="ontextnotfound"></a>CrichEditView::OnTextNotFound

Llamado por el marco de trabajo cada vez que se produce un error en una búsqueda.

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
El texto que no se encontró.

### <a name="remarks"></a>Observaciones

Reemplace esta función para cambiar la notificación de salida de [messageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep).

Para obtener más información, consulte [MessageBeep](/windows/win32/api/winuser/nf-winuser-messagebeep) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

## <a name="cricheditviewonupdatechareffect"></a><a name="onupdatechareffect"></a>CRichEditView::OnUpdateCharEffect

El marco de trabajo llama a esta función para actualizar la interfaz de usuario de comandos para los comandos de efecto de carácter.

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto.

*dwMask*<br/>
Indica la máscara de formato de caracteres.

*dwEffect*<br/>
Indica el efecto de formato de caracteres.

### <a name="remarks"></a>Observaciones

La máscara *dwMask* especifica qué atributos de formato de caracteres se deben comprobar. Las marcas *dwEffect* enumeran los atributos de formato de caracteres que se han establecido o claros.

Para obtener más información sobre los parámetros *dwMask* y *dwEffect* y sus valores potenciales, consulte los miembros de datos correspondientes de [CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

## <a name="cricheditviewonupdateparaalign"></a><a name="onupdateparaalign"></a>CrichEditView::OnUpdateParaalign

El marco de trabajo llama a esta función para actualizar la interfaz de usuario de comandos para los comandos de efecto de párrafo.

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>Parámetros

*pCmdUI*<br/>
Puntero a un [CCmdUI](../../mfc/reference/ccmdui-class.md) objeto.

*wAlign*<br/>
La alineación de párrafos que se debe comprobar. Uno de los valores siguientes:

- PFA_LEFT Alinee los párrafos con el margen izquierdo.

- PFA_RIGHT Alinee los párrafos con el margen derecho.

- PFA_CENTER Centrar los párrafos entre los márgenes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

## <a name="cricheditviewprintinsiderect"></a><a name="printinsiderect"></a>CRichEditView::PrintInsideRect

Llame a esta función para dar formato a un intervalo de texto en un control de edición enriquecido para que quepa dentro de *rectLayout* para el dispositivo especificado por *pDC*.

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
[RECT](/windows/win32/api/windef/ns-windef-rect) o [CRect](../../atl-mfc-shared/reference/crect-class.md) que define el área de salida.

*nIndexStart*<br/>
El índice de base cero del primer carácter que se va a formatear.

*nIndexStop*<br/>
El índice de base cero del último carácter que se va a formatear.

*bOutput*<br/>
Indica si se debe representar el texto. Si FALSE, el texto se acaba de medir.

### <a name="return-value"></a>Valor devuelto

El índice del último carácter que cabe en el área de salida más uno.

### <a name="remarks"></a>Observaciones

Normalmente, esta llamada va seguida de una llamada a [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) que genera la salida.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewprintpage"></a><a name="printpage"></a>CRichEditView::PrintPage

Llame a esta función para dar formato a un intervalo de texto en un control de edición enriquecido para el dispositivo de salida especificado por *pDC*.

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero a un contexto de dispositivo para la salida de página.

*nIndexStart*<br/>
El índice de base cero del primer carácter que se va a formatear.

*nIndexStop*<br/>
El índice de base cero del último carácter que se va a formatear.

### <a name="return-value"></a>Valor devuelto

El índice del último carácter que cabe en la página más uno.

### <a name="remarks"></a>Observaciones

[GetPageRect](#getpagerect) y [GetPrintRect](#getprintrect)controlan el diseño de cada página. Normalmente, esta llamada va seguida de una llamada a [CRichEditCtrl::DisplayBand](../../mfc/reference/cricheditctrl-class.md#displayband) que genera la salida.

Tenga en cuenta que los márgenes son relativos a la página física, no a la página lógica. Por lo tanto, los márgenes de cero a menudo recortarán el texto ya que muchas impresoras tienen áreas no imprimibles en la página. Para evitar recortar el texto, debe llamar a [SetMargins](#setmargins) y establecer márgenes razonables antes de imprimir.

## <a name="cricheditviewqueryacceptdata"></a><a name="queryacceptdata"></a>CRichEditView::QueryAcceptData

Llamado por el marco de trabajo para pegar un objeto en la edición enriquecida.

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
Puntero a [iDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) para consultar.

*lpcfFormat*<br/>
Puntero al formato de datos aceptable.

*dwReco*<br/>
No se usa.

*bRealmente*<br/>
Indica si la operación de pegar debe continuar o no.

*hMetaFile*<br/>
Identificador del metarchivo utilizado para dibujar el icono del elemento.

### <a name="return-value"></a>Valor devuelto

Un valor HRESULT que informa del éxito de la operación.

### <a name="remarks"></a>Observaciones

Invalide esta función para controlar la organización diferente de los elementos COM en la clase de documento derivada. Este es un avanzado reemplazable.

Para obtener más información `IDataObject`sobre HRESULT y , vea [Estructura de códigos de error COM](/windows/win32/com/structure-of-com-error-codes) e [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject), respectivamente, en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

## <a name="cricheditviewsetcharformat"></a><a name="setcharformat"></a>CRichEditView::SetCharFormat

Llame a esta función para establecer los `CRichEditView` atributos de formato de caracteres para el nuevo texto en este objeto.

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>Parámetros

*Cf*<br/>
[Estructura CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) que contiene los nuevos atributos de formato de caracteres predeterminados.

### <a name="remarks"></a>Observaciones

Esta función sólo `dwMask` cambia los atributos especificados por el miembro de *cf.*

Para obtener más información, vea [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) mensaje y la estructura [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

## <a name="cricheditviewsetmargins"></a><a name="setmargins"></a>CRichEditView::SetMargins

Llame a esta función para establecer los márgenes de impresión para esta vista de edición enriquecida.

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>Parámetros

*rectMargin*<br/>
Los nuevos valores de margen para la impresión, medidos en MM_TWIPS.

### <a name="remarks"></a>Observaciones

Si [m_nWordWrap](#m_nwordwrap) m_nWordWrap `WrapToTargetDevice`es , debe llamar a [WrapChanged](#wrapchanged) después de utilizar esta función para ajustar las características de impresión.

Tenga en cuenta que los márgenes utilizados por [PrintPage](#printpage) son relativos a la página física, no a la página lógica. Por lo tanto, los márgenes de cero a menudo recortarán el texto ya que muchas impresoras tienen áreas no imprimibles en la página. Para evitar el recorte del `SetMargins` texto, debe llamar a use para establecer márgenes de impresora razonables antes de imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::GetPaperSize](#getpapersize).

## <a name="cricheditviewsetpapersize"></a><a name="setpapersize"></a>CRichEditView::SetPaperSize

Llame a esta función para establecer el tamaño del papel para imprimir esta vista de edición enriquecida.

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>Parámetros

*sizePaper*<br/>
Los nuevos valores de tamaño de papel para la impresión, medidos en MM_TWIPS.

### <a name="remarks"></a>Observaciones

Si [m_nWordWrap](#m_nwordwrap) m_nWordWrap `WrapToTargetDevice`es , debe llamar a [WrapChanged](#wrapchanged) después de utilizar esta función para ajustar las características de impresión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

## <a name="cricheditviewsetparaformat"></a><a name="setparaformat"></a>CRichEditView::SetParaformat

Llame a esta función para establecer los `CRichEditView` atributos de formato de párrafo para la selección actual en este objeto.

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>Parámetros

*Pf*<br/>
[Estructura PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) que contiene los nuevos atributos de formato de párrafo predeterminados.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se realiza correctamente; de lo contrario, 0.

### <a name="remarks"></a>Observaciones

Esta función solo `dwMask` cambia los atributos especificados por el miembro de *pf.*

Para obtener más información, consulte [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) mensaje y la estructura [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

## <a name="cricheditviewtextnotfound"></a><a name="textnotfound"></a>CrichEditView::TextNotFound

Llame a esta función para restablecer el estado de búsqueda interno del control [CRichEditView](../../mfc/reference/cricheditview-class.md) después de una llamada con error a [FindText](#findtext).

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>Parámetros

*lpszFind*<br/>
Contiene la cadena de texto que no se encontró.

### <a name="remarks"></a>Observaciones

Se recomienda llamar a este método inmediatamente después de llamadas con error a [FindText](#findtext) para que el estado de búsqueda interno del control se restablezca correctamente.

El parámetro *lpszFind* debe incluir el mismo contenido que la cadena proporcionada a [FindText](#findtext). Después de restablecer el estado de búsqueda interno, este método llamará a la [OnTextNotFound](#ontextnotfound) método con la cadena de búsqueda proporcionada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CRichEditView::FindText](#findtext).

## <a name="cricheditviewwrapchanged"></a><a name="wrapchanged"></a>CRichEditView::WrapChanged

Llame a esta función cuando las características de impresión hayan cambiado ( [SetMargins](#setmargins) o [SetPaperSize](#setpapersize)).

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Observaciones

Reemplace esta función para modificar la forma en que la vista de edición enriquecida responde a los cambios en [m_nWordWrap](#m_nwordwrap) o a las características de impresión ( [OnPrinterChanged](#onprinterchanged)).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Clase CCtrlView](../../mfc/reference/cctrlview-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc (clase)](../../mfc/reference/cricheditdoc-class.md)<br/>
[Clase CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)
