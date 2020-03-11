---
title: CView (clase)
ms.date: 11/04/2016
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
ms.openlocfilehash: f6be846e80209ce94c84222d61c37a7964baad03
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855546"
---
# <a name="cview-class"></a>CView (clase)

Proporciona la funcionalidad básica para las clases de vista definidas por el usuario.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Members

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CView:: CView](#cview)|Construye un objeto `CView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CView::D oPreparePrinting](#doprepareprinting)|Muestra el cuadro de diálogo Imprimir y crea el contexto de dispositivo de impresora. Llame a al invalidar la función miembro de `OnPreparePrinting`.|
|[CView:: GetDocument](#getdocument)|Devuelve el documento asociado a la vista.|
|[CView:: IsSelected](#isselected)|Comprueba si un elemento de documento está seleccionado. Necesario para la compatibilidad con OLE.|
|[CView:: OnDragEnter](#ondragenter)|Se llama cuando se arrastra un elemento por primera vez a la región de arrastrar y colocar de una vista.|
|[CView:: OnDragLeave](#ondragleave)|Se llama cuando un elemento arrastrado deja la región de arrastrar y colocar de una vista.|
|[CView:: OnDragOver](#ondragover)|Se le llama cuando se arrastra un elemento sobre el área de arrastrar y colocar de una vista.|
|[CView:: OnDragScroll](#ondragscroll)|Se llama para determinar si el cursor se arrastra en el área de desplazamiento de la ventana.|
|[CView:: Allocate](#ondrop)|Se llama cuando un elemento se ha colocado en la región de arrastrar y colocar de una vista, controlador predeterminado.|
|[CView:: OnDropEx](#ondropex)|Se llama cuando un elemento se ha colocado en la región de arrastrar y colocar de una vista, controlador principal.|
|[CView:: OnInitialUpdate](#oninitialupdate)|Se llama después de adjuntar una vista por primera vez a un documento.|
|[CView:: OnPrepareDC](#onpreparedc)|Se llama antes de llamar a la función miembro `OnDraw` para la presentación en pantalla o se llama a la función miembro `OnPrint` para la impresión o la vista previa de impresión.|
|[CView:: onscroll](#onscroll)|Se le llama cuando se arrastran elementos OLE más allá de los bordes de la vista.|
|[CView:: OnScrollBy](#onscrollby)|Se llama cuando se desplaza una vista que contiene elementos OLE en contexto activos.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CView:: OnActivateFrame](#onactivateframe)|Se llama cuando la ventana de marco que contiene la vista está activada o desactivada.|
|[CView:: OnActivateView](#onactivateview)|Se llama cuando se activa una vista.|
|[CView:: OnBeginPrinting](#onbeginprinting)|Se llama cuando comienza un trabajo de impresión; Invalide para asignar recursos de la interfaz de dispositivo gráfico (GDI).|
|[CView:: OnDraw](#ondraw)|Se llama para presentar una imagen del documento para la presentación en pantalla, la impresión o la vista previa de impresión. Implementación requerida.|
|[CView:: OnBeginPrinting](#onendprinting)|Se llama cuando finaliza un trabajo de impresión; Invalide para desasignar recursos GDI.|
|[CView:: OnEndPrintPreview](#onendprintpreview)|Se llama cuando se sale del modo de vista previa.|
|[CView:: OnPreparePrinting](#onprepareprinting)|Se llama antes de imprimir u obtener una vista previa de un documento; Invalide para inicializar el cuadro de diálogo Imprimir.|
|[CView:: OnPrint](#onprint)|Se llama para imprimir u obtener una vista previa de una página del documento.|
|[CView:: actualización](#onupdate)|Se llama para notificar a una vista que su documento se ha modificado.|

## <a name="remarks"></a>Observaciones

Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario: la vista representa una imagen del documento en la pantalla o la impresora e interpreta los datos proporcionados por el usuario como operaciones en el documento.

Una vista es un elemento secundario de una ventana de marco. Más de una vista puede compartir una ventana de marco, como en el caso de una ventana divisora. La relación entre una clase de vista, una clase de ventana de marco y una clase de documento se establece mediante un objeto `CDocTemplate`. Cuando el usuario abre una nueva ventana o divide una existente, el marco de trabajo crea una nueva vista y la adjunta al documento.

Una vista solo se puede adjuntar a un documento, pero un documento puede tener varias vistas asociadas a la vez, por ejemplo, si el documento se muestra en una ventana divisora o en varias ventanas secundarias en una aplicación de interfaz de múltiples documentos (MDI). La aplicación puede admitir distintos tipos de vistas para un tipo de documento determinado. por ejemplo, un programa de procesamiento de texto puede proporcionar una vista de texto completa de un documento y una vista de esquema que muestra solo los encabezados de la sección. Estos tipos diferentes de vistas se pueden colocar en ventanas de marco independientes o en paneles independientes de una sola ventana de marco si se usa una ventana divisora.

Una vista puede ser responsable de administrar distintos tipos de entrada, como la entrada mediante teclado, la entrada del mouse o la entrada a través de las acciones de arrastrar y colocar, así como los comandos de los menús, las barras de herramientas o las barras de desplazamiento. Una vista recibe los comandos reenviados por su ventana de marco. Si la vista no controla un comando determinado, reenvía el comando a su documento asociado. Al igual que todos los destinos de comando, una vista controla los mensajes a través de un mapa de mensajes.

La vista es responsable de mostrar y modificar los datos del documento, pero no de almacenarlos. El documento proporciona la vista con los detalles necesarios sobre sus datos. Puede permitir que la vista obtenga acceso a los miembros de datos del documento directamente, o bien puede proporcionar funciones miembro en la clase de documento para que llame a la clase de vista.

Cuando los datos de un documento cambian, la vista responsable de los cambios normalmente llama a la función [CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) del documento, que notifica a todas las demás vistas mediante una llamada a la función miembro `OnUpdate` para cada una de ellas. La implementación predeterminada de `OnUpdate` invalida el área de cliente completa de la vista. Puede invalidarlo para invalidar solo las regiones del área de cliente que se asignan a las partes modificadas del documento.

Para usar `CView`, derive una clase a partir de ella e implemente la función miembro `OnDraw` para realizar la presentación en pantalla. También puede utilizar `OnDraw` para realizar la impresión y la vista previa de impresión. El marco de trabajo controla el bucle de impresión para imprimir y obtener una vista previa del documento.

Una vista controla los mensajes de la barra de desplazamiento con las funciones miembro [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) . Puede implementar el control de mensajes de la barra de desplazamiento en estas funciones, o puede usar la `CView` clase derivada [CScrollView](../../mfc/reference/cscrollview-class.md) para controlar el desplazamiento.

Además de `CScrollView`, el biblioteca MFC proporciona nueve clases derivadas de `CView`:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), una vista que permite el uso de la arquitectura de vista de documento con controles de árbol, lista y edición enriquecida.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), una vista que muestra los registros de base de datos en los controles de cuadro de diálogo.

- [CEditView](../../mfc/reference/ceditview-class.md), una vista que proporciona un editor de texto de varias líneas simple. Puede utilizar un objeto `CEditView` como control en un cuadro de diálogo, así como una vista de un documento.

- [CFormView](../../mfc/reference/cformview-class.md), una vista desplazable que contiene controles de cuadro de diálogo y se basa en un recurso de plantilla de cuadro de diálogo.

- [CListView](../../mfc/reference/clistview-class.md), una vista que permite el uso de la arquitectura de vista de documento con controles de lista.

- [CRecordView](../../mfc/reference/crecordview-class.md), una vista que muestra los registros de base de datos en los controles de cuadro de diálogo.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), una vista que permite el uso de la arquitectura de vista de documento con controles Rich Edit.

- [CScrollView](../../mfc/reference/cscrollview-class.md), una vista que proporciona automáticamente compatibilidad con el desplazamiento.

- [CTreeView](../../mfc/reference/ctreeview-class.md), una vista que permite el uso de la arquitectura de vista de documento con controles de árbol.

La clase `CView` también tiene una clase de implementación derivada denominada `CPreviewView`, que usa el marco para realizar la vista previa de impresión. Esta clase proporciona compatibilidad con las características únicas de la ventana de vista previa de impresión, como una barra de herramientas, una vista previa de una o dos páginas y el zoom, es decir, el aumento de la imagen previsualizada. No es necesario llamar ni reemplazar ninguna de las funciones miembro de `CPreviewView`a menos que desee implementar su propia interfaz para la vista previa de impresión (por ejemplo, si desea admitir la edición en modo de vista previa de impresión). Para obtener más información sobre el uso de `CView`, vea [arquitectura de documento/vista](../../mfc/document-view-architecture.md) e [impresión](../../mfc/printing.md). Además, consulte la [Nota técnica 30](../../mfc/tn030-customizing-printing-and-print-preview.md) para obtener más detalles sobre cómo personalizar la vista previa de impresión.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cview"></a>CView:: CView

Construye un objeto `CView`.

```
CView();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama al constructor cuando se crea una nueva ventana de marco o se divide una ventana. Reemplace la función miembro [OnInitialUpdate](#oninitialupdate) para inicializar la vista después de adjuntar el documento.

##  <a name="doprepareprinting"></a>CView::D oPreparePrinting

Llame a esta función desde la invalidación de [OnPreparePrinting](#onprepareprinting) para invocar el cuadro de diálogo Imprimir y crear un contexto de dispositivo de impresora.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si puede comenzar la impresión o la vista previa de impresión; 0 si se ha cancelado la operación.

### <a name="remarks"></a>Observaciones

El comportamiento de esta función depende de si se llama para la impresión o la vista previa de impresión (especificada por el miembro `m_bPreview` del parámetro *Pinfo* ). Si se está imprimiendo un archivo, esta función invoca al cuadro de diálogo Imprimir, usando los valores de la estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) a los que apunta *Pinfo* ; una vez que el usuario ha cerrado el cuadro de diálogo, la función crea un contexto de dispositivo de impresora basado en los valores especificados por el usuario en el cuadro de diálogo y devuelve este contexto de dispositivo mediante el parámetro *Pinfo* . Este contexto de dispositivo se usa para imprimir el documento.

Si se está realizando una vista previa de un archivo, esta función crea un contexto de dispositivo de impresora con la configuración de impresora actual. este contexto de dispositivo se usa para simular la impresora durante la versión preliminar.

##  <a name="getdocument"></a>CView:: GetDocument

Llame a esta función para obtener un puntero al documento de la vista.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto [CDocument](../../mfc/reference/cdocument-class.md) asociado a la vista. NULL si la vista no está asociada a un documento.

### <a name="remarks"></a>Observaciones

Esto le permite llamar a las funciones miembro del documento.

##  <a name="isselected"></a>CView:: IsSelected

Lo llama el marco de trabajo para comprobar si el elemento de documento especificado está seleccionado.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parámetros

*pDocItem*<br/>
Apunta al elemento de documento que se está probando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el elemento de documento especificado está seleccionado; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función devuelve FALSE. Invalide esta función si está implementando la selección mediante objetos [CDocItem](../../mfc/reference/cdocitem-class.md) . Debe reemplazar esta función si la vista contiene elementos OLE.

##  <a name="onactivateframe"></a>CView:: OnActivateFrame

Lo llama el marco de trabajo cuando la ventana de marco que contiene la vista está activada o desactivada.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parámetros

*nState*<br/>
Especifica si la ventana de marco se está activando o desactivando. Puede ser uno de los siguientes valores:

- WA_INACTIVE la ventana de marco se está desactivando.

- WA_ACTIVE la ventana de marco se está activando a través de algún método que no sea un clic del mouse (por ejemplo, mediante la interfaz de teclado para seleccionar la ventana).

- WA_CLICKACTIVE la ventana de marco se está activando con un clic del mouse

*pFrameWnd*<br/>
Puntero a la ventana de marco que se va a activar.

### <a name="remarks"></a>Observaciones

Reemplace esta función miembro si desea realizar un procesamiento especial cuando la ventana de marco asociada a la vista esté activada o desactivada. Por ejemplo, [CFormView](../../mfc/reference/cformview-class.md) realiza esta invalidación cuando guarda y restaura el control que tiene el foco.

##  <a name="onactivateview"></a>CView:: OnActivateView

Lo llama el marco de trabajo cuando una vista está activada o desactivada.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parámetros

*bActivate*<br/>
Indica si la vista se está activando o desactivando.

*pActivateView*<br/>
Apunta al objeto de vista que se está activando.

*pDeactiveView*<br/>
Apunta al objeto de vista que se está desactivando.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función establece el foco en la vista que se está activando. Invalide esta función si desea realizar un procesamiento especial cuando una vista está activada o desactivada. Por ejemplo, si desea proporcionar indicaciones visuales especiales que distinguen la vista activa de las vistas inactivas, examinaría el parámetro *bActivate* y actualizaría la apariencia de la vista en consecuencia.

Los parámetros *pActivateView* y *pDeactiveView* apuntan a la misma vista si la ventana de marco principal de la aplicación se activa sin ningún cambio en la vista activa; por ejemplo, si el foco se transfiere desde otra aplicación a este, en lugar de hacerlo de una vista a otra dentro de la aplicación o al cambiar entre las ventanas secundarias MDI. Esto permite que una vista vuelva a obtener su paleta, si es necesario.

Estos parámetros se diferencian cuando se llama a [CFrameWnd:: SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) con una vista diferente de lo que devolvería [CFrameWnd:: GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) . Esto sucede con mayor frecuencia con ventanas divisoras.

##  <a name="onbeginprinting"></a>CView:: OnBeginPrinting

Lo llama el marco al comenzar un trabajo de impresión o de vista previa de impresión, después de llamar a `OnPreparePrinting` .

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto del dispositivo de impresora.

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada. Reemplace esta función para asignar los recursos de GDI, como lápices o fuentes, que se necesitan específicamente para imprimir. Seleccione los objetos GDI en el contexto del dispositivo dentro de la función miembro [OnPrint](#onprint) para cada página que los use. Si usa el mismo objeto de vista para realizar la presentación en pantalla y la impresión, use variables independientes para los recursos GDI necesarios para cada presentación; esto le permite actualizar la pantalla durante la impresión.

También puede usar esta función para realizar inicializaciones que dependan de las propiedades del contexto del dispositivo de impresora. Por ejemplo, el número de páginas necesarias para imprimir el documento puede depender de la configuración que especificó el usuario en el cuadro de diálogo Imprimir (por ejemplo, la longitud de la página). En esta situación, no puede especificar la longitud del documento en la función miembro [OnPreparePrinting](#onprepareprinting) , donde lo haría normalmente. Debe esperar a que se cree el contexto del dispositivo de impresora en función de la configuración del cuadro de diálogo. [OnBeginPrinting](#onbeginprinting) es la primera función reemplazable que proporciona acceso al objeto [CDC](../../mfc/reference/cdc-class.md) que representa el contexto del dispositivo de impresora, por lo que puede establecer la longitud del documento desde esta función. Tenga en cuenta que si no se especifica la longitud del documento en este momento, no se muestra una barra de desplazamiento durante la vista previa de impresión.

##  <a name="ondragenter"></a>CView:: OnDragEnter

Lo llama el marco de trabajo cuando el Mouse entra por primera vez en la región de no desplazamiento de la ventana de destino de colocación.

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pDataObject*<br/>
Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se arrastra en el área de colocación de la vista.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Elija*<br/>
La posición actual del mouse en relación con el área de cliente de la vista.

### <a name="return-value"></a>Valor devuelto

Un valor del tipo enumerado DROPEFFECT, que indica el tipo de colocación que se produciría si el usuario quitara el objeto en esta posición. Normalmente, el tipo de Drop depende del estado de la clave actual indicado por *dwKeyState*. Una asignación estándar de los valores de KeyStates a DROPEFFECT es:

- DROPEFFECT_NONE el objeto de datos no se puede quitar de esta ventana.

- DROPEFFECT_LINK para MK_CONTROL &#124; MK_SHIFT crea una vinculación entre el objeto y su servidor.

- DROPEFFECT_COPY para MK_CONTROL crea una copia del objeto colocado.

- DROPEFFECT_MOVE para MK_ALT crea una copia del objeto colocado y elimina el objeto original. Este suele ser el efecto de colocación predeterminado cuando la vista puede aceptar este objeto de datos.

Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Observaciones

La implementación predeterminada consiste en no hacer nada y devolver DROPEFFECT_NONE.

Invalide esta función para prepararse para futuras llamadas a la función miembro [OnDragOver](#ondragover) . Los datos necesarios del objeto de datos deben recuperarse en este momento para su uso posterior en la función miembro `OnDragOver`. La vista también debe actualizarse en este momento para proporcionar los comentarios visuales del usuario. Para obtener más información, vea el artículo [OLE arrastrar y colocar: implementar un destino de colocación](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragleave"></a>CView:: OnDragLeave

Lo llama el marco de trabajo durante una operación de arrastre cuando el mouse se mueve fuera del área de colocación válida para esa ventana.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Observaciones

Invalide esta función si la vista actual necesita limpiar las acciones realizadas durante las llamadas a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) , como quitar los comentarios de los usuarios visuales mientras se arrastra y se quita el objeto.

##  <a name="ondragover"></a>CView:: OnDragOver

Lo llama el marco de trabajo durante una operación de arrastre cuando el mouse se mueve sobre la ventana de destino de colocación.

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pDataObject*<br/>
Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se arrastra sobre el destino de colocación.

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Elija*<br/>
La posición actual del mouse en relación con el área de cliente de vista.

### <a name="return-value"></a>Valor devuelto

Un valor del tipo enumerado DROPEFFECT, que indica el tipo de colocación que se produciría si el usuario quitara el objeto en esta posición. El tipo de Drop suele depender del estado de la clave actual, según se indica en *dwKeyState*. Una asignación estándar de los valores de KeyStates a DROPEFFECT es:

- DROPEFFECT_NONE el objeto de datos no se puede quitar de esta ventana.

- DROPEFFECT_LINK para MK_CONTROL &#124; MK_SHIFT crea una vinculación entre el objeto y su servidor.

- DROPEFFECT_COPY para MK_CONTROL crea una copia del objeto colocado.

- DROPEFFECT_MOVE para MK_ALT crea una copia del objeto colocado y elimina el objeto original. Este suele ser el efecto de colocación predeterminado cuando la vista puede aceptar el objeto de datos.

Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Observaciones

La implementación predeterminada consiste en no hacer nada y devolver DROPEFFECT_NONE.

Invalide esta función para proporcionar al usuario información visual durante la operación de arrastre. Dado que se llama a esta función de forma continua, todo el código que contenga se debe optimizar lo máximo posible. Para obtener más información, vea el artículo [OLE arrastrar y colocar: implementar un destino de colocación](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondragscroll"></a>CView:: OnDragScroll

Lo llama el marco de trabajo antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si el punto está en la región de desplazamiento.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Elija*<br/>
Contiene la ubicación del cursor, en píxeles, con respecto a la pantalla.

### <a name="return-value"></a>Valor devuelto

Un valor del tipo enumerado DROPEFFECT, que indica el tipo de colocación que se produciría si el usuario quitara el objeto en esta posición. Normalmente, el tipo de Drop depende del estado de la clave actual indicado por *dwKeyState*. Una asignación estándar de los valores de KeyStates a DROPEFFECT es:

- DROPEFFECT_NONE el objeto de datos no se puede quitar de esta ventana.

- DROPEFFECT_LINK para MK_CONTROL &#124; MK_SHIFT crea una vinculación entre el objeto y su servidor.

- DROPEFFECT_COPY para MK_CONTROL crea una copia del objeto colocado.

- DROPEFFECT_MOVE para MK_ALT crea una copia del objeto colocado y elimina el objeto original.

- DROPEFFECT_SCROLL indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en la vista de destino.

Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Observaciones

Invalide esta función cuando desee proporcionar un comportamiento especial para este evento. La implementación predeterminada desplaza automáticamente las ventanas cuando se arrastra el cursor al área de desplazamiento predeterminada dentro del borde de cada ventana. Para obtener más información, vea el artículo [OLE arrastrar y colocar: implementar un destino de colocación](../../mfc/drag-and-drop-ole.md#implement-a-drop-target).

##  <a name="ondraw"></a>CView:: OnDraw

Lo llama el marco de trabajo para presentar una imagen del documento.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se va a utilizar para representar una imagen del documento.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función para realizar la presentación en pantalla, la impresión y la vista previa de impresión, y pasa un contexto de dispositivo diferente en cada caso. No hay ninguna implementación predeterminada.

Debe reemplazar esta función para mostrar la vista del documento. Puede realizar llamadas a la interfaz de dispositivo gráfico (GDI) mediante el objeto [CDC](../../mfc/reference/cdc-class.md) al que apunta el parámetro *pDC* . Puede seleccionar recursos GDI, como lápices o fuentes, en el contexto del dispositivo antes de dibujar y, a continuación, anular su selección posteriormente. A menudo, el código de dibujo puede ser independiente del dispositivo; es decir, no requiere información sobre el tipo de dispositivo que muestra la imagen.

Para optimizar el dibujo, llame a la función miembro [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) del contexto del dispositivo para averiguar si se dibujará un rectángulo determinado. Si necesita distinguir entre la impresión y la presentación en pantalla normal, llame a la función miembro [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) del contexto del dispositivo.

##  <a name="ondrop"></a>CView:: Allocate

Lo llama el marco de trabajo cuando el usuario libera un objeto de datos sobre un destino de colocación válido.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

' pDataObject * apunta al [COleDataObject](../../mfc/reference/coledataobject-class.md) que se coloca en el destino de colocación.

*dropEffect*<br/>
Efecto de colocación que el usuario ha solicitado.

- DROPEFFECT_COPY crea una copia del objeto de datos que se va a quitar.

- DROPEFFECT_MOVE mueve el objeto de datos a la ubicación actual del mouse.

- DROPEFFECT_LINK crea un vínculo entre un objeto de datos y su servidor.

*Elija*<br/>
La posición actual del mouse en relación con el área de cliente de vista.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación de eliminación se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada y devuelve FALSE.

Invalide esta función para implementar el efecto de una colocación OLE en el área cliente de la vista. El objeto de datos se puede examinar mediante *pDataObject* para los formatos de datos del portapapeles y los datos quitados en el punto especificado.

> [!NOTE]
>  El marco de trabajo no llama a esta función si hay una invalidación en [OnDropEx](#ondropex) en esta clase de vista.

##  <a name="ondropex"></a>CView:: OnDropEx

Lo llama el marco de trabajo cuando el usuario libera un objeto de datos sobre un destino de colocación válido.

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*pDataObject*<br/>
Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se coloca en el destino de colocación.

*dropDefault*<br/>
El efecto que el usuario eligió para la operación de colocar predeterminada en función del estado de la clave actual. Puede ser DROPEFFECT_NONE. Los efectos de colocación se describen en la sección Comentarios.

*Plegable*<br/>
Una lista de los efectos de colocación que admite el origen de colocación. Los valores de efecto de colocación se pueden combinar mediante la **&#124;** operación OR bit a bit (). Los efectos de colocación se describen en la sección Comentarios.

*Elija*<br/>
La posición actual del mouse en relación con el área de cliente de vista.

### <a name="return-value"></a>Valor devuelto

Efecto de colocar que resultó del intento de colocar en la ubicación especificada por *Point*. Debe ser uno de los valores indicados por *dropEffectList*. Los efectos de colocación se describen en la sección Comentarios.

### <a name="remarks"></a>Observaciones

La implementación predeterminada consiste en no hacer nada y devolver un valor ficticio (-1) para indicar que el marco debe llamar al controlador de [Drop](#ondrop) .

Invalide esta función para implementar el efecto de arrastrar y colocar con el botón secundario del mouse. La acción de arrastrar y colocar del botón secundario del mouse normalmente muestra un menú de opciones cuando se suelta el botón secundario del mouse.

La invalidación de `OnDropEx` debe consultar el botón secundario del mouse. Puede llamar a [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) o almacenar el estado correcto del botón del mouse desde el controlador [OnDragEnter](#ondragenter) .

- Si el botón secundario del mouse está inactivo, la invalidación debe mostrar un menú emergente que ofrece compatibilidad con los efectos de colocación mediante el origen de colocación.

   - Examine *la lista desplegable para* determinar los efectos de colocación que admite el origen de la colocación. Habilite solo estas acciones en el menú emergente.

   - Use [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) para establecer la acción predeterminada basada en *dropDefault*.

   - Por último, realice la acción indicada por la selección del usuario en el menú emergente.

- Si el botón secundario del mouse no está inactivo, la invalidación debe procesarlo como una solicitud Drop estándar. Use el efecto de colocación especificado en *dropDefault*. Como alternativa, la invalidación puede devolver el valor ficticio (-1) para indicar que `OnDrop` controlará esta operación de colocar.

Use *pDataObject* para examinar el `COleDataObject` el formato de datos del portapapeles y los datos quitados en el punto especificado.

Los efectos de colocación describen la acción asociada a una operación de colocar. Vea la siguiente lista de efectos de colocación:

- DROPEFFECT_NONE no se permitiría la eliminación.

- DROPEFFECT_COPY se realizaría una operación de copia.

- DROPEFFECT_MOVE se realizará una operación de movimiento.

- DROPEFFECT_LINK se establecería un vínculo entre los datos colocados y los datos originales.

- DROPEFFECT_SCROLL indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

Para obtener más información sobre cómo establecer el comando de menú predeterminado, vea [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) en el Windows SDK y [CMenu:: GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) en este volumen.

##  <a name="onendprinting"></a>CView:: OnBeginPrinting

Lo llama el marco de trabajo después de que un documento se haya impreso u vista previa.

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto del dispositivo de impresora.

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada. Invalide esta función para liberar los recursos GDI asignados en la función miembro [OnBeginPrinting](#onbeginprinting) .

##  <a name="onendprintpreview"></a>CView:: OnEndPrintPreview

Lo llama el marco de trabajo cuando el usuario sale del modo de vista previa de impresión.

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto del dispositivo de impresora.

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual.

*Elija*<br/>
Especifica el punto de la página que se mostró por última vez en el modo de vista previa.

*pView*<br/>
Apunta al objeto de vista que se usa para la vista previa.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a la función miembro [OnBeginPrinting](#onendprinting) y restaura la ventana de marco principal al estado en que se encontraba antes de que comenzara la vista previa de impresión. Invalide esta función para realizar un procesamiento especial cuando finalice el modo de vista previa. Por ejemplo, si desea mantener la posición del usuario en el documento al cambiar del modo de vista previa al modo de presentación normal, puede desplazarse hasta la posición descrita por el parámetro de *punto* y el miembro de `m_nCurPage` de la estructura de `CPrintInfo` al que apunta el parámetro *Pinfo* .

Llame siempre a la versión de la clase base de `OnEndPrintPreview` desde la invalidación, normalmente al final de la función.

##  <a name="oninitialupdate"></a>CView:: OnInitialUpdate

Lo llama el marco de trabajo después de adjuntar la vista por primera vez al documento, pero antes de que se muestre inicialmente la vista.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a la función miembro [Alactualizar](#onupdate) sin información de sugerencia (es decir, con los valores predeterminados de 0 para el parámetro *lHint* y null para el parámetro *pHint* ). Invalide esta función para realizar cualquier inicialización única que requiera información sobre el documento. Por ejemplo, si la aplicación tiene documentos de tamaño fijo, puede usar esta función para inicializar los límites de desplazamiento de una vista en función del tamaño del documento. Si la aplicación admite documentos de tamaño variable, use [Actualizar](#onupdate) para actualizar los límites de desplazamiento cada vez que cambie el documento.

##  <a name="onpreparedc"></a>CView:: OnPrepareDC

Lo llama el marco de trabajo antes de que se llame a la función miembro [OnDraw](#ondraw) para la presentación en pantalla y antes de que se llame a la función miembro [OnPrint](#onprint) para cada página durante la impresión o la vista previa de impresión.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto de dispositivo que se va a utilizar para representar una imagen del documento.

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual si se llama a `OnPrepareDC` para la impresión o la vista previa de impresión; el miembro `m_nCurPage` especifica la página que se va a imprimir. Este parámetro es NULL si se llama a `OnPrepareDC` para la presentación en pantalla.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada si se llama a la función para la presentación en pantalla. Sin embargo, esta función se invalida en las clases derivadas, como [CScrollView](../../mfc/reference/cscrollview-class.md), para ajustar los atributos del contexto del dispositivo. por consiguiente, siempre debe llamar a la implementación de la clase base al principio de la invalidación.

Si se llama a la función para la impresión, la implementación predeterminada examina la información de la página almacenada en el parámetro *Pinfo* . Si no se ha especificado la longitud del documento, `OnPrepareDC` supone que el documento tiene una página de longitud y detiene el bucle de impresión después de imprimir una página. La función detiene el bucle de impresión estableciendo el `m_bContinuePrinting` miembro de la estructura en FALSE.

Invalide `OnPrepareDC` por cualquiera de las siguientes razones:

- Para ajustar los atributos del contexto del dispositivo según sea necesario para la página especificada. Por ejemplo, si necesita establecer el modo de asignación u otras características del contexto del dispositivo, hágalo en esta función.

- Para realizar la paginación en tiempo de impresión. Normalmente, se especifica la longitud del documento cuando comienza la impresión, utilizando la función miembro [OnPreparePrinting](#onprepareprinting) . Sin embargo, si no sabe de antemano cuánto tiempo es el documento (por ejemplo, al imprimir un número indeterminado de registros de una base de datos), invalide `OnPrepareDC` para probar el final del documento mientras se imprime. Cuando no haya más el documento que se va a imprimir, establezca el `m_bContinuePrinting` miembro de la estructura de `CPrintInfo` en FALSE.

- Para enviar códigos de escape a la impresora página por página. Para enviar códigos de escape desde `OnPrepareDC`, llame a la función miembro `Escape` del parámetro *pDC* .

Llame a la versión de la clase base de `OnPrepareDC` al principio de la invalidación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView:: OnPreparePrinting

Lo llama el marco de trabajo antes de que se imprima o se vea una vista previa de un documento.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual.

### <a name="return-value"></a>Valor devuelto

Distinto de cero para comenzar la impresión; 0 si se ha cancelado el trabajo de impresión.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada.

Debe reemplazar esta función para habilitar la impresión y la vista previa de impresión. Llame a la función miembro [DoPreparePrinting](#doprepareprinting) , pasándole el parámetro *Pinfo* y, a continuación, devuelva su valor devuelto. `DoPreparePrinting` muestra el cuadro de diálogo Imprimir y crea un contexto de dispositivo de impresora. Si desea inicializar el cuadro de diálogo Imprimir con valores distintos de los predeterminados, asigne valores a los miembros de *Pinfo*. Por ejemplo, si conoce la longitud del documento, pase el valor a la función miembro [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) de *Pinfo* antes de llamar a `DoPreparePrinting`. Este valor se muestra en el cuadro para: en la parte del intervalo del cuadro de diálogo Imprimir.

`DoPreparePrinting` no muestra el cuadro de diálogo Imprimir para un trabajo de vista previa. Si desea omitir el cuadro de diálogo Imprimir para un trabajo de impresión, compruebe que el miembro `m_bPreview` de *Pinfo* es false y, a continuación, ESTABLÉZCALO en true antes de pasarlo a `DoPreparePrinting`; Restablezca el valor FALSE después.

Si necesita realizar inicializaciones que requieran acceso al objeto `CDC` que representa el contexto del dispositivo de impresora (por ejemplo, si necesita conocer el tamaño de la página antes de especificar la longitud del documento), invalide la función miembro `OnBeginPrinting`.

Si desea establecer el valor de los miembros `m_nNumPreviewPages` o `m_strPageDesc` del parámetro *Pinfo* , hágalo después de llamar a `DoPreparePrinting`. La función miembro `DoPreparePrinting` establece `m_nNumPreviewPages` en el valor que se encuentra en la de la aplicación. Y establece `m_strPageDesc` en su valor predeterminado.

### <a name="example"></a>Ejemplo

  Invalide `OnPreparePrinting` y llame a `DoPreparePrinting` desde la invalidación para que el marco de trabajo muestre un cuadro de diálogo de impresión y cree un controlador de dominio de impresora.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Si sabe cuántas páginas contiene el documento, establezca la página máxima en `OnPreparePrinting` antes de llamar a `DoPreparePrinting`. El marco de trabajo mostrará el número de página máximo en el cuadro "para" del cuadro de diálogo Imprimir.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView:: OnPrint

Lo llama el marco de trabajo para imprimir u obtener una vista previa de una página del documento.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto del dispositivo de impresora.

*pInfo*<br/>
Apunta a una estructura de `CPrintInfo` que describe el trabajo de impresión actual.

### <a name="remarks"></a>Observaciones

Para cada página que se va a imprimir, el marco de trabajo llama a esta función inmediatamente después de llamar a la función miembro [OnPrepareDC](#onpreparedc) . La página que se va a imprimir se especifica mediante el `m_nCurPage` miembro de la estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) al que se redirige *Pinfo* . La implementación predeterminada llama a la función miembro [OnDraw](#ondraw) y le pasa el contexto de dispositivo de impresora.

Invalide esta función por cualquiera de las siguientes razones:

- Para permitir la impresión de documentos de páginas multipágina. Represente solo la parte del documento que corresponde a la página que se está imprimiendo actualmente. Si está utilizando `OnDraw` para realizar la representación, puede ajustar el origen de la ventanilla para que solo se imprima la parte adecuada del documento.

- Para que la imagen impresa tenga un aspecto diferente al de la imagen de la pantalla (es decir, si la aplicación no es WYSIWYG). En lugar de pasar el contexto de dispositivo de impresora a `OnDraw`, use el contexto de dispositivo para representar una imagen con los atributos que no se muestran en la pantalla.

   Si necesita recursos GDI para imprimir que no utiliza para la presentación en pantalla, selecciónelos en el contexto del dispositivo antes de dibujarlos y anule su selección posteriormente. Estos recursos GDI deben asignarse en [OnBeginPrinting](#onbeginprinting) y publicarse en [OnBeginPrinting](#onendprinting).

- Para implementar encabezados o pies de página. Todavía puede usar `OnDraw` para realizar la representación restringiendo el área en la que puede imprimir.

Tenga en cuenta que el miembro `m_rectDraw` del parámetro *Pinfo* describe el área imprimible de la página en unidades lógicas.

No llame a `OnPrepareDC` en la invalidación de `OnPrint`; el marco de trabajo llama a `OnPrepareDC` automáticamente antes de llamar a `OnPrint`.

### <a name="example"></a>Ejemplo

A continuación se encuentra un esquema para una función de `OnPrint` invalidada:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Para ver otro ejemplo, vea [CRichEditView::P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect).

##  <a name="onscroll"></a>CView:: onscroll

Lo llama el marco de trabajo para determinar si es posible el desplazamiento.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*nScrollCode*<br/>
Código de barra de desplazamiento que indica la solicitud de desplazamiento del usuario. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produce horizontalmente y un byte de orden superior, que determina el tipo de desplazamiento que se produce verticalmente:

- SB_BOTTOM se desplaza hasta la parte inferior.

- SB_LINEDOWN desplaza una línea hacia abajo.

- SB_LINEUP desplaza una línea hacia arriba.

- SB_PAGEDOWN desplaza una página hacia abajo.

- SB_PAGEUP desplaza una página hacia arriba.

- SB_THUMBTRACK arrastra el cuadro de desplazamiento a la posición especificada. La posición actual se especifica en *NPOs*.

- SB_TOP se desplaza hasta la parte superior.

*nPos*<br/>
Contiene la posición actual del cuadro de desplazamiento si el código de barra de desplazamiento es SB_THUMBTRACK; de lo contrario, no se utiliza. En función del intervalo de desplazamiento inicial, *NPOs* puede ser negativo y debe convertirse en un **int** si es necesario.

*bDoScroll*<br/>
Determina si realmente debe realizar la acción de desplazamiento especificada. Si es TRUE, el desplazamiento debe realizarse; Si es FALSE, el desplazamiento no debe realizarse.

### <a name="return-value"></a>Valor devuelto

Si *bDoScroll* es true y la vista se ha desplazado realmente, devuelve un valor distinto de cero; de lo contrario, es 0. Si *bDoScroll* es false, devuelve el valor que se habría devuelto si *bDoScroll* era true, aunque no haga realmente el desplazamiento.

### <a name="remarks"></a>Observaciones

En un caso, el marco de trabajo llama a esta función con *bDoScroll* establecido en true cuando la vista recibe un mensaje de la barra de desplazamiento. En este caso, realmente debe desplazarse por la vista. En el otro caso, se llama a esta función con *bDoScroll* establecido en false cuando un elemento OLE se arrastra inicialmente en la región de desplazamiento automático de un destino de colocación antes de que tenga lugar el desplazamiento realmente. En este caso, en realidad no debe desplazarse por la vista.

##  <a name="onscrollby"></a>CView:: OnScrollBy

Lo llama el marco de trabajo cuando el usuario ve un área más allá de la vista actual del documento, arrastrando un elemento OLE con los bordes actuales de la vista o manipulando las barras de desplazamiento horizontales o verticales.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*sizeScroll*<br/>
Número de píxeles desplazados horizontalmente y verticalmente.

*bDoScroll*<br/>
Determina si se produce el desplazamiento de la vista. Si es TRUE, se realiza el desplazamiento. Si es FALSE, no se produce el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se ha podido desplazar la vista; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

En las clases derivadas, este método comprueba si la vista es desplazable en la dirección solicitada por el usuario y, a continuación, actualiza la nueva región si es necesario. [CWnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd:: OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) llaman automáticamente a esta función para realizar la solicitud de desplazamiento real.

La implementación predeterminada de este método no cambia la vista, pero si no se llama, la vista no se desplazará en una clase derivada de `CScrollView`.

Si el ancho o el alto del documento supera los 32767 píxeles, el desplazamiento pasado 32767 producirá un error porque se llama a `OnScrollBy` con un argumento *sizeScroll* no válido.

##  <a name="onupdate"></a>CView:: actualización

Lo llama el marco de trabajo una vez que se ha modificado el documento de la vista; [CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) llama a esta función y permite que la vista actualice su presentación para reflejar esas modificaciones.

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>Parámetros

*pSender*<br/>
Apunta a la vista que modificó el documento, o NULL si se van a actualizar todas las vistas.

*lHint*<br/>
Contiene información sobre las modificaciones.

*pHint*<br/>
Apunta a un objeto que almacena información sobre las modificaciones.

### <a name="remarks"></a>Observaciones

También se llama mediante la implementación predeterminada de [OnInitialUpdate](#oninitialupdate). La implementación predeterminada invalida el área de cliente completa y la marca para pintar cuando se recibe el siguiente mensaje de WM_PAINT. Invalide esta función si desea actualizar solo las regiones que se asignan a las partes modificadas del documento. Para ello, debe pasar información sobre las modificaciones mediante los parámetros de la sugerencia.

Para usar *lHint*, defina valores de sugerencia especiales, normalmente una máscara de o un tipo enumerado, y haga que el documento pase uno de estos valores. Para usar *pHint*, derive una clase Hint de [CObject](../../mfc/reference/cobject-class.md) y haga que el documento pase un puntero a un objeto Hint. al reemplazar `OnUpdate`, utilice la función miembro [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) para determinar el tipo en tiempo de ejecución del objeto Hint.

Normalmente no debe realizar ningún dibujo directamente desde `OnUpdate`. En su lugar, determine el rectángulo que describe, en coordenadas de dispositivo, el área que requiere actualización; pase este rectángulo a [CWnd:: InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Esto hace que la pintura se produzca la próxima vez que se reciba un mensaje de [WM_PAINT](/windows/win32/gdi/wm-paint) .

Si *lHint* es 0 y *pHint* es null, el documento ha enviado una notificación de actualización genérica. Si una vista recibe una notificación de actualización genérica, o si no puede descodificar las sugerencias, debería invalidar su área cliente completa.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd (clase)](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC (clase)](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)
