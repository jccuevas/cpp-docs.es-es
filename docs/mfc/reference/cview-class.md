---
title: CView (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- views [C++], view classes
- multiple views
- CView class
- document/view architecture
- input, and view class
- MDI [C++], view windows
- print preview, view windows
- windows [C++], views
- child windows, views
- frame windows [C++], views
- user input [C++], interpreting through view class
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
caps.latest.revision: 25
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
ms.openlocfilehash: ce5100a9ee4a1c20df04f79f0c8cd645ae3afce7
ms.lasthandoff: 02/24/2017

---
# <a name="cview-class"></a>CView (clase)
Proporciona la funcionalidad básica para las clases de vista definidas por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class AFX_NOVTABLE CView : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CView::CView](#cview)|Construye un objeto `CView`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CView::DoPreparePrinting](#doprepareprinting)|Muestra el cuadro de diálogo Imprimir y crea el contexto de dispositivo de impresora; Llame al reemplazar el `OnPreparePrinting` función miembro.|  
|[CView::GetDocument](#getdocument)|Devuelve el documento asociado a la vista.|  
|[CView::IsSelected](#isselected)|Comprueba si se selecciona un elemento de documento. Se requiere para la compatibilidad con OLE.|  
|[CView::OnDragEnter](#ondragenter)|Se llama cuando un elemento se arrastra en primer lugar en la región de arrastrar y colocar de una vista.|  
|[CView::OnDragLeave](#ondragleave)|Se llama cuando un elemento arrastrado sale de una vista de la zona de arrastrar y colocar.|  
|[CView::OnDragOver](#ondragover)|Se llama cuando se arrastra un elemento sobre el área de arrastrar y colocar de una vista.|  
|[CView::OnDragScroll](#ondragscroll)|Se llama para determinar si se arrastra el cursor en la región de desplazamiento de la ventana.|  
|[CView::OnDrop](#ondrop)|Se llama cuando se ha quitado un elemento en la región de arrastrar y colocar de una vista, el controlador predeterminado.|  
|[CView::OnDropEx](#ondropex)|Se llama cuando se ha quitado un elemento en la región de arrastrar y colocar de una vista, el controlador principal.|  
|[CView:: OnInitialUpdate](#oninitialupdate)|Se llama después de una vista en primer lugar se adjunta a un documento.|  
|[CView::OnPrepareDC](#onpreparedc)|Llamado antes de la `OnDraw` se llama una función miembro de pantalla o el `OnPrint` se llama la función miembro para la vista previa de impresión o.|  
|[CView::OnScroll](#onscroll)|Se llama cuando se arrastran elementos OLE más allá de los bordes de la vista.|  
|[CView::OnScrollBy](#onscrollby)|Se llama cuando se desplaza una vista que contiene elementos OLE en contexto activos.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CView::OnActivateFrame](#onactivateframe)|Se llama cuando se activa o se desactiva la ventana de marco que contiene la vista.|  
|[CView::OnActivateView](#onactivateview)|Se llama cuando se activa una vista.|  
|[CView:: OnBeginPrinting](#onbeginprinting)|Se llama cuando se inicia un trabajo de impresión; invalidar para asignar recursos de la interfaz (GDI) de dispositivo de gráficos.|  
|[CView:: OnDraw](#ondraw)|Se llama para representar una imagen del documento para presentación en pantalla, impresión o vista previa de impresión. Implementación necesaria.|  
|[OnEndPrinting](#onendprinting)|Se llama cuando finaliza el trabajo de impresión; invalidación para desasignar recursos GDI.|  
|[CView::OnEndPrintPreview](#onendprintpreview)|Se llama cuando se sale de modo de vista previa.|  
|[CView:: OnPreparePrinting](#onprepareprinting)|Se llama antes de que un documento se imprime o muestra una vista previa; invalidación para inicializar el cuadro de diálogo Imprimir.|  
|[CView::OnPrint](#onprint)|Se llama para imprimir u obtener una vista previa de una página del documento.|  
|[CView::OnUpdate](#onupdate)|Se llama para notificar a una vista que su documento ha sido modificado.|  
  
## <a name="remarks"></a>Comentarios  
 Una vista se adjunta a un documento y actúa como intermediario entre el documento y el usuario: la vista procesa una imagen del documento en la pantalla o impresora e interpreta proporcionados por el usuario como operaciones sobre el documento.  
  
 Una vista es un elemento secundario de una ventana de marco. Más de una vista puede compartir una ventana de marco, como en el caso de una ventana divisora. La relación entre una clase de vista, una clase de ventana de marco y una clase de documento se establece mediante un `CDocTemplate` objeto. Cuando el usuario abre una ventana nueva o existente se divide una, el marco de trabajo construye una nueva vista y lo adjunta al documento.  
  
 Una vista se puede adjuntar a un único documento, pero un documento puede tener varias vistas que se adjunta a la vez, por ejemplo, si el documento se muestra en una ventana divisora, o en varias ventanas secundarias en una aplicación de múltiples documentos (MDI) de la interfaz. La aplicación puede admitir distintos tipos de vistas para un tipo de documento determinado; Por ejemplo, un programa de procesamiento de texto puede proporcionar una vista de texto completo de un documento y una vista de esquema que muestra sólo los títulos de sección. Estos tipos de vistas pueden colocarse en ventanas de marco distintas o en paneles independientes de una sola ventana de marco, si utiliza una ventana divisora.  
  
 Una vista puede ser responsable de controlar varios tipos diferentes de entradas, como la entrada de teclado, mouse de entrada o entrada a través de arrastrar y colocar, así como comandos de menús, barras de herramientas o barras de desplazamiento. Una vista recibe comandos reenviados por su ventana de marco. Si la vista no controla un comando determinado, reenvía el comando hacia su documento asociado. Al igual que todos los destinos de comando, una vista controla los mensajes a través de un mapa de mensajes.  
  
 Es responsable de la vista para mostrar y modificar los datos del documento, pero no para almacenarlos. El documento proporciona la vista con la información necesaria acerca de sus datos. Puede permitir el acceso de vista directamente los miembros de datos del documento, o puede proporcionar funciones de miembro en la clase de documento para llamar a la clase de vista.  
  
 Cuando cambian los datos de un documento, la vista de los cambios se llama normalmente el [UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) función para el documento, lo que indica a todas las vistas mediante una llamada a la `OnUpdate` función miembro para cada uno. La implementación predeterminada de `OnUpdate` invalida el área de cliente de la vista. Se puede reemplazar para invalidar sólo aquellas regiones del área de cliente que se asignan a las partes modificadas del documento.  
  
 Usar `CView`, derivar una clase e implementar el `OnDraw` función miembro para realizar la presentación en pantalla. También puede utilizar `OnDraw` para realizar la impresión y vista previa. El marco de trabajo administra el bucle de impresión para impresión y vista previa del documento.  
  
 Una vista controla los mensajes de la barra de desplazamiento con el [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) funciones miembro. Puede implementar en estas funciones de tratamiento de mensajes de barra de desplazamiento o puede usar el `CView` clase derivada [CScrollView](../../mfc/reference/cscrollview-class.md) para controlar el desplazamiento por usted.  
  
 Además `CScrollView`, Microsoft Foundation Class Library proporciona nueve otras clases derivadas de `CView`:  
  
- [CCtrlView](../../mfc/reference/cctrlview-class.md), una vista que permite el uso de documento: vista de arquitectura con enriquecido, lista y árbol de controles de edición.  
  
- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md), una vista que muestra registros de base de datos en controles de cuadro de diálogo.  
  
- [CEditView](../../mfc/reference/ceditview-class.md), una vista que proporciona un editor de texto multilínea. Puede usar un `CEditView` objeto como un control en un cuadro de diálogo, así como una vista en un documento.  
  
- [CFormView](../../mfc/reference/cformview-class.md), una vista desplazable que contiene controles de cuadro de diálogo y se basa en un recurso de plantilla de cuadro de diálogo.  
  
- [CListView](../../mfc/reference/clistview-class.md), una vista que permite el uso de documento: arquitectura de vista con los controles de lista.  
  
- [CRecordView](../../mfc/reference/crecordview-class.md), una vista que muestra registros de base de datos en controles de cuadro de diálogo.  
  
- [CRichEditView](../../mfc/reference/cricheditview-class.md), una vista que permite el uso de documento: vista de arquitectura con enriquecido de controles de edición.  
  
- [CScrollView](../../mfc/reference/cscrollview-class.md), una vista que proporciona automáticamente compatibilidad con desplazamiento.  
  
- [CTreeView](../../mfc/reference/ctreeview-class.md), una vista que permite el uso de documento: arquitectura de vista con los controles de árbol.  
  
 El `CView` clase también tiene una clase de implementación derivada denominada **CPreviewView**, que se usa el marco de trabajo para realizar una vista previa de impresión. Esta clase proporciona compatibilidad para las características exclusivas de la ventana de vista previa de impresión, como una barra de herramientas, la vista previa de página único o doble, y zoom, es, ampliando la imagen de vista previa. No es necesario llamar o reemplazar cualquiera de **CPreviewView**de funciones miembro, a menos que desee implementar su propia interfaz de vista previa de impresión (por ejemplo, si desea admitir la edición en modo de vista previa). Para obtener más información sobre el uso de `CView`, consulte [arquitectura documento/vista](../../mfc/document-view-architecture.md) y [imprimir](../../mfc/printing.md). Además, consulte [30 de nota técnica](../../mfc/tn030-customizing-printing-and-print-preview.md) para obtener más información acerca de cómo personalizar la vista previa de impresión.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CView`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxwin.h  
  
##  <a name="cview"></a>CView::CView  
 Construye un objeto `CView`.  
  
```  
CView();
```  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama al constructor cuando se crea una nueva ventana de marco o se divide una ventana. Invalidar el [OnInitialUpdate](#oninitialupdate) función miembro para inicializar la vista después de que se adjunta el documento.  
  
##  <a name="doprepareprinting"></a>CView::DoPreparePrinting  
 Llame a esta función desde el reemplazo de [OnPreparePrinting](#onprepareprinting) para invocar el cuadro de diálogo Imprimir y crear un contexto de dispositivo de impresora.  
  
```  
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pInfo`  
 Apunta a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura que describe el trabajo de impresión actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la vista previa de impresión o puede comenzar; 0 si se ha cancelado la operación.  
  
### <a name="remarks"></a>Comentarios  
 Comportamiento de esta función depende de si se le llama para la vista previa de impresión o (especificada por el **m_bPreview** miembro de la `pInfo` parámetro). Si se imprime un archivo, esta función invoca el cuadro de diálogo Imprimir, mediante los valores de la [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura `pInfo` apunta a; después de que el usuario ha cerrado el cuadro de diálogo, la función crea un contexto de dispositivo de impresora basado en configuración del usuario especificado en el cuadro de diálogo y devuelve el contexto del dispositivo a través de la `pInfo` parámetro. Este contexto de dispositivo se utiliza para imprimir el documento.  
  
 Si un archivo de vista previa, esta función crea un contexto de dispositivo de impresora con la configuración actual de la impresora; este contexto de dispositivo se utiliza para simular la impresora durante la vista previa.  
  
##  <a name="getdocument"></a>CView::GetDocument  
 Llame a esta función para obtener un puntero al documento de la vista.  
  
```  
CDocument* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [CDocument](../../mfc/reference/cdocument-class.md) objeto asociado a la vista. **NULL** si la vista no se adjunta a un documento.  
  
### <a name="remarks"></a>Comentarios  
 Esto le permite llamar a funciones de miembro del documento.  
  
##  <a name="isselected"></a>CView::IsSelected  
 Llamado por el marco de trabajo para comprobar si se selecciona el elemento de documento especificado.  
  
```  
virtual BOOL IsSelected(const CObject* pDocItem) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDocItem`  
 Señala el elemento de documento que se está probando.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se selecciona el elemento de documento especificado; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función devuelve **FALSE**. Reemplace esta función si va a implementar la selección mediante [CDocItem](../../mfc/reference/cdocitem-class.md) objetos. Debe reemplazar esta función si la vista contiene elementos OLE.  
  
##  <a name="onactivateframe"></a>CView::OnActivateFrame  
 Llamado por el marco de trabajo cuando se activa o se desactiva la ventana de marco que contiene la vista.  
  
```  
virtual void OnActivateFrame(
    UINT nState,  
    CFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `nState`  
 Especifica si la ventana de marco está activado o desactivado. Puede ser uno de los siguientes valores:  
  
- **WA_INACTIVE** la ventana de marco que se va a desactivar.  
  
- **WA_ACTIVE** se activa la ventana de marco a través de algún método distinto de un clic del mouse (por ejemplo, mediante el uso de la interfaz de teclado para seleccionar la ventana).  
  
- **WA_CLICKACTIVE** se activa mediante un clic del mouse en la ventana de marco  
  
 `pFrameWnd`  
 Puntero a la ventana de marco que se van a activar.  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función miembro si desea realizar un procesamiento especial cuando se activa o se desactiva la ventana de marco asociada a la vista. Por ejemplo, [CFormView](../../mfc/reference/cformview-class.md) realiza esta invalidación cuando guarda y restaura el control que tiene el foco.  
  
##  <a name="onactivateview"></a>CView::OnActivateView  
 Llamado por el marco de trabajo cuando una vista está activada o desactivada.  
  
```  
virtual void OnActivateView(
    BOOL bActivate,  
    CView* pActivateView,  
    CView* pDeactiveView);
```  
  
### <a name="parameters"></a>Parámetros  
 `bActivate`  
 Indica si la vista se activa o se desactiva.  
  
 `pActivateView`  
 Señala al objeto de vista que se va a activar.  
  
 `pDeactiveView`  
 Señala al objeto de vista que se ha desactivado.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función establece el foco en la vista que se va a activar. Reemplace esta función si desea realizar un procesamiento especial cuando una vista está activada o desactivada. Por ejemplo, si desea proporcionar indicaciones visuales especiales que distinguen la vista activa de las vistas inactivas, examinaría el `bActivate` parámetro y actualizar la apariencia de la vista en consecuencia.  
  
 El `pActivateView` y `pDeactiveView` parámetros apuntan a la misma vista si se activa la ventana de marco principal de la aplicación sin cambios en la vista activa, por ejemplo, si el foco se están transfiriendo desde otra aplicación a éste, en lugar de una vista a otra dentro de la aplicación o al cambiar entre ventanas secundarias MDI. Esto permite una vista para volver a procesar su paleta, si es necesario.  
  
 Estos parámetros se diferencian cuando [CFrameWnd::SetActiveView](../../mfc/reference/cframewnd-class.md#setactiveview) se llama con una vista diferente de lo que [CFrameWnd::GetActiveView](../../mfc/reference/cframewnd-class.md#getactiveview) devolvería. Esto suele ocurrir con ventanas divisoras.  
  
##  <a name="onbeginprinting"></a>CView:: OnBeginPrinting  
 Lo llama el marco al comenzar un trabajo de impresión o de vista previa de impresión, después de llamar a `OnPreparePrinting` .  
  
```  
virtual void OnBeginPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Apunta al contexto del dispositivo de impresora.  
  
 `pInfo`  
 Apunta a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura que describe el trabajo de impresión actual.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Reemplace esta función para asignar los recursos de GDI, como lápices o fuentes, que se necesitan específicamente para imprimir. Seleccione los objetos GDI en el contexto de dispositivo desde el [OnPrint](#onprint) función de miembro para cada página que los utiliza. Si usa el mismo objeto de vista para realizar la presentación en pantalla y la impresión, use variables independientes para los recursos GDI necesarios para cada presentación; esto le permite actualizar la pantalla durante la impresión.  
  
 También puede usar esta función para realizar inicializaciones que dependan de las propiedades del contexto del dispositivo de impresora. Por ejemplo, el número de páginas necesarias para imprimir el documento puede depender de la configuración que especificó el usuario en el cuadro de diálogo Imprimir (por ejemplo, la longitud de la página). En esta situación, no puede especificar la longitud del documento en el [OnPreparePrinting](#onprepareprinting) función miembro, lo haría normalmente donde; debe esperar a que el contexto de dispositivo de impresora se ha creado en función de la configuración del cuadro de diálogo. [OnBeginPrinting](#onbeginprinting) es la primera función reemplazable que proporciona acceso a la [CDC](../../mfc/reference/cdc-class.md) objeto que representa el contexto de dispositivo de impresora, por lo que puede establecer la longitud del documento desde esta función. Tenga en cuenta que si no se especifica la longitud del documento en este momento, no se muestra una barra de desplazamiento durante la vista previa de impresión.  
  
##  <a name="ondragenter"></a>CView::OnDragEnter  
 Lo llama el marco de trabajo cuando el mouse entra por primera vez la región sin desplazamiento de la ventana de destino.  
  
```  
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDataObject`  
 Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se arrastran en el área de colocación de la vista.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 La posición actual de mouse relativa al área de cliente de la vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de la `DROPEFFECT` tipo enumerado, que indica el tipo de destino que ocurriría si el usuario coloca el objeto en esta posición. El tipo de destino depende normalmente el estado actual de la clave indicado por `dwKeyState`. Una asignación estándar de Estados para `DROPEFFECT` valores es:  
  
- `DROPEFFECT_NONE`No se puede quitar el objeto de datos en esta ventana.  
  
- `DROPEFFECT_LINK`para **MK_CONTROL | MK_SHIFT** crea un vínculo entre el objeto y su servidor.  
  
- `DROPEFFECT_COPY`para **MK_CONTROL** crea una copia del objeto quitada.  
  
- `DROPEFFECT_MOVE`para **MK_ALT** crea una copia del objeto quitado y eliminar el objeto original. Esto suele ser el efecto de colocar de forma predeterminada, cuando la vista puede aceptar este objeto de datos.  
  
 Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Comentarios  
 Implementación predeterminada es no hacer nada y devolver `DROPEFFECT_NONE`.  
  
 Reemplazar esta función para prepararse para las futuras llamadas a la [OnDragOver](#ondragover) función miembro. Se deben recuperar los datos necesarios del objeto de datos en este momento para su uso posterior en el `OnDragOver` función miembro. La vista también debe actualizarse en este momento para proporcionar información visual al usuario. Para obtener más información, vea el artículo [arrastrar y colocar: implementar un destino de colocación](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondragleave"></a>CView::OnDragLeave  
 Lo llama el marco de trabajo durante una operación de arrastre cuando se mueve el mouse fuera del área de colocación válido para esa ventana.  
  
```  
virtual void OnDragLeave();
```  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función si necesita limpiar las acciones realizadas durante la vista actual [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) llamadas, como la eliminación de cualquier información visual al usuario mientras el objeto se arrastra y coloca.  
  
##  <a name="ondragover"></a>CView::OnDragOver  
 Lo llama el marco de trabajo durante una operación de arrastre cuando se mueve el mouse sobre la ventana de destino.  
  
```  
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,  
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDataObject`  
 Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se está arrastrando sobre el destino de colocación.  
  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 La posición actual del mouse relativa al área de cliente de vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de la `DROPEFFECT` tipo enumerado, que indica el tipo de destino que ocurriría si el usuario coloca el objeto en esta posición. El tipo de destino depende a menudo en el estado actual de la clave como se indica en `dwKeyState`. Una asignación estándar de Estados para `DROPEFFECT` valores es:  
  
- `DROPEFFECT_NONE`No se puede quitar el objeto de datos en esta ventana.  
  
- `DROPEFFECT_LINK`para **MK_CONTROL | MK_SHIFT** crea un vínculo entre el objeto y su servidor.  
  
- `DROPEFFECT_COPY`para **MK_CONTROL** crea una copia del objeto quitada.  
  
- `DROPEFFECT_MOVE`para **MK_ALT** crea una copia del objeto quitado y eliminar el objeto original. Esto suele ser el efecto de colocar de forma predeterminada, cuando la vista puede aceptar el objeto de datos.  
  
 Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Comentarios  
 Es la implementación predeterminada no hace nada y devolver `DROPEFFECT_NONE`.  
  
 Reemplazar esta función para proporcionar información visual al usuario durante la operación de arrastre. Puesto que esta función se llama continuamente, debe optimizarse tanto como sea posible cualquier código contenido en él. Para obtener más información, vea el artículo [arrastrar y colocar: implementar un destino de colocación](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondragscroll"></a>CView::OnDragScroll  
 Llamado por el marco antes de llamar a [OnDragEnter](#ondragenter) o [OnDragOver](#ondragover) para determinar si el punto está en la región desplazable.  
  
```  
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwKeyState`  
 Contiene el estado de las teclas modificadoras. Se trata de una combinación de cualquier número de los siguientes: **MK_CONTROL**, **MK_SHIFT**, **MK_ALT**, **MK_LBUTTON**, **MK_MBUTTON**, y **MK_RBUTTON**.  
  
 `point`  
 Contiene la ubicación del cursor, en píxeles, relativo a la pantalla.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de la `DROPEFFECT` tipo enumerado, que indica el tipo de destino que ocurriría si el usuario coloca el objeto en esta posición. El tipo de destino depende normalmente el estado actual de la clave indicado por `dwKeyState`. Una asignación estándar de Estados para `DROPEFFECT` valores es:  
  
- `DROPEFFECT_NONE`No se puede quitar el objeto de datos en esta ventana.  
  
- `DROPEFFECT_LINK`para **MK_CONTROL | MK_SHIFT** crea un vínculo entre el objeto y su servidor.  
  
- `DROPEFFECT_COPY`para **MK_CONTROL** crea una copia del objeto quitada.  
  
- `DROPEFFECT_MOVE`para **MK_ALT** crea una copia del objeto quitado y eliminar el objeto original.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de desplazamiento de arrastrar tiene lugar o se está produciendo en la vista de destino.  
  
 Para obtener más información, vea el ejemplo de conceptos avanzados de MFC [OCLIENT](../../visual-cpp-samples.md).  
  
### <a name="remarks"></a>Comentarios  
 Reemplace esta función cuando desea proporcionar un comportamiento especial para este evento. La implementación predeterminada desplaza automáticamente windows cuando se arrastra el cursor en la región de desplazamiento predeterminado dentro del borde de cada ventana. Para obtener más información, vea el artículo [arrastrar y colocar: implementar un destino de colocación](../../mfc/drag-and-drop-implementing-a-drop-target.md).  
  
##  <a name="ondraw"></a>CView:: OnDraw  
 Llamado por el marco de trabajo para procesar una imagen del documento.  
  
```  
virtual void OnDraw(CDC* pDC) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Señala al contexto de dispositivo que se usará para representar una imagen del documento.  
  
### <a name="remarks"></a>Comentarios  
 El marco de trabajo llama a esta función para realizar la presentación en pantalla, impresión y vista previa de impresión, y pasa un contexto de dispositivo diferentes en cada caso. No hay ninguna implementación predeterminada.  
  
 Debe reemplazar esta función para mostrar la vista del documento. Puede realizar llamadas de dispositivo gráfico (GDI) de la interfaz mediante la [CDC](../../mfc/reference/cdc-class.md) objeto al que apunta el `pDC` parámetro. Puede seleccionar recursos GDI, como lápices o fuentes, en el contexto de dispositivo antes de dibujar y, a continuación, anule la selección de ellos posteriormente. A menudo, el código de dibujo puede ser independiente del dispositivo; es decir, no requiere información sobre el tipo de dispositivo muestra la imagen.  
  
 Para optimizar el dibujo, llame a la [RectVisible](../../mfc/reference/cdc-class.md#rectvisible) función miembro del contexto de dispositivo para averiguar si se dibujará un rectángulo determinado. Si necesita distinguir entre la presentación en pantalla normal e impresión, llame a la [IsPrinting](../../mfc/reference/cdc-class.md#isprinting) función miembro del contexto de dispositivo.  
  
##  <a name="ondrop"></a>CView::OnDrop  
 Lo llama el marco de trabajo cuando el usuario suelta un objeto de datos en un destino de colocación válido.  
  
```  
virtual BOOL OnDrop(
    COleDataObject* pDataObject,  
    DROPEFFECT dropEffect,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDataObject`  
 Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se coloca en el destino de colocación.  
  
 `dropEffect`  
 El efecto de que el usuario ha solicitado.  
  
- `DROPEFFECT_COPY`Crea una copia del objeto de datos que se va a quitar.  
  
- `DROPEFFECT_MOVE`Mueve el objeto de datos a la ubicación del mouse actual.  
  
- `DROPEFFECT_LINK`Crea un vínculo entre un objeto de datos y su servidor.  
  
 `point`  
 La posición actual del mouse relativa al área de cliente de vista.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la operación de colocar se realizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada y devuelve **FALSE**.  
  
 Reemplazar esta función para implementar el efecto de colocar de OLE en el área de cliente de la vista. Se puede examinar el objeto de datos a través de `pDataObject` para datos de Portapapeles formatos y los datos se coloca en el punto especificado.  
  
> [!NOTE]
>  El marco no llama a esta función si no hay un reemplazo para [OnDropEx](#ondropex) en esta clase de vista.  
  
##  <a name="ondropex"></a>CView::OnDropEx  
 Lo llama el marco de trabajo cuando el usuario suelta un objeto de datos en un destino de colocación válido.  
  
```  
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,  
    DROPEFFECT dropDefault,  
    DROPEFFECT dropList,  
    CPoint point);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDataObject`  
 Apunta a la [COleDataObject](../../mfc/reference/coledataobject-class.md) que se coloca en el destino de colocación.  
  
 `dropDefault`  
 El efecto que el usuario ha elegido para la operación de colocar de forma predeterminada según el estado actual de la clave. Puede ser `DROPEFFECT_NONE`. Efectos de colocar se explican en la sección Comentarios.  
  
 `dropList`  
 Una lista de los efectos de colocación que admite el origen de colocación. Los valores de efecto de colocar se pueden combinar mediante una operación OR bit a bit ( **|**) operación. Efectos de colocar se explican en la sección Comentarios.  
  
 `point`  
 La posición actual del mouse relativa al área de cliente de vista.  
  
### <a name="return-value"></a>Valor devuelto  
 El efecto que dan como resultado del intento de colocar en la ubicación especificada por `point`. Debe ser uno de los valores indicados por *dropEffectList*. Efectos de colocar se explican en la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada es no hacer nada y devolver un valor ficticio (-1) para indicar que el marco de trabajo debe llamar a la [OnDrop](#ondrop) controlador.  
  
 Reemplazar esta función para implementar el efecto de un botón secundario del mouse de arrastrar y colocar. Botón secundario del mouse de arrastrar y colocar normalmente muestra un menú de opciones cuando se suelta el botón derecho.  
  
 El reemplazo de `OnDropEx` debe consultar a la derecha del botón del mouse. Puede llamar a [GetKeyState](http://msdn.microsoft.com/library/windows/desktop/ms646301) o almacenar el estado de la derecha del botón del mouse desde el [OnDragEnter](#ondragenter) controlador.  
  
-   Si el botón derecho del mouse está inactivo, el reemplazo debe mostrar un menú emergente que ofrece a los efectos de colocación que admite el origen de colocación.  
  
    -   Examinar `dropList` para determinar los efectos de colocación admitidos por el origen de colocación. Habilitar sólo estas acciones en el menú emergente.  
  
    -   Utilice [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) para establecer la acción predeterminada basándose en `dropDefault`.  
  
    -   Por último, realice la acción que se indica mediante la selección del usuario en el menú emergente.  
  
-   Si el botón derecho del mouse no está inactivo, el reemplazo debe procesar como una solicitud de entrega estándar. Utilice el efecto de colocación especificado en `dropDefault`. Como alternativa, la invalidación puede devolver el valor ficticio (-1) para indicar que `OnDrop` controlará esta operación de colocar.  
  
 Utilice `pDataObject` para examinar el `COleDataObject` para datos del Portapapeles de formato y los datos se coloca en el punto especificado.  
  
 La acción asociada a una operación de colocar describen los efectos de colocación. Consulte la siguiente lista de efectos de colocar:  
  
- `DROPEFFECT_NONE`No se permitirá una caída.  
  
- `DROPEFFECT_COPY`Se realizará una operación de copia.  
  
- `DROPEFFECT_MOVE`Se realizará una operación de movimiento.  
  
- `DROPEFFECT_LINK`Se puede establecer un vínculo desde los datos colocados en los datos originales.  
  
- `DROPEFFECT_SCROLL`Indica que una operación de desplazamiento de arrastrar tiene lugar o se está produciendo en el destino.  
  
 Para obtener más información acerca de cómo establecer el comando de menú predeterminado, consulte [SetMenuDefaultItem](http://msdn.microsoft.com/library/windows/desktop/ms647996) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] y [CMenu::GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu) en este volumen.  
  
##  <a name="onendprinting"></a>OnEndPrinting  
 Llamado por el marco de trabajo cuando se imprime un documento o una vista previa.  
  
```  
virtual void OnEndPrinting(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Apunta al contexto del dispositivo de impresora.  
  
 `pInfo`  
 Apunta a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura que describe el trabajo de impresión actual.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada. Reemplazar esta función para liberar los recursos GDI asignados en el [OnBeginPrinting](#onbeginprinting) función miembro.  
  
##  <a name="onendprintpreview"></a>CView::OnEndPrintPreview  
 Lo llama el marco de trabajo cuando el usuario sale del modo de vista previa de impresión.  
  
```  
virtual void OnEndPrintPreview(
    CDC* pDC,  
    CPrintInfo* pInfo,  
    POINT point,  
    CPreviewView* pView);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Apunta al contexto del dispositivo de impresora.  
  
 `pInfo`  
 Apunta a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura que describe el trabajo de impresión actual.  
  
 `point`  
 Especifica el punto en la página que se mostró por última vez en modo de vista previa.  
  
 `pView`  
 Señala al objeto view que se utiliza para la vista previa.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función llama a la [OnEndPrinting](#onendprinting) función miembro y restaura la ventana de marco principal al estado que tenía antes de la vista previa de impresión comenzó. Reemplazar esta función para realizar un procesamiento especial cuando se termina el modo de vista previa. Por ejemplo, si desea mantener la posición del usuario en el documento al cambiar de modo de vista previa al modo de presentación normal, puede desplazarse a la posición descrita por el `point` parámetro y el `m_nCurPage` miembro de la `CPrintInfo` estructura que la `pInfo` parámetro señala a.  
  
 Llame siempre a la versión de la clase base `OnEndPrintPreview` desde el reemplazo, normalmente al final de la función.  
  
##  <a name="oninitialupdate"></a>CView:: OnInitialUpdate  
 Lo llama el marco de trabajo después de la vista se adjunta al documento en primer lugar, pero antes de que la vista se muestra inicialmente.  
  
```  
virtual void OnInitialUpdate();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función llama a la [OnUpdate](#onupdate) función miembro sin información de sugerencia (es decir, usando los valores predeterminados de 0 para el `lHint` parámetro y **NULL** para el `pHint` parámetro). Reemplazar esta función para realizar cualquier inicialización única que requiera información sobre el documento. Por ejemplo, si la aplicación tiene documentos de tamaño fijo, puede utilizar esta función para inicializar los límites de una vista desplazable en función del tamaño del documento. Si la aplicación admite documentos de tamaño variable, utilice [OnUpdate](#onupdate) actualizar el desplazamiento limita cada vez los cambios del documento.  
  
##  <a name="onpreparedc"></a>CView::OnPrepareDC  
 Llamado por el marco antes de la [OnDraw](#ondraw) se llama la función miembro de presentación en pantalla y antes de la [OnPrint](#onprint) función miembro se llama para cada página durante la vista previa de impresión o.  
  
```  
virtual void OnPrepareDC(
    CDC* pDC,  
    CPrintInfo* pInfo = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Señala al contexto de dispositivo que se usará para representar una imagen del documento.  
  
 `pInfo`  
 Apunta a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura que describe el trabajo de impresión actual si `OnPrepareDC` se llama para la vista previa de impresión o; el `m_nCurPage` miembro especifica la página que se va a imprimir. Este parámetro es **NULL** si `OnPrepareDC` se llama para presentación en pantalla.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función no hace nada si se llama a la función para presentación en pantalla. Sin embargo, esta función se reemplaza en clases derivadas, como [CScrollView](../../mfc/reference/cscrollview-class.md), para ajustar los atributos de contexto de dispositivo; por lo tanto, siempre se debe llamar la implementación de la clase base al principio de su invalidación.  
  
 Si se llama a la función de impresión, la implementación predeterminada examina la información de la página almacenada en la `pInfo` parámetro. Si no se ha especificado la longitud del documento, `OnPrepareDC` supone el documento que se va a una página y se detiene el bucle de impresión después de imprimir una página. La función detiene el bucle de impresión estableciendo la `m_bContinuePrinting` miembro de la estructura a **FALSE**.  
  
 Reemplazar `OnPrepareDC` para cualquiera de los siguientes motivos:  
  
-   Para ajustar los atributos de contexto de dispositivo según sea necesario para la página especificada. Por ejemplo, si necesita establecer el modo de asignación u otras características del contexto de dispositivo, hacerlo en esta función.  
  
-   Para realizar la paginación en tiempo de impresión. Normalmente especifica la longitud del documento cuando comienza la impresión, usando la [OnPreparePrinting](#onprepareprinting) función miembro. Sin embargo, si no conoce de antemano cuánto tiempo el documento es (por ejemplo, al imprimir un número indeterminado de registros de una base de datos), reemplazar `OnPrepareDC` para buscar el final del documento mientras se imprime. Cuando no hay ninguna otra parte de que se imprima el documento, establecer el `m_bContinuePrinting` miembro de la `CPrintInfo` estructura a **FALSE**.  
  
-   Para enviar los códigos de escape a la impresora en la página por página. Para enviar los códigos de escape de `OnPrepareDC`, llame a la **Escape** función miembro de la `pDC` parámetro.  
  
 Llame a la versión de la clase base de `OnPrepareDC` al principio de su invalidación.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCDocView&#183;](../../mfc/codesnippet/cpp/cview-class_1.cpp)]  
  
##  <a name="onprepareprinting"></a>CView:: OnPreparePrinting  
 Llamado por el marco antes de imprimir un documento o una vista previa.  
  
```  
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pInfo`  
 Apunta a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura que describe el trabajo de impresión actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero para iniciar la impresión. 0 si se ha cancelado el trabajo de impresión.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada.  
  
 Debe reemplazar esta función para habilitar la impresión y vista previa. Llame a la [DoPreparePrinting](#doprepareprinting) función miembro, pasándole el `pInfo` parámetro y, a continuación, devolver su valor devuelto; `DoPreparePrinting` muestra el cuadro de diálogo Imprimir y crea un contexto de dispositivo de impresora. Si desea inicializar el cuadro de diálogo Imprimir con valores distintos de los predeterminados, asigne valores a los miembros de `pInfo`. Por ejemplo, si conoce la longitud del documento, pasar el valor a la [SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage) función miembro de `pInfo` antes de llamar a `DoPreparePrinting`. Este valor se muestra en la línea: cuadro en la parte del intervalo del cuadro de diálogo Imprimir.  
  
 `DoPreparePrinting`no muestra el cuadro de diálogo de impresión de un trabajo de vista previa. Si desea omitir el cuadro de diálogo de impresión de un trabajo de impresión, compruebe que la **m_bPreview** miembro de `pInfo` es **FALSE** y, a continuación, se establece en **TRUE** antes de pasarlo a `DoPreparePrinting`; restablecerla para **FALSE** posteriormente.  
  
 Si necesita realizan inicializaciones que requieren acceso a la `CDC` reemplazar el objeto que representa el contexto de dispositivo de impresora (por ejemplo, si necesita saber el tamaño de página antes de especificar la longitud del documento), el `OnBeginPrinting` función miembro.  
  
 Si desea establecer el valor de la **m_nNumPreviewPages** o **m_strPageDesc** los miembros de la `pInfo` parámetro, hacerlo después de llamar a `DoPreparePrinting`. El `DoPreparePrinting` conjuntos de la función miembro **m_nNumPreviewPages** en el valor que se encuentra en la aplicación. Archivo INI y establece **m_strPageDesc** a su valor predeterminado.  
  
### <a name="example"></a>Ejemplo  
  Invalidar `OnPreparePrinting` y llame a `DoPreparePrinting` desde la invalidación para que se muestre un cuadro de diálogo Imprimir y crear una controlador de dominio de la impresora para el marco de trabajo.  
  
 [!code-cpp[NVC_MFCDocView&#184;](../../mfc/codesnippet/cpp/cview-class_2.cpp)]  
  
 Si sabe cuántas páginas contiene el documento, establezca el número máximo de páginas en `OnPreparePrinting` antes de llamar a `DoPreparePrinting`. El marco de trabajo mostrará el número máximo de página en el cuadro "para" del cuadro de diálogo Imprimir.  
  
 [!code-cpp[NVC_MFCDocView&#185;](../../mfc/codesnippet/cpp/cview-class_3.cpp)]  
  
##  <a name="onprint"></a>CView::OnPrint  
 Llamado por el marco de trabajo para imprimir o vista previa una página del documento.  
  
```  
virtual void OnPrint(
    CDC* pDC,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Apunta al contexto del dispositivo de impresora.  
  
 `pInfo`  
 Apunta a un `CPrintInfo` estructura que describe el trabajo de impresión actual.  
  
### <a name="remarks"></a>Comentarios  
 Para cada página que se va a imprimir, el marco de trabajo llama a esta función inmediatamente después de llamar a la [OnPrepareDC](#onpreparedc) función miembro. Especifica la página que se está imprimiendo la `m_nCurPage` miembro de la [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) estructura `pInfo` apunta a. La implementación predeterminada llama el [OnDraw](#ondraw) función miembro y pasa el contexto de dispositivo de impresora.  
  
 Reemplazar esta función para cualquiera de los siguientes motivos:  
  
-   Para permitir la impresión de documentos de varias páginas. Presentar sólo la parte del documento que corresponde a la página que se está imprimiendo. Si utiliza `OnDraw` para realizar el procesamiento, puede ajustar el origen de la ventanilla para que se imprime sólo la parte adecuada del documento.  
  
-   Para hacer que la imagen impresa sea diferente de la imagen en pantalla (es decir, si la aplicación no es WYSIWYG). En lugar de pasar la impresora en el contexto de dispositivo para `OnDraw`, use el contexto de dispositivo para presentar una imagen de uso de atributos no se muestran en la pantalla.  
  
     Si necesita recursos de GDI para la impresión que no se usan para presentación en pantalla, selecciónelos en el contexto de dispositivo antes de dibujar y anular su selección posteriormente. Se deben asignar estos recursos GDI en [OnBeginPrinting](#onbeginprinting) y publique en [OnEndPrinting](#onendprinting).  
  
-   Para implementar los encabezados o pies de página. Todavía puede usar `OnDraw` para realizar la representación restringiendo el área que puede imprimir.  
  
 Tenga en cuenta que el **m_rectDraw** miembro de la `pInfo` parámetro describe el área imprimible de la página en unidades lógicas.  
  
 No llame a `OnPrepareDC` en el reemplazo de `OnPrint`; el marco llama `OnPrepareDC` automáticamente antes de llamar a `OnPrint`.  
  
### <a name="example"></a>Ejemplo  
 El siguiente es un esquema para un invalidado `OnPrint` función:  
  
 [!code-cpp[NVC_MFCDocView&#186;](../../mfc/codesnippet/cpp/cview-class_4.cpp)]  
  
 Para obtener otro ejemplo, vea [CRichEditView::PrintInsideRect](../../mfc/reference/cricheditview-class.md#printinsiderect).  
  
##  <a name="onscroll"></a>CView::OnScroll  
 Llamado por el marco de trabajo para determinar si el desplazamiento es posible.  
  
```  
virtual BOOL OnScroll(
    UINT nScrollCode,  
    UINT nPos,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `nScrollCode`  
 Se desplaza en un código de barras de desplazamiento que indica al usuario la solicitud. Este parámetro se compone de dos partes: un byte de orden inferior, que determina el tipo de desplazamiento que se produzca horizontalmente, y un byte de orden superior, que determina el tipo de desplazamiento que se produzca vertical:  
  
- **SB_BOTTOM** se desplaza hacia abajo.  
  
- **SB_LINEDOWN** se desplaza una línea hacia abajo.  
  
- **SB_LINEUP** sube una línea.  
  
- **SB_PAGEDOWN** se desplaza una página hacia abajo.  
  
- **SB_PAGEUP** desplaza una página hacia arriba.  
  
- **SB_THUMBTRACK** arrastrar el cuadro de desplazamiento a la posición especificada. Se especifica la posición actual en `nPos`.  
  
- **SB_TOP** se desplaza a la parte superior.  
  
 `nPos`  
 Contiene la posición actual del cuadro de desplazamiento si el código de la barra de desplazamiento es **SB_THUMBTRACK**; de lo contrario, no se utiliza. Según el intervalo de desplazamiento inicial, `nPos` puede ser negativo y debe convertirse a una `int` si es necesario.  
  
 `bDoScroll`  
 Determina si debe hacer realidad la acción de desplazamiento especificada. Si **es TRUE,** , a continuación, el desplazamiento debe tener lugar; si **FALSE**, no debería se produzca el desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si `bDoScroll` es **TRUE** y realmente se ha desplazado la vista, a continuación, devolver distinto de cero; en caso contrario, 0. Si `bDoScroll` es **FALSE**, a continuación, devolver el valor que se habría devuelto si `bDoScroll` fueron **TRUE**, aunque en realidad no hace el desplazamiento.  
  
### <a name="remarks"></a>Comentarios  
 En un caso con el marco de trabajo llama a esta función `bDoScroll` establecido en **TRUE** cuando la vista recibe un mensaje de la barra de desplazamiento. En este caso, debe desplazarse realmente la vista. En el caso anterior, esta función se invoca con `bDoScroll` establecido en **FALSE** cuando un elemento OLE inicialmente se arrastra dentro de la región de desplazamiento automático de un destino de colocación antes de desplazamiento realiza en realidad. En este caso, se debe realmente se desplaza la vista.  
  
##  <a name="onscrollby"></a>CView::OnScrollBy  
 Lo llama el marco de trabajo cuando el usuario ve un área más allá de la vista actual del documento, ya sea arrastrando un elemento OLE en los bordes de la vista actual o manipular las barras de desplazamiento vertical u horizontal.  
  
```  
virtual BOOL OnScrollBy(
    CSize sizeScroll,  
    BOOL bDoScroll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `sizeScroll`  
 Número de píxeles de desplazamiento horizontal y verticalmente.  
  
 `bDoScroll`  
 Determina si la vista de desplazamiento se produce. Si **es TRUE,** , a continuación, el desplazamiento se realiza; si **FALSE**, no se produzca el desplazamiento.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si la vista puede desplazar; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 En clases derivadas este método comprueba si la vista es desplazable en la dirección que el usuario solicita y, a continuación, actualiza la región de nuevo si es necesario. Esta función se invoca automáticamente [CWnd::OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll) y [CWnd::OnVScroll](../../mfc/reference/cwnd-class.md#onvscroll) para realizar la solicitud de desplazamiento real.  
  
 La implementación predeterminada de este método no cambia la vista, pero si no se llama, la vista no se desplaza en un `CScrollView`-clase derivada.  
  
 Si el documento ancho o alto supera 32767 píxeles, desplazarse más allá de 32767 fallará porque `OnScrollBy` se llama con no es válido `sizeScroll` argumento.  
  
##  <a name="onupdate"></a>CView::OnUpdate  
 Llamado por el marco de trabajo después de que se ha modificado el documento de la vista; Esta función se invoca [UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews) y permite que la vista actualice su presentación para reflejar las modificaciones.  
  
```  
virtual void OnUpdate(
    CView* pSender,  
    LPARAM lHint,  
    CObject* pHint);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSender`  
 Apunta a la vista que se modificó el documento, o **NULL** si todas las vistas que se van a actualizarse.  
  
 `lHint`  
 Contiene información acerca de las modificaciones.  
  
 `pHint`  
 Apunta a un objeto que almacena información sobre las modificaciones.  
  
### <a name="remarks"></a>Comentarios  
 También se denomina la implementación predeterminada de [OnInitialUpdate](#oninitialupdate). La implementación predeterminada invalida toda el área cliente, lo marca para pintar cuando la próxima `WM_PAINT` recibe el mensaje. Reemplace esta función si desea actualizar solo las regiones que se asignan a las partes modificadas del documento. Para ello debe pasar información acerca de las modificaciones utilizando los parámetros de la sugerencia.  
  
 Usar `lHint`, definir valores de sugerencia especial, normalmente una máscara de bits o un tipo enumerado y que el documento pase uno de estos valores. Usar `pHint`, derive una clase de sugerencia de [CObject](../../mfc/reference/cobject-class.md) y tener el documento pasar un puntero a un objeto de sugerencia; al reemplazar `OnUpdate`, utilice el [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof) para determinar el tipo de tiempo de ejecución del objeto de sugerencia de función miembro.  
  
 Normalmente no debería realizar cualquier dibujo directamente desde `OnUpdate`. En su lugar, determinar el rectángulo de describir, en coordenadas de dispositivo, el área que requiere la actualización. Pase este rectángulo para [CWnd::InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect). Esto hace que el dibujo para que se produzca la próxima vez que un [WM_PAINT](http://msdn.microsoft.com/library/windows/desktop/dd145213) recibe el mensaje.  
  
 Si `lHint` es 0 y `pHint` es **NULL**, el documento ha enviado una notificación de actualización genérico. Si recibe una notificación de actualización genérico a una vista, o si no puede descodificar las sugerencias, debe invalidar su área cliente completo.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MDIDOCVW de MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [CFrameWnd (clase)](../../mfc/reference/cframewnd-class.md)   
 [CSplitterWnd (clase)](../../mfc/reference/csplitterwnd-class.md)   
 [CDC (clase)](../../mfc/reference/cdc-class.md)   
 [CDocTemplate (clase)](../../mfc/reference/cdoctemplate-class.md)   
 [CDocument (clase)](../../mfc/reference/cdocument-class.md)

