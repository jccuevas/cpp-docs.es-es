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
ms.openlocfilehash: 763e36b0736ce588e7e2aded25e50347f9e0ca70
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373203"
---
# <a name="cview-class"></a>CView (clase)

Proporciona la funcionalidad básica para las clases de vista definidas por el usuario.

## <a name="syntax"></a>Sintaxis

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CView::CView](#cview)|Construye un objeto `CView`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CView::DoPreparePrinting](#doprepareprinting)|Muestra el cuadro de diálogo Imprimir y crea el contexto del dispositivo de impresora; llamar al reemplazar `OnPreparePrinting` la función miembro.|
|[CView::GetDocument](#getdocument)|Devuelve el documento asociado a la vista.|
|[CView::IsSelected](#isselected)|Comprueba si se ha seleccionado un elemento de documento. Necesario para la compatibilidad con OLE.|
|[CView::OnDragEnter](#ondragenter)|Se llama cuando un elemento se arrastra por primera vez a la región de arrastrar y colocar de una vista.|
|[CView::OnDragLeave](#ondragleave)|Se llama cuando un elemento arrastrado sale de la región de arrastrar y colocar de una vista.|
|[CView::OnDragOver](#ondragover)|Se llama cuando se arrastra un elemento sobre la región de arrastrar y colocar de una vista.|
|[CView::OnDragScroll](#ondragscroll)|Se llama para determinar si el cursor se arrastra a la región de desplazamiento de la ventana.|
|[CView::OnDrop](#ondrop)|Se llama cuando se ha colocado un elemento en la región de arrastrar y colocar de una vista, controlador predeterminado.|
|[CView::OnDropEx](#ondropex)|Se llama cuando se ha colocado un elemento en la región de arrastrar y colocar de una vista, controlador principal.|
|[CView::OnInitialUpdate](#oninitialupdate)|Se llama después de adjuntar una vista primero a un documento.|
|[CView::OnPrepareDC](#onpreparedc)|Se llama `OnDraw` antes de llamar a `OnPrint` la función miembro para la visualización de pantalla o se llama a la función miembro para imprimir o vista previa de impresión.|
|[CView::OnScroll](#onscroll)|Se llama cuando los elementos OLE se arrastran más allá de los bordes de la vista.|
|[CView::OnScrollBy](#onscrollby)|Se llama cuando se desplaza una vista que contiene elementos OLE activos en el lugar.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CView::OnActivateFrame](#onactivateframe)|Se llama cuando se activa o desactiva la ventana de marco que contiene la vista.|
|[CView::OnActivateView](#onactivateview)|Se llama cuando se activa una vista.|
|[CView::OnBeginPrinting](#onbeginprinting)|Se llama cuando comienza un trabajo de impresión; reemplazar para asignar recursos de interfaz de dispositivo gráfico (GDI).|
|[CView::OnDraw](#ondraw)|Se llama para renderizar una imagen del documento para la visualización de la pantalla, la impresión o la vista previa de impresión. Se requiere implementación.|
|[CView::OnEndPrinting](#onendprinting)|Se llama cuando finaliza un trabajo de impresión; invalidar para desasignar recursos GDI.|
|[CView::OnEndPrintPreview](#onendprintpreview)|Se llama cuando se cierra el modo de vista previa.|
|[CView::OnPreparePrinting](#onprepareprinting)|Se llama antes de imprimir o previsualizar un documento; reemplazar para inicializar el cuadro de diálogo Imprimir.|
|[CView::OnPrint](#onprint)|Se llama para imprimir u obtener una vista previa de una página del documento.|
|[CView::OnUpdate](#onupdate)|Se llama para notificar a una vista que su documento ha sido modificado.|

## <a name="remarks"></a>Observaciones

Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario: la vista representa una imagen del documento en la pantalla o impresora e interpreta la entrada del usuario como operaciones en el documento.

Una vista es un elemento secundario de una ventana de marco. Más de una vista puede compartir una ventana de marco, como en el caso de una ventana divisora. La relación entre una clase de vista, una clase de `CDocTemplate` ventana de marco y una clase de documento se establece mediante un objeto. Cuando el usuario abre una nueva ventana o divide una existente, el marco de trabajo construye una nueva vista y la adjunta al documento.

Una vista se puede adjuntar a un solo documento, pero un documento puede tener varias vistas asociadas a la vez, por ejemplo, si el documento se muestra en una ventana divisora o en varias ventanas secundarias en una aplicación de interfaz de varios documentos (MDI). La aplicación puede admitir diferentes tipos de vistas para un tipo de documento determinado; por ejemplo, un programa de procesamiento de texto podría proporcionar una vista de texto completa de un documento y una vista de esquema que muestre solo los encabezados de sección. Estos diferentes tipos de vistas se pueden colocar en ventanas de marco independientes o en paneles independientes de una sola ventana de marco si utiliza una ventana divisora.

Una vista puede ser responsable de controlar varios tipos diferentes de entrada, como la entrada del teclado, la entrada del ratón o la entrada a través de arrastrar y colocar, así como los comandos de menús, barras de herramientas o barras de desplazamiento. Una vista recibe comandos reenviados por su ventana de marco. Si la vista no controla un comando determinado, reenvía el comando a su documento asociado. Al igual que todos los destinos de comando, una vista controla los mensajes a través de un mapa de mensajes.

La vista es responsable de mostrar y modificar los datos del documento, pero no de almacenarlos. El documento proporciona a la vista los detalles necesarios sobre sus datos. Puede permitir que la vista acceda a los miembros de datos del documento directamente o puede proporcionar funciones miembro en la clase de documento para que la clase de vista llame.

Cuando cambian los datos de un documento, la vista responsable de los cambios normalmente llama a la función `OnUpdate` [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) para el documento, que notifica a todas las demás vistas mediante una llamada a la función miembro para cada uno. La implementación `OnUpdate` predeterminada de invalida todo el área de cliente de la vista. Puede invalidarlo para invalidar solo las regiones del área de cliente que se asignan a las partes modificadas del documento.

Para `CView`usar , derive una clase `OnDraw` de ella e implemente la función miembro para realizar la visualización de pantalla. También puede `OnDraw` utilizar para realizar la impresión y la vista previa de impresión. El marco de trabajo controla el bucle de impresión para imprimir y previsualizar el documento.

Una vista controla los mensajes de barra de desplazamiento con el [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funciones miembro. Puede implementar el control de mensajes de barra de `CView` desplazamiento en estas funciones, o puede usar la clase derivada [CScrollView](../../mfc/reference/cscrollview-class.md) para controlar el desplazamiento por usted.

`CScrollView`Además, la biblioteca Microsoft Foundation Class `CView`proporciona otras nueve clases derivadas de:

- [CCtrlView](../../mfc/reference/cctrlview-class.md), una vista que permite el uso de documento - arquitectura de vista con controles de árbol, lista y edición enriquecida.

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), una vista que muestra registros de base de datos en controles de cuadro de diálogo.

- [CEditView](../../mfc/reference/ceditview-class.md), una vista que proporciona un editor de texto multilínea simple. Puede utilizar `CEditView` un objeto como control en un cuadro de diálogo, así como una vista en un documento.

- [CFormView](../../mfc/reference/cformview-class.md), una vista desplazable que contiene controles de cuadro de diálogo y se basa en un recurso de plantilla de cuadro de diálogo.

- [CListView](../../mfc/reference/clistview-class.md), una vista que permite el uso de documento - arquitectura de vista con controles de lista.

- [CRecordView](../../mfc/reference/crecordview-class.md), una vista que muestra registros de base de datos en controles de cuadro de diálogo.

- [CRichEditView](../../mfc/reference/cricheditview-class.md), una vista que permite el uso de documento - arquitectura de vista con controles de edición enriquecidos.

- [CScrollView](../../mfc/reference/cscrollview-class.md), una vista que proporciona automáticamente compatibilidad con el desplazamiento.

- [CTreeView](../../mfc/reference/ctreeview-class.md), una vista que permite el uso de documento - arquitectura de vista con controles de árbol.

La `CView` clase también tiene una `CPreviewView`clase de implementación derivada denominada , que el marco de trabajo utiliza para realizar la vista previa de impresión. Esta clase proporciona compatibilidad con las características exclusivas de la ventana de vista previa de impresión, como una barra de herramientas, una vista previa de una o dos páginas y el zoom, es decir, la ampliación de la imagen previsualizada. No es necesario llamar o invalidar `CPreviewView`ninguna de las funciones miembro de 's a menos que desee implementar su propia interfaz para la vista previa de impresión (por ejemplo, si desea admitir la edición en modo de vista previa de impresión). Para obtener más `CView`información sobre el uso de , consulte Arquitectura de [documento/vista](../../mfc/document-view-architecture.md) e [Impresión](../../mfc/printing.md). Además, consulte [la Nota técnica 30](../../mfc/tn030-customizing-printing-and-print-preview.md) para obtener más información sobre cómo personalizar la vista previa de impresión.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cviewcview"></a><a name="cview"></a>CView::CView

Construye un objeto `CView`.

```
CView();
```

### <a name="remarks"></a>Observaciones

El marco de trabajo llama al constructor cuando se crea una nueva ventana de marco o se divide una ventana. Invalidar el [OnInitialUpdate](#oninitialupdate) función miembro para inicializar la vista después de adjuntar el documento.

## <a name="cviewdoprepareprinting"></a><a name="doprepareprinting"></a>CView::DoPreparePrinting

Llame a esta función desde la invalidación de [OnPreparePrinting](#onprepareprinting) para invocar el cuadro de diálogo Imprimir y crear un contexto de dispositivo de impresora.

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si puede comenzar la impresión o la vista previa de impresión; 0 si la operación se ha cancelado.

### <a name="remarks"></a>Observaciones

El comportamiento de esta función depende de si se llama para `m_bPreview` imprimir o vista previa de impresión (especificado por el miembro del parámetro *pInfo).* Si se está imprimiendo un archivo, esta función invoca el cuadro de diálogo Imprimir, utilizando los valores de la estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) a la que *apunta pInfo;* después de que el usuario haya cerrado el cuadro de diálogo, la función crea un contexto de dispositivo de impresora basado en la configuración que el usuario especificó en el cuadro de diálogo y devuelve este contexto de dispositivo a través del parámetro *pInfo.* Este contexto de dispositivo se utiliza para imprimir el documento.

Si se está previsualizando un archivo, esta función crea un contexto de dispositivo de impresora utilizando la configuración actual de la impresora; este contexto de dispositivo se utiliza para simular la impresora durante la vista previa.

## <a name="cviewgetdocument"></a><a name="getdocument"></a>CView::GetDocument

Llame a esta función para obtener un puntero al documento de la vista.

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al objeto [CDocument](../../mfc/reference/cdocument-class.md) asociado a la vista. NULL si la vista no está asociada a un documento.

### <a name="remarks"></a>Observaciones

Esto le permite llamar a las funciones miembro del documento.

## <a name="cviewisselected"></a><a name="isselected"></a>CView::IsSelected

Llamado por el marco de trabajo para comprobar si el elemento de documento especificado está seleccionado.

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>Parámetros

*pDocItem*<br/>
Señala el elemento de documento que se está probando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se selecciona el elemento de documento especificado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función devuelve FALSE. Invalide esta función si está implementando la selección mediante [CDocItem](../../mfc/reference/cdocitem-class.md) objetos. Debe invalidar esta función si la vista contiene elementos OLE.

## <a name="cviewonactivateframe"></a><a name="onactivateframe"></a>CView::OnActivateFrame

Llamado por el marco de trabajo cuando la ventana de marco que contiene la vista está activada o desactivada.

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>Parámetros

*nEstado*<br/>
Especifica si la ventana de marco se está activando o desactivando. Puede ser uno de los siguientes valores:

- WA_INACTIVE Se está desactivando la ventana de marco.

- WA_ACTIVE La ventana de marco se está activando a través de algún método que no sea un clic del ratón (por ejemplo, mediante el uso de la interfaz del teclado para seleccionar la ventana).

- WA_CLICKACTIVE La ventana del marco se activa con un clic del ratón

*pFrameWnd*<br/>
Puntero a la ventana de marco que se va a activar.

### <a name="remarks"></a>Observaciones

Invalide esta función miembro si desea realizar un procesamiento especial cuando se activa o desactiva la ventana de marco asociada a la vista. Por ejemplo, [CFormView](../../mfc/reference/cformview-class.md) realiza esta invalidación cuando guarda y restaura el control que tiene el foco.

## <a name="cviewonactivateview"></a><a name="onactivateview"></a>CView::OnActivateView

Llamado por el marco de trabajo cuando se activa o desactiva una vista.

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>Parámetros

*bActivar*<br/>
Indica si la vista se está activando o desactivando.

*pActivateView*<br/>
Apunta al objeto de vista que se está activando.

*pDeactiveView*<br/>
Apunta al objeto de vista que se está desactivando.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función establece el foco en la vista que se está activando. Reemplace esta función si desea realizar un procesamiento especial cuando se activa o desactiva una vista. Por ejemplo, si desea proporcionar indicaciones visuales especiales que distingan la vista activa de las vistas inactivas, examinaría el parámetro *bActivate* y actualizaría la apariencia de la vista en consecuencia.

Los parámetros *pActivateView* y *pDeactiveView* apuntan a la misma vista si la ventana de marco principal de la aplicación está activada sin ningún cambio en la vista activa, por ejemplo, si el foco se transfiere de otra aplicación a esta, en lugar de de una vista a otra dentro de la aplicación o al cambiar entre ventanas secundarias MDI. Esto permite que una vista vuelva a realizar su paleta, si es necesario.

Estos parámetros difieren cuando [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) se llama con una vista que es diferente de lo que [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) devolvería. Esto sucede con mayor frecuencia con las ventanas divisoras.

## <a name="cviewonbeginprinting"></a><a name="onbeginprinting"></a>CView::OnBeginPrinting

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

## <a name="cviewondragenter"></a><a name="ondragenter"></a>CView::OnDragEnter

Llamado por el marco de trabajo cuando el mouse entra por primera vez en la región de no desplazamiento de la ventana de destino de colocación.

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
Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Punto*<br/>
La posición actual del ratón en relación con el área de cliente de la vista.

### <a name="return-value"></a>Valor devuelto

Valor del tipo enumerado DROPEFFECT, que indica el tipo de colocación que se produciría si el usuario coloca el objeto en esta posición. El tipo de colocación suele depender del estado de clave actual indicado por *dwKeyState*. Una asignación estándar de estados clave a valores DROPEFFECT es:

- DROPEFFECT_NONE El objeto de datos no se puede quitar en esta ventana.

- DROPEFFECT_LINK para MK_CONTROL &#124; MK_SHIFT Crea un vínculo entre el objeto y su servidor.

- DROPEFFECT_COPY para MK_CONTROL Crea una copia del objeto descartado.

- DROPEFFECT_MOVE para MK_ALT Crea una copia del objeto descartado y elimina el objeto original. Normalmente, este es el efecto de colocación predeterminado, cuando la vista puede aceptar este objeto de datos.

Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Observaciones

La implementación predeterminada es no hacer nada y devolver DROPEFFECT_NONE.

Invalide esta función para prepararse para futuras llamadas a la [OnDragOver](#ondragover) función miembro. Los datos necesarios del objeto de datos se deben `OnDragOver` recuperar en este momento para su uso posterior en la función miembro. La vista también debe actualizarse en este momento para proporcionar al usuario comentarios visuales. Para obtener más información, vea el artículo [arrastrar y colocar OLE: Implementar un destino](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)de colocación .

## <a name="cviewondragleave"></a><a name="ondragleave"></a>CView::OnDragLeave

Llamado por el marco de trabajo durante una operación de arrastre cuando el mouse se mueve fuera del área de colocación válida para esa ventana.

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>Observaciones

Invalide esta función si la vista actual necesita limpiar las acciones realizadas durante las llamadas [OnDragEnter](#ondragenter) o [OnDragOver,](#ondragover) como quitar los comentarios visuales del usuario mientras se arrastraba y quitaba el objeto.

## <a name="cviewondragover"></a><a name="ondragover"></a>CView::OnDragOver

Llamado por el marco de trabajo durante una operación de arrastre cuando el mouse se mueve sobre la ventana de destino de colocación.

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
Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Punto*<br/>
La posición actual del mouse en relación con el área de cliente de vista.

### <a name="return-value"></a>Valor devuelto

Valor del tipo enumerado DROPEFFECT, que indica el tipo de colocación que se produciría si el usuario coloca el objeto en esta posición. El tipo de colocación a menudo depende del estado de clave actual indicado por *dwKeyState*. Una asignación estándar de estados clave a valores DROPEFFECT es:

- DROPEFFECT_NONE El objeto de datos no se puede quitar en esta ventana.

- DROPEFFECT_LINK para MK_CONTROL &#124; MK_SHIFT Crea un vínculo entre el objeto y su servidor.

- DROPEFFECT_COPY para MK_CONTROL Crea una copia del objeto descartado.

- DROPEFFECT_MOVE para MK_ALT Crea una copia del objeto descartado y elimina el objeto original. Normalmente, este es el efecto de colocación predeterminado, cuando la vista puede aceptar el objeto de datos.

Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Observaciones

La implementación predeterminada es no hacer nada y devolver DROPEFFECT_NONE.

Reemplace esta función para proporcionar al usuario comentarios visuales durante la operación de arrastre. Puesto que esta función se llama continuamente, cualquier código contenido en ella debe optimizarse tanto como sea posible. Para obtener más información, vea el artículo [arrastrar y colocar OLE: Implementar un destino](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)de colocación .

## <a name="cviewondragscroll"></a><a name="ondragscroll"></a>CView::OnDragScroll

Llamado por el marco de trabajo antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si el punto está en la región de desplazamiento.

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

*dwKeyState*<br/>
Contiene el estado de las teclas modificadoras. Esta es una combinación de cualquier número de los siguientes: MK_CONTROL, MK_SHIFT, MK_ALT, MK_LBUTTON, MK_MBUTTON y MK_RBUTTON.

*Punto*<br/>
Contiene la ubicación del cursor, en píxeles, en relación con la pantalla.

### <a name="return-value"></a>Valor devuelto

Valor del tipo enumerado DROPEFFECT, que indica el tipo de colocación que se produciría si el usuario coloca el objeto en esta posición. El tipo de colocación suele depender del estado de clave actual indicado por *dwKeyState*. Una asignación estándar de estados clave a valores DROPEFFECT es:

- DROPEFFECT_NONE El objeto de datos no se puede quitar en esta ventana.

- DROPEFFECT_LINK para MK_CONTROL &#124; MK_SHIFT Crea un vínculo entre el objeto y su servidor.

- DROPEFFECT_COPY para MK_CONTROL Crea una copia del objeto descartado.

- DROPEFFECT_MOVE para MK_ALT Crea una copia del objeto descartado y elimina el objeto original.

- DROPEFFECT_SCROLL Indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en la vista de destino.

Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../overview/visual-cpp-samples.md).

### <a name="remarks"></a>Observaciones

Invalide esta función cuando desee proporcionar un comportamiento especial para este evento. La implementación predeterminada desplaza automáticamente las ventanas cuando se arrastra el cursor a la región de desplazamiento predeterminada dentro del borde de cada ventana. Para obtener más información, vea el artículo [arrastrar y colocar OLE: Implementar un destino](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)de colocación .

## <a name="cviewondraw"></a><a name="ondraw"></a>CView::OnDraw

Llamado por el marco de trabajo para representar una imagen del documento.

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Señala el contexto del dispositivo que se utilizará para representar una imagen del documento.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función para realizar la visualización de pantalla, la impresión y la vista previa de impresión, y pasa un contexto de dispositivo diferente en cada caso. No hay ninguna implementación predeterminada.

Debe reemplazar esta función para mostrar la vista del documento. Puede realizar llamadas de interfaz de dispositivo gráfico (GDI) utilizando el objeto [CDC](../../mfc/reference/cdc-class.md) al que apunta el parámetro *pDC.* Puede seleccionar recursos GDI, como plumillas o fuentes, en el contexto del dispositivo antes de dibujar y, a continuación, anular su selección. A menudo, el código de dibujo puede ser independiente del dispositivo; es decir, no requiere información sobre qué tipo de dispositivo está mostrando la imagen.

Para optimizar el dibujo, llame a la [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) función miembro del contexto del dispositivo para averiguar si se dibujará un rectángulo determinado. Si necesita distinguir entre la visualización normal de la pantalla y la impresión, llame a la [isprinting](../../mfc/reference/cdc-class.md#isprinting) función miembro del contexto del dispositivo.

## <a name="cviewondrop"></a><a name="ondrop"></a>CView::OnDrop

Llamado por el marco de trabajo cuando el usuario libera un objeto de datos sobre un destino de colocación válido.

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>Parámetros

'pDataObject* Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se coloca en el destino de colocación.

*dropEffect*<br/>
El efecto de colocación que el usuario ha solicitado.

- DROPEFFECT_COPY Crea una copia del objeto de datos que se va a quitar.

- DROPEFFECT_MOVE Mueve el objeto de datos a la ubicación actual del mouse.

- DROPEFFECT_LINK Crea un vínculo entre un objeto de datos y su servidor.

*Punto*<br/>
La posición actual del mouse en relación con el área de cliente de vista.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la caída se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada y devuelve FALSE.

Invalide esta función para implementar el efecto de una colocación OLE en el área de cliente de la vista. El objeto de datos se puede examinar a través de *pDataObject* para los formatos de datos del Portapapeles y los datos colocados en el punto especificado.

> [!NOTE]
> El marco de trabajo no llama a esta función si hay una invalidación de [OnDropEx](#ondropex) en esta clase de vista.

## <a name="cviewondropex"></a><a name="ondropex"></a>CView::OnDropEx

Llamado por el marco de trabajo cuando el usuario libera un objeto de datos sobre un destino de colocación válido.

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
El efecto que el usuario eligió para la operación de colocación predeterminada en función del estado de clave actual. Puede ser DROPEFFECT_NONE. Los efectos de caída se describen en la sección Comentarios.

*dropList*<br/>
Una lista de los efectos de colocación que admite el origen de colocación. Los valores de efecto de colocación se pueden combinar mediante la operación OR ( **&#124;**) bit a bit. Los efectos de caída se describen en la sección Comentarios.

*Punto*<br/>
La posición actual del mouse en relación con el área de cliente de vista.

### <a name="return-value"></a>Valor devuelto

El efecto de colocación resultante del intento de colocación en la ubicación especificada por *el punto*. Debe ser uno de los valores indicados por *dropEffectList*. Los efectos de caída se describen en la sección Comentarios.

### <a name="remarks"></a>Observaciones

La implementación predeterminada es no hacer nada y devolver un valor ficticio ( -1 ) para indicar que el marco de trabajo debe llamar a la [OnDrop](#ondrop) controlador.

Reemplace esta función para implementar el efecto de un botón derecho del ratón arrastrar y soltar. Arrastrar y soltar con el botón derecho del ratón normalmente muestra un menú de opciones cuando se suelta el botón derecho del ratón.

La invalidación de `OnDropEx` should consulta para el botón derecho del ratón. Puede llamar a [GetKeyState](/windows/win32/api/winuser/nf-winuser-getkeystate) o almacenar el estado del botón derecho del mouse desde el [OnDragEnter](#ondragenter) controlador.

- Si el botón derecho del ratón está abajo, la anulación debe mostrar un menú emergente que ofrece el soporte de efectos de colocación por el origen de colocación.

  - Examine *dropList* para determinar los efectos de colocación admitidos por el origen de colocación. Habilite solo estas acciones en el menú emergente.

  - Utilice [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) para establecer la acción predeterminada basada en *dropDefault*.

  - Por último, realice la acción indicada por la selección de usuario en el menú emergente.

- Si el botón derecho del ratón no está abajo, la invalidación debe procesarlo como una solicitud de colocación estándar. Utilice el efecto de colocación especificado en *dropDefault*. Como alternativa, la invalidación puede devolver el valor `OnDrop` ficticio ( -1 ) para indicar que controlará esta operación de colocación.

Utilice *pDataObject* para `COleDataObject` examinar el formato de datos del Portapapeles y los datos colocados en el punto especificado.

Los efectos de colocación describen la acción asociada a una operación de colocación. Consulte la siguiente lista de efectos de caída:

- DROPEFFECT_NONE No se permitiría una caída.

- DROPEFFECT_COPY Se realizaría una operación de copia.

- DROPEFFECT_MOVE Se realizaría una operación de movimiento.

- DROPEFFECT_LINK Se establecería un vínculo de los datos eliminados a los datos originales.

- DROPEFFECT_SCROLL Indica que una operación de desplazamiento de arrastre está a punto de producirse o se está produciendo en el destino.

Para obtener más información sobre cómo establecer el comando de menú predeterminado, vea [SetMenuDefaultItem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem) en el Windows SDK y [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) en este volumen.

## <a name="cviewonendprinting"></a><a name="onendprinting"></a>CView::OnEndPrinting

Llamado por el marco de trabajo después de imprimir o previsualizar un documento.

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

La implementación predeterminada de esta función no hace nada. Invalide esta función para liberar los recursos De GDI asignados en el [OnBeginPrinting](#onbeginprinting) función miembro.

## <a name="cviewonendprintpreview"></a><a name="onendprintpreview"></a>CView::OnEndPrintPreview

Llamado por el marco de trabajo cuando el usuario sale del modo de vista previa de impresión.

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

*Punto*<br/>
Especifica el punto de la página que se mostró por última vez en modo de vista previa.

*pView*<br/>
Señala el objeto de vista utilizado para la previsualización.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a la [OnEndPrinting](#onendprinting) función miembro y restaura la ventana de marco principal al estado en el que estaba antes de que comenzara la vista previa de impresión. Reemplace esta función para realizar un procesamiento especial cuando finalice el modo de vista previa. Por ejemplo, si desea mantener la posición del usuario en el documento al cambiar del modo de vista previa al `m_nCurPage` modo `CPrintInfo` de visualización normal, puede desplazarse a la posición descrita por el parámetro *de punto* y el miembro de la estructura a la que apunta el parámetro *pInfo.*

Llame siempre a la `OnEndPrintPreview` versión de clase base de la invalidación, normalmente al final de la función.

## <a name="cviewoninitialupdate"></a><a name="oninitialupdate"></a>CView::OnInitialUpdate

Llamado por el marco de trabajo después de que la vista se adjunta primero al documento, pero antes de que se muestre inicialmente la vista.

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función llama a la función miembro [OnUpdate](#onupdate) sin información de sugerencia (es decir, utilizando los valores predeterminados de 0 para el parámetro *lHint* y NULL para el parámetro *pHint).* Reemplace esta función para realizar cualquier inicialización única que requiera información sobre el documento. Por ejemplo, si la aplicación tiene documentos de tamaño fijo, puede usar esta función para inicializar los límites de desplazamiento de una vista en función del tamaño del documento. Si la aplicación admite documentos de tamaño variable, utilice [OnUpdate](#onupdate) para actualizar los límites de desplazamiento cada vez que cambie el documento.

## <a name="cviewonpreparedc"></a><a name="onpreparedc"></a>CView::OnPrepareDC

Llamado por el marco de trabajo antes de la [OnDraw](#ondraw) se llama a la función miembro para la visualización de pantalla y antes de la [OnPrint](#onprint) se llama a la función miembro para cada página durante la impresión o vista previa de impresión.

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Señala el contexto del dispositivo que se utilizará para representar una imagen del documento.

*pInfo*<br/>
Señala a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe `OnPrepareDC` el trabajo de impresión actual si se llama para imprimir o obtener una vista previa de impresión; el `m_nCurPage` miembro especifica la página a punto de imprimirse. Este parámetro es `OnPrepareDC` NULL si se llama para la visualización de la pantalla.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta función no hace nada si se llama a la función para la visualización de pantalla. Sin embargo, esta función se invalida en clases derivadas, como [CScrollView](../../mfc/reference/cscrollview-class.md), para ajustar los atributos del contexto del dispositivo; por lo tanto, siempre debe llamar a la implementación de la clase base al principio de la invalidación.

Si se llama a la función para imprimir, la implementación predeterminada examina la información de página almacenada en el *pInfo* parámetro. Si no se ha especificado la `OnPrepareDC` longitud del documento, se supone que el documento tiene una página y detiene el bucle de impresión después de imprimir una página. La función detiene el `m_bContinuePrinting` bucle de impresión estableciendo el miembro de la estructura en FALSE.

Invalidación `OnPrepareDC` por cualquiera de las siguientes razones:

- Para ajustar los atributos del contexto del dispositivo según sea necesario para la página especificada. Por ejemplo, si necesita establecer el modo de asignación u otras características del contexto del dispositivo, hágalo en esta función.

- Para realizar la paginación en tiempo de impresión. Normalmente se especifica la longitud del documento cuando comienza la impresión, mediante el [OnPreparePrinting](#onprepareprinting) función miembro. Sin embargo, si no sabe de antemano cuánto tiempo dura el documento (por ejemplo, `OnPrepareDC` al imprimir un número indeterminado de registros de una base de datos), anule para probar el final del documento mientras se está imprimiendo. Cuando no haya más del documento que se `m_bContinuePrinting` va `CPrintInfo` a imprimir, establezca el miembro de la estructura en FALSE.

- Para enviar códigos de escape a la impresora página por página. Para enviar códigos de escape desde `OnPrepareDC`, llame a la `Escape` función miembro del parámetro *pDC.*

Llame a la `OnPrepareDC` versión de clase base al principio de la invalidación.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

## <a name="cviewonprepareprinting"></a><a name="onprepareprinting"></a>CView::OnPreparePrinting

Llamado por el marco de trabajo antes de que se imprima o previsualice un documento.

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pInfo*<br/>
Apunta a una estructura [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo de impresión actual.

### <a name="return-value"></a>Valor devuelto

Distinto de cero para comenzar a imprimir; 0 si se ha cancelado el trabajo de impresión.

### <a name="remarks"></a>Observaciones

La implementación predeterminada no hace nada.

Debe anular esta función para habilitar la impresión y la vista previa de impresión. Llame a la [DoPreparePrinting](#doprepareprinting) función miembro, pasándole el *pInfo* parámetro y, a continuación, devolver su valor devuelto; `DoPreparePrinting` muestra el cuadro de diálogo Imprimir y crea un contexto de dispositivo de impresora. Si desea inicializar el cuadro de diálogo Imprimir con valores distintos de los predeterminados, asigne valores a los miembros de *pInfo*. Por ejemplo, si conoce la longitud del documento, pase el valor a la `DoPreparePrinting`función miembro [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) de *pInfo* antes de llamar a . Este valor se muestra en el cuadro Para: en la parte Rango del cuadro de diálogo Imprimir.

`DoPreparePrinting`no muestra el cuadro de diálogo Imprimir para un trabajo de vista previa. Si desea omitir el cuadro de diálogo Imprimir para `m_bPreview` un trabajo de impresión, compruebe que el `DoPreparePrinting`miembro de *pInfo* es FALSE y, a continuación, establézcalo en TRUE antes de pasarlo a ; restablecerlo a FALSE después.

Si necesita realizar inicializaciones que requieren `CDC` acceso al objeto que representa el contexto del dispositivo de impresora (por ejemplo, `OnBeginPrinting` si necesita conocer el tamaño de página antes de especificar la longitud del documento), invalide la función miembro.

Si desea establecer el valor `m_nNumPreviewPages` `m_strPageDesc` de los miembros o del `DoPreparePrinting`parámetro *pInfo,* hágalo después de llamar a . La `DoPreparePrinting` función `m_nNumPreviewPages` miembro se establece en el valor que se encuentra en el archivo . INI y `m_strPageDesc` establece su valor predeterminado.

### <a name="example"></a>Ejemplo

  Invalide `OnPreparePrinting` `DoPreparePrinting` y llame desde la invalidación para que el marco de trabajo muestre un cuadro de diálogo Imprimir y cree un controlador de dominio de impresora automáticamente.

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

Si sabe cuántas páginas contiene el documento, establezca la página máxima `OnPreparePrinting` antes de llamar a `DoPreparePrinting`. El marco de trabajo mostrará el número máximo de página en el cuadro "a" del cuadro de diálogo Imprimir.

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

## <a name="cviewonprint"></a><a name="onprint"></a>CView::OnPrint

Llamado por el marco de trabajo para imprimir u obtener una vista previa de una página del documento.

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Apunta al contexto del dispositivo de impresora.

*pInfo*<br/>
Señala a `CPrintInfo` una estructura que describe el trabajo de impresión actual.

### <a name="remarks"></a>Observaciones

Para cada página que se imprime, el marco de trabajo llama a esta función inmediatamente después de llamar a la [OnPrepareDC](#onpreparedc) función miembro. El miembro de la estructura `m_nCurPage` [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) a la que *apunta pInfo* especifica la página que se está imprimiendo. La implementación predeterminada llama a la [OnDraw](#ondraw) función miembro y le pasa el contexto del dispositivo de impresora.

Reemplace esta función por cualquiera de las siguientes razones:

- Para permitir la impresión de documentos de varias páginas. Renderice solo la parte del documento que corresponde a la página que se está imprimiendo actualmente. Si está utilizando `OnDraw` para realizar la representación, puede ajustar el origen de la ventana gráfica para que solo se imprima la parte adecuada del documento.

- Para que la imagen impresa se vea diferente de la imagen de pantalla (es decir, si la aplicación no es WYSIWYG). En lugar de pasar `OnDraw`el contexto del dispositivo de impresora a , utilice el contexto del dispositivo para representar una imagen utilizando atributos que no se muestran en la pantalla.

   Si necesita recursos GDI para imprimir que no utiliza para la visualización de pantalla, selecciónelos en el contexto del dispositivo antes de dibujar y anule la selección después. Estos recursos GDI deben asignarse en [OnBeginPrinting](#onbeginprinting) y liberarse en [OnEndPrinting](#onendprinting).

- Para implementar encabezados o pies de página. Todavía puede `OnDraw` utilizar para realizar la representación restringiendo el área en la que puede imprimir.

Tenga en `m_rectDraw` cuenta que el miembro del parámetro *pInfo* describe el área imprimible de la página en unidades lógicas.

No llame `OnPrepareDC` a su `OnPrint`anulación de ; el marco `OnPrepareDC` de `OnPrint`trabajo llama automáticamente antes de llamar a .

### <a name="example"></a>Ejemplo

A continuación se muestra un `OnPrint` esqueleto para una función anulada:

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

Para obtener otro ejemplo, vea [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).

## <a name="cviewonscroll"></a><a name="onscroll"></a>CView::OnScroll

Llamado por el marco de trabajo para determinar si el desplazamiento es posible.

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*nScrollCode*<br/>
Un código de barra de desplazamiento que indica la solicitud de desplazamiento del usuario. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produce horizontalmente, y un byte de orden superior, que determina el tipo de desplazamiento que se produce verticalmente:

- SB_BOTTOM Se desplaza hacia abajo.

- SB_LINEDOWN Desplaza una línea hacia abajo.

- SB_LINEUP Desplaza una línea.

- SB_PAGEDOWN Desplaza una página hacia abajo.

- SB_PAGEUP Desplaza una página hacia arriba.

- SB_THUMBTRACK Cuadro de desplazamiento Arrastra a la posición especificada. La posición actual se especifica en *nPos*.

- SB_TOP Se desplaza a la parte superior.

*Fnco*<br/>
Contiene la posición actual del cuadro de desplazamiento si el código de barra de desplazamiento es SB_THUMBTRACK; de lo contrario no se utiliza. Dependiendo del rango de desplazamiento inicial, *nPos* puede ser negativo y debe convertirse en un **int** si es necesario.

*bDoScroll*<br/>
Determina si realmente debe realizar la acción de desplazamiento especificada. Si TRUE, a continuación, el desplazamiento debe tener lugar; si FALSE, a continuación, no debe producirse el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Si *bDoScroll* es TRUE y la vista se desplazó realmente, devuelva distinto de cero; de lo contrario 0. Si *bDoScroll* es FALSE, devuelva el valor que habría devuelto si *bDoScroll* fuera TRUE, aunque en realidad no realice el desplazamiento.

### <a name="remarks"></a>Observaciones

En un caso, el marco de trabajo llama a esta función con *bDoScroll* establecido en TRUE cuando la vista recibe un mensaje de barra de desplazamiento. En este caso, debería desplazarse por la vista. En el otro caso, se llama a esta función con *bDoScroll* establecido en FALSE cuando un elemento OLE se arrastra inicialmente a la región de desplazamiento automático de un destino de colocación antes de que el desplazamiento realmente tenga lugar. En este caso, no debe desplazarse realmente por la vista.

## <a name="cviewonscrollby"></a><a name="onscrollby"></a>CView::OnScrollBy

Llamado por el marco de trabajo cuando el usuario ve un área más allá de la vista actual del documento, ya sea arrastrando un elemento OLE contra los bordes actuales de la vista o manipulando las barras de desplazamiento verticales u horizontales.

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>Parámetros

*sizeScroll*<br/>
Número de píxeles desplazados horizontal y verticalmente.

*bDoScroll*<br/>
Determina si se produce el desplazamiento de la vista. Si TRUE, a continuación, el desplazamiento tiene lugar; si FALSE, a continuación, no se produce el desplazamiento.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la vista se pudo desplazar; de lo contrario 0.

### <a name="remarks"></a>Observaciones

En las clases derivadas, este método comprueba si la vista se puede desplazar en la dirección que el usuario solicitó y, a continuación, actualiza la nueva región si es necesario. [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) llaman automáticamente a esta función para realizar la solicitud de desplazamiento real.

La implementación predeterminada de este método no cambia la vista, pero si `CScrollView`no se llama, la vista no se desplazará en una clase derivada.

Si el ancho o alto del documento supera los 32767 píxeles, se producirá un error al desplazarse más allá de 32767 porque `OnScrollBy` se llama con un argumento *sizeScroll* no válido.

## <a name="cviewonupdate"></a><a name="onupdate"></a>CView::OnUpdate

Llamado por el marco de trabajo después de que se haya modificado el documento de la vista; [CDocument::UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) llama a esta función y permite que la vista actualice su visualización para reflejar esas modificaciones.

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

También se llama por la implementación predeterminada de [OnInitialUpdate](#oninitialupdate). La implementación predeterminada invalida todo el área de cliente, marcándola para pintar cuando se recibe el siguiente mensaje de WM_PAINT. Reemplace esta función si desea actualizar solo las regiones que se asignan a las partes modificadas del documento. Para ello, debe pasar información sobre las modificaciones utilizando los parámetros de sugerencia.

Para utilizar *lHint*, defina valores de sugerencia especiales, normalmente una máscara de bits o un tipo enumerado, y haga que el documento pase uno de estos valores. Para utilizar *pHint*, derive una clase de sugerencia de [CObject](../../mfc/reference/cobject-class.md) y haga que el documento pase un puntero a un objeto de sugerencia; al reemplazar `OnUpdate`, utilice la función miembro [CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) para determinar el tipo en tiempo de ejecución del objeto de sugerencia.

Normalmente no debe realizar ningún `OnUpdate`dibujo directamente desde . En su lugar, determine el rectángulo que describe, en coordenadas de dispositivo, el área que requiere actualización; pasar este rectángulo a [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Esto hace que la pintura se produzca la próxima vez que se reciba un mensaje [de WM_PAINT.](/windows/win32/gdi/wm-paint)

Si *lHint* es 0 y *pHint* es NULL, el documento ha enviado una notificación de actualización genérica. Si una vista recibe una notificación de actualización genérica, o si no puede descodificar las sugerencias, debe invalidar toda su área de cliente.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)<br/>
[Clase CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)<br/>
[Clase CDC](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument (clase)](../../mfc/reference/cdocument-class.md)
