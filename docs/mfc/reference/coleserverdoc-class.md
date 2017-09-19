---
title: Clase COleServerDoc | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
dev_langs:
- C++
helpviewer_keywords:
- servers, OLE
- OLE server applications, managing server documents
- container/server applications
- OLE server documents
- COleServerDoc class
- server documents, OLE
- OLE containers, server documents
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
caps.latest.revision: 24
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
ms.openlocfilehash: db50c2a5709fbc07d0e0db99a4cffc733c4b6ead
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="coleserverdoc-class"></a>Clase COleServerDoc
La clase base para los documentos de servidor OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleServerDoc::COleServerDoc](#coleserverdoc)|Construye un objeto `COleServerDoc`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleServerDoc::ActivateDocObject](#activatedocobject)|Activa el documento DocObject asociado.|  
|[COleServerDoc::ActivateInPlace](#activateinplace)|Activa el documento para su edición en contexto.|  
|[COleServerDoc::DeactivateAndUndo](#deactivateandundo)|Desactiva la interfaz de usuario del servidor.|  
|[COleServerDoc::DiscardUndoState](#discardundostate)|Descarta la información de estado de deshacer.|  
|[COleServerDoc::GetClientSite](#getclientsite)|Recupera un puntero al propio `IOleClientSite` interfaz.|  
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|Devuelve un puntero a un elemento que representa todo el documento.|  
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|Devuelve el rectángulo de recorte actual para su edición en contexto.|  
|[COleServerDoc::GetItemPosition](#getitemposition)|Devuelve el rectángulo de posición actual, con respecto al área de cliente de la aplicación contenedora para edición en contexto.|  
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|Devuelve el factor de zoom en píxeles.|  
|[COleServerDoc::IsDocObject](#isdocobject)|Determina si el documento es un objeto DocObject.|  
|[COleServerDoc::IsEmbedded](#isembedded)|Indica si el documento está incrustado en un documento contenedor o ejecución independiente.|  
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|Devuelve `TRUE` si el elemento está activado en su lugar.|  
|[COleServerDoc::NotifyChanged](#notifychanged)|Notifica a los contenedores que el usuario ha cambiado el documento.|  
|[COleServerDoc::NotifyClosed](#notifyclosed)|Notifica a los contenedores que el usuario cerró el documento.|  
|[COleServerDoc::NotifyRename](#notifyrename)|Notifica a los contenedores que el usuario ha cambiado el nombre del documento.|  
|[COleServerDoc::NotifySaved](#notifysaved)|Notifica a los contenedores que el usuario ha guardado el documento.|  
|[COleServerDoc::OnDeactivate](#ondeactivate)|Lo llama el marco de trabajo cuando el usuario desactiva un elemento que se ha activado en su lugar.|  
|[COleServerDoc::OnDeactivateUI](#ondeactivateui)|Llamado por el marco para destruir controles y otros elementos de interfaz de usuario creados para la activación en contexto.|  
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|Llamado por el marco de trabajo cuando se activa o se desactiva la ventana de marco de documento del contenedor.|  
|[COleServerDoc::OnResizeBorder](#onresizeborder)|Llamado por el marco cuando cambia la ventana de marco o la ventana de documento de la aplicación contenedora.|  
|[COleServerDoc::OnShowControlBars](#onshowcontrolbars)|Llamado por el marco de trabajo para mostrar u ocultar las barras de control de edición en contexto.|  
|[COleServerDoc::OnUpdateDocument](#onupdatedocument)|Lo llama el marco de trabajo cuando se guarda un documento de servidor es un elemento incrustado, actualizar copia del contenedor del elemento.|  
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|Cambia la posición del marco de edición en contexto.|  
|[COleServerDoc::SaveEmbedding](#saveembedding)|Indica a la aplicación de contenedor para guardar el documento.|  
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|Desplaza el documento contenedor.|  
|[COleServerDoc::UpdateAllItems](#updateallitems)|Notifica a los contenedores que el usuario ha cambiado el documento.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleServerDoc::CreateInPlaceFrame](#createinplaceframe)|Llamado por el marco para crear una ventana de marco de edición en contexto.|  
|[COleServerDoc::DestroyInPlaceFrame](#destroyinplaceframe)|Llamado por el marco para destruir una ventana de marco de edición en contexto.|  
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|Reemplazar esta función para crear un nuevo `CDocObjectServer` objeto e indicar que este documento es un contenedor de DocObject.|  
|[COleServerDoc::OnClose](#onclose)|Llamado por el marco cuando solicita un contenedor para cerrar el documento.|  
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|Ejecuta un comando especificado o muestra ayuda para el comando.|  
|[COleServerDoc::OnFrameWindowActivate](#onframewindowactivate)|Llamado por el marco de trabajo cuando se activa o se desactiva la ventana de marco del contenedor.|  
|[COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem)|Se llama para obtener un `COleServerItem` que representa el documento completo; se utiliza para obtener un elemento incrustado. Implementación necesaria.|  
|[COleServerDoc::OnReactivateAndUndo](#onreactivateandundo)|Llamado por el marco para deshacer los cambios realizados durante la edición en contexto.|  
|[COleServerDoc::OnSetHostNames](#onsethostnames)|Llamado por el marco de trabajo cuando un contenedor establece el título de ventana para un objeto incrustado.|  
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|Llamado por el marco para situar la ventana de marco de edición en contexto dentro de la ventana de la aplicación contenedora.|  
|[COleServerDoc::OnShowDocument](#onshowdocument)|Llamado por el marco de trabajo para mostrar u ocultar el documento.|  
  
## <a name="remarks"></a>Comentarios  
 Puede contener un documento de servidor [COleServerItem](../../mfc/reference/coleserveritem-class.md) objetos que representan la interfaz del servidor para los elementos incrustados o vinculados. Cuando una aplicación de servidor se inicia por un contenedor para editar un elemento incrustado, el elemento se carga como su propio documento de servidor; el `COleServerDoc` objeto contiene una sola `COleServerItem` objeto, formada por todo el documento. Cuando una aplicación de servidor se inicia por un contenedor para editar un elemento vinculado, se carga un documento existente del disco; una parte del contenido del documento está resaltada para indicar que el elemento vinculado.  
  
 `COleServerDoc`los objetos también pueden contener elementos de la [COleClientItem](../../mfc/reference/coleclientitem-class.md) clase. Esto le permite crear aplicaciones de servidor del contenedor. El marco de trabajo proporciona funciones para almacenar correctamente la `COleClientItem` elementos mientras atiende la `COleServerItem` objetos.  
  
 Si la aplicación de servidor no admite vínculos, un documento de servidor siempre contendrá un único elemento de servidor, que representa todo el objeto incrustado como un documento. Si la aplicación de servidor admite vínculos, se debe crear un elemento del servidor cada vez que se copia una selección en el Portapapeles.  
  
 Usar `COleServerDoc`, derivar una clase e implementar la [OnGetEmbeddedItem](#ongetembeddeditem) función miembro, que permite al servidor admiten objetos incrustados. Derivar una clase de `COleServerItem` para implementar los elementos en sus documentos y devolver objetos de esa clase de `OnGetEmbeddedItem`.  
  
 Para admitir los elementos vinculados, `COleServerDoc` proporciona el [OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem) función miembro. Puede usar la implementación predeterminada o anularlo si tiene su propia forma de administrar los elementos de documento.  
  
 Es necesario un `COleServerDoc`-clase derivada para cada tipo de servidor compatible con la aplicación de documento. Por ejemplo, si la aplicación de servidor es compatible con las hojas de cálculo y gráficos, necesita dos `COleServerDoc`-las clases derivadas.  
  
 Para obtener más información sobre los servidores, vea el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocument](../../mfc/reference/cdocument-class.md)  
  
 [COleDocument](../../mfc/reference/coledocument-class.md)  
  
 [COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)  
  
 `COleServerDoc`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="activatedocobject"></a>COleServerDoc::ActivateDocObject  
 Activa el documento DocObject asociado.  
  
```  
void ActivateDocObject();
```  
  
### <a name="remarks"></a>Comentarios  
 De forma predeterminada, `COleServerDoc` no admite documentos activos (también denominados DocObjects). Para habilitar esta compatibilidad, consulte [GetDocObjectServer](#getdocobjectserver) y la clase [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md).  
  
##  <a name="activateinplace"></a>COleServerDoc::ActivateInPlace  
 Activa el elemento para su edición en contexto.  
  
```  
BOOL ActivateInPlace();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; de lo contrario, 0, lo que indica que el elemento está completamente abierto.  
  
### <a name="remarks"></a>Comentarios  
 Esta función realiza todas las operaciones necesarias para la activación en contexto. Crea una ventana de marco en contexto, lo activa y tamaños al elemento, configura compartidos menús y otros controles, desplaza el elemento en la vista y establece el foco en la ventana de marco en contexto.  
  
 Esta función llama a la implementación predeterminada de [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow). Llame a esta función si la aplicación admite otro verbo para la activación en contexto (como reproducir).  
  
##  <a name="coleserverdoc"></a>COleServerDoc::COleServerDoc  
 Construye un `COleServerDoc` objeto sin necesidad de conectarse con las DLL del sistema OLE.  
  
```  
COleServerDoc();
```  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar a [COleLinkingDoc::Register](../../mfc/reference/colelinkingdoc-class.md#register) para abrir las comunicaciones con OLE. Si está utilizando [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md) en la aplicación, `COleLinkingDoc::Register` es llamado por `COleLinkingDoc`de implementación de `OnNewDocument`, `OnOpenDocument`, y `OnSaveDocument`.  
  
##  <a name="createinplaceframe"></a>COleServerDoc::CreateInPlaceFrame  
 El marco de trabajo llama a esta función para crear una ventana de marco de edición en contexto.  
  
```  
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pParentWnd`  
 Puntero a la ventana primaria de la aplicación contenedora.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la ventana de marco en contexto, o **NULL** si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada usa la información especificada en la plantilla de documento para crear el marco. La vista utilizada es la primera vista creada para el documento. Esta vista se separa en el marco original temporalmente y se adjunta al marco recién creado.  
  
 Avanzada reemplazable.  
  
##  <a name="deactivateandundo"></a>COleServerDoc::DeactivateAndUndo  
 Llame a esta función si deshacer compatible con la aplicación y el usuario elige deshacer después de activar un elemento, pero antes de editarlo.  
  
```  
BOOL DeactivateAndUndo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Al llamar a esta función, si la aplicación se escribe utilizando la biblioteca Microsoft Foundation Class, [COleClientItem::OnDeactivateAndUndo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo) para llamar, que desactiva la interfaz de usuario del servidor.  
  
##  <a name="destroyinplaceframe"></a>COleServerDoc::DestroyInPlaceFrame  
 El marco de trabajo llama a esta función para destruir una ventana de marco en contexto y devolver al servidor de la ventana de documento de la aplicación a su estado antes de la activación en contexto.  
  
```  
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFrameWnd`  
 Puntero a la ventana de marco en contexto para ser destruidos.  
  
### <a name="remarks"></a>Comentarios  
 Avanzada reemplazable.  
  
##  <a name="discardundostate"></a>COleServerDoc::DiscardUndoState  
 Si el usuario realiza una operación de edición que no se puede deshacer, llame a esta función para forzar la aplicación de contenedor para descartar la información de estado de deshacer.  
  
```  
BOOL DiscardUndoState();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero en caso de éxito; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función se proporciona para que los servidores que admiten deshacer pueden liberar los recursos que sea consumidos por la información de estado de deshacer no se puede usar.  
  
##  <a name="getclientsite"></a>COleServerDoc::GetClientSite  
 Recupera un puntero al propio `IOleClientSite` interfaz.  
  
```  
LPOLECLIENTSITE GetClientSite() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Recupera un puntero al propio [IOleClientSite](http://msdn.microsoft.com/library/windows/desktop/ms693706) interfaz.  
  
##  <a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer  
 Reemplazar esta función para crear un nuevo `CDocObjectServer` elemento y devolver un puntero a él.  
  
```  
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDocSite`  
 Puntero a la `IOleDocumentSite` interfaz que se conectará el servidor de este documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un `CDocObjectServer`; **NULL** si la operación ha fallado.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se activa un servidor DocObject, la devolución de no **NULL** puntero muestra que el cliente puede admitir DocObjects. La implementación predeterminada devuelve **NULL**.  
  
 Una implementación típica de un documento que admite DocObjects simplemente asignará un nuevo `CDocObjectServer` de objetos y devolver al llamador. Por ejemplo:  
  
 [!code-cpp[NVC_MFCOleServer&3;](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]  
  
##  <a name="getembeddeditem"></a>COleServerDoc::GetEmbeddedItem  
 Llame a esta función para obtener un puntero a un elemento que representa todo el documento.  
  
```  
COleServerItem* GetEmbeddedItem();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento que representa el documento completo; **NULL** si la operación ha fallado.  
  
### <a name="remarks"></a>Comentarios  
 Llama a [COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem), una función virtual con ninguna implementación predeterminada.  
  
##  <a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect  
 Llame a la `GetItemClipRect` la función miembro para obtener las coordenadas del rectángulo de recorte del elemento que se está editando en su lugar.  
  
```  
void GetItemClipRect(LPRECT lpClipRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpClipRect`  
 Puntero a un `RECT` estructura o un `CRect` objeto que recibe las coordenadas del rectángulo de recorte del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Las coordenadas están en píxeles con respecto al área de cliente de la ventana de aplicación de contenedor.  
  
 No debería ocurrir dibujo fuera del rectángulo de recorte. Normalmente, el dibujo se restringe automáticamente. Utilice esta función para determinar si el usuario se ha desplazado fuera de la parte visible del documento. Si es así, desplazar el documento contenedor según sea necesario mediante una llamada a [ScrollContainerBy](#scrollcontainerby).  
  
##  <a name="getitemposition"></a>COleServerDoc::GetItemPosition  
 Llame a la `GetItemPosition` para obtener las coordenadas del elemento que se está editando en lugar de función miembro.  
  
```  
void GetItemPosition(LPRECT lpPosRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPosRect`  
 Puntero a un `RECT` estructura o un `CRect` objeto que recibe las coordenadas del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Las coordenadas están en píxeles con respecto al área de cliente de la ventana de aplicación de contenedor.  
  
 La posición del elemento que se puede comparar con el rectángulo de recorte actual para determinar el alcance a la que el elemento esté visible (o no) en la pantalla.  
  
##  <a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor  
 El `GetZoomFactor` función miembro determina el factor de zoom de"" de un elemento que se ha activado para la edición en contexto.  
  
```  
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,  
    LPSIZE lpSizeDenom = NULL,  
    LPCRECT lpPosRect = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *lpSizeNum*  
 Puntero a un objeto de clase `CSize` que contendrá el numerador del factor de zoom. Puede ser **NULL**.  
  
 *lpSizeDenom*  
 Puntero a un objeto de clase `CSize` que contendrá el denominador del factor de zoom. Puede ser **NULL**.  
  
 `lpPosRect`  
 Puntero a un objeto de clase `CRect` que describe la posición del elemento nuevo. Si este argumento es **NULL**, la función utiliza la posición del elemento actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se activa el elemento en lugar de edición y el factor de zoom es distinto de 100% (1:1); en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 El factor de zoom, en píxeles, que es la proporción de tamaño del elemento a su tamaño actual. Si la aplicación no ha establecido la extensión del elemento, su tamaño natural (según lo determinado por [COleServerItem::OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)) se utiliza.  
  
 La función establece sus primeros dos argumentos en el numerador y el denominador "factor de zoom." del elemento Si el elemento no se está editando en su lugar, la función establece estos argumentos a un valor predeterminado de 100% (o 1:1) y devuelve cero. Para obtener más información, consulte 40 Nota técnica, [en lugar MFC/OLE cambiar el tamaño y zoom](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md).  
  
##  <a name="isdocobject"></a>COleServerDoc::IsDocObject  
 Determina si el documento es un objeto DocObject.  
  
```  
BOOL IsDocObject() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si el documento es DocObject; de lo contrario, **FALSE**.  
  
##  <a name="isembedded"></a>COleServerDoc::IsEmbedded  
 Llame a la `IsEmbedded` para determinar si el documento representa un objeto incrustado en un contenedor de la función miembro.  
  
```  
BOOL IsEmbedded() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `COleServerDoc` objeto es un documento que representa un objeto incrustado en un contenedor; de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Un documento que se cargan desde un archivo no se incrusta aunque pueden ser manipulados por una aplicación de contenedor como un vínculo. Para incrustar, se considera un documento que está incrustado en un documento contenedor.  
  
##  <a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive  
 Llame a la `IsInPlaceActive` la función miembro para determinar si el elemento está actualmente en estado activo en contexto.  
  
```  
BOOL IsInPlaceActive() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la `COleServerDoc` objeto está activo en su lugar; de lo contrario, 0.  
  
##  <a name="notifychanged"></a>COleServerDoc::NotifyChanged  
 Llame a esta función para notificar a todos los elementos vinculados conectados al documento que ha cambiado el documento.  
  
```  
void NotifyChanged();
```  
  
### <a name="remarks"></a>Comentarios  
 Normalmente, se llama a esta función cuando el usuario cambie algunos atributos globales, como las dimensiones del documento del servidor. Si un elemento OLE está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En aplicaciones de contenedor escritas con la biblioteca Microsoft Foundation Class, el [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) función miembro de `COleClientItem` se llama.  
  
> [!NOTE]
>  Esta función se incluye por compatibilidad con OLE 1. Las nuevas aplicaciones deben utilizar [UpdateAllItems](#updateallitems).  
  
##  <a name="notifyclosed"></a>COleServerDoc::NotifyClosed  
 Llame a esta función para notificar a los contenedores que se ha cerrado el documento.  
  
```  
void NotifyClosed();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario elige el comando Cerrar en el menú archivo, `NotifyClosed` llama a `COleServerDoc`de implementación de la [OnCloseDocument](../../mfc/reference/cdocument-class.md#onclosedocument) función miembro. En aplicaciones de contenedor escritas con la biblioteca Microsoft Foundation Class, el [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) función miembro de `COleClientItem` se llama.  
  
##  <a name="notifyrename"></a>COleServerDoc::NotifyRename  
 Llame a esta función cuando el usuario cambia el nombre del documento de servidor.  
  
```  
void NotifyRename(LPCTSTR lpszNewName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszNewName`  
 Puntero a una cadena que especifica el nuevo nombre del documento de servidor. por lo general, suele ser una ruta de acceso completa.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario elige el comando Guardar como en el menú archivo, `NotifyRename` llama a `COleServerDoc`de implementación de la [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument) función miembro. Esta función se notifica a los archivos DLL, que a su vez notificar a los contenedores del sistema OLE. En aplicaciones de contenedor escritas con la biblioteca Microsoft Foundation Class, el [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) función miembro de `COleClientItem` se llama.  
  
##  <a name="notifysaved"></a>COleServerDoc::NotifySaved  
 Llame a esta función cuando el usuario guarda el documento de servidor.  
  
```  
void NotifySaved();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando el usuario elige el comando Guardar en el menú archivo, `NotifySaved` es llamado por `COleServerDoc`de implementación de [OnSaveDocument](../../mfc/reference/cdocument-class.md#onsavedocument). Esta función se notifica a los archivos DLL, que a su vez notificar a los contenedores del sistema OLE. En aplicaciones de contenedor escritas con la biblioteca Microsoft Foundation Class, el [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) función miembro de `COleClientItem` se llama.  
  
##  <a name="onclose"></a>COleServerDoc::OnClose  
 Llamado por el marco cuando un contenedor solicita que se cierre el documento de servidor.  
  
```  
virtual void OnClose(OLECLOSE dwCloseOption);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCloseOption`  
 Un valor de la enumeración `OLECLOSE`. Este parámetro puede tener uno de los valores siguientes:  
  
- `OLECLOSE_SAVEIFDIRTY`El archivo se guarda si se ha modificado.  
  
- `OLECLOSE_NOSAVE`El archivo se cierra sin estar guardado.  
  
- `OLECLOSE_PROMPTSAVE`Si se ha modificado el archivo, el usuario se le pide confirmación para guardarlo.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `CDocument::OnCloseDocument`.  
  
 Para obtener más información y valores adicionales, consulte [OLECLOSE](http://msdn.microsoft.com/library/windows/desktop/ms680623) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="ondeactivate"></a>COleServerDoc::OnDeactivate  
 Llamado por el marco de trabajo cuando el usuario desactiva un elemento incrustado o vinculado que está activo actualmente en el contexto.  
  
```  
virtual void OnDeactivate();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función restaura la interfaz de usuario de la aplicación contenedora a su estado original y destruye los menús y otros controles que se crearon para la activación en contexto.  
  
 La información de estado de deshacer incondicionalmente se debería liberar en este momento.  
  
 Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md)...  
  
##  <a name="ondeactivateui"></a>COleServerDoc::OnDeactivateUI  
 Se llama cuando el usuario desactiva un elemento que se ha activado en su lugar.  
  
```  
virtual void OnDeactivateUI(BOOL bUndoable);
```  
  
### <a name="parameters"></a>Parámetros  
 `bUndoable`  
 Especifica si se pueden deshacer los cambios de edición.  
  
### <a name="remarks"></a>Comentarios  
 Esta función restaura a su estado original, ocultar los menús y otros controles que se crearon para la activación en contexto interfaz de usuario de la aplicación contenedora.  
  
 El marco siempre establece `bUndoable` a **FALSE**. Si el servidor permite deshacer y hay una operación que se puede deshacer, llame a la implementación de clase base con `bUndoable` establecido en **TRUE**.  
  
##  <a name="ondocwindowactivate"></a>COleServerDoc::OnDocWindowActivate  
 El marco de trabajo llama a esta función para activar o desactivar una ventana de documento para su edición en contexto.  
  
```  
virtual void OnDocWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 `bActivate`  
 Especifica si la ventana de documento está activado o desactivado.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada se quita o agrega los elementos de la interfaz de usuario de nivel de marco según corresponda. Reemplace esta función si desea realizar acciones adicionales cuando se activa o desactiva el documento que contiene el elemento.  
  
 Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md)...  
  
##  <a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd  
 El marco de trabajo llama a esta función para ejecutar un comando especificado o muestra ayuda para el comando.  
  
```  
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,  
    DWORD nCmdID,  
    DWORD nCmdExecOpt,  
    VARIANTARG* pvarargIn,  
    VARIANTARG* pvarargOut);
```  
  
### <a name="parameters"></a>Parámetros  
 `pguidCmdGroup`  
 Puntero a un GUID que identifica un conjunto de comandos. Puede ser **NULL** para indicar el grupo de comandos de manera predeterminada.  
  
 `nCmdID`  
 Comando para ejecutar. Debe estar en el grupo identificado por `pguidCmdGroup`.  
  
 *nCmdExecOut*  
 La forma en el objeto debe ejecutar el comando, uno o varios de los siguientes valores de la **OLECMDEXECOPT** (enumeración):  
  
 **OLECMDEXECOPT_DODEFAULT**  
  
 **OLECMDEXECOPT_PROMPTUSER**  
  
 **OLECMDEXECOPT_DONTPROMPTUSER**  
  
 **OLECMDEXECOPT_SHOWHELP**  
  
 `pvarargIn`  
 Puntero a un **VARIANTARG** que contiene los argumentos de entrada para el comando. Puede ser **NULL**.  
  
 `pvarargOut`  
 Puntero a un **VARIANTARG** para recibir los valores devueltos de la salida del comando. Puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si es correcto; en caso contrario, uno de los siguientes códigos de error:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Se produjo un error inesperado|  
|**E_FAIL**|Se produjo el error|  
|**E_NOTIMPL**|Indica MFC sí debería intentar traducir y enviar el comando|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`no es **NULL** pero no especifica un grupo de comandos reconocidos|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`no se reconoce como un comando válido en el grupo`pguidCmdGroup`|  
|**OLECMDERR_DISABLED**|El comando identificado por `nCmdID` está deshabilitado y no se puede ejecutar|  
|**OLECMDERR_NOHELP**|Llamador más frecuentes para obtener ayuda sobre el comando identificado por `nCmdID` pero no hay ayuda disponible|  
|**OLECMDERR_CANCELED**|El usuario canceló la ejecución|  
  
### <a name="remarks"></a>Comentarios  
 `COleCmdUI`puede utilizarse para habilitar, actualizar y establecer otras propiedades de los comandos de interfaz de usuario de DocObject. Después de los comandos de inicialización, puede ejecutarlas con `OnExecOleCmd`.  
  
 El marco de trabajo llama a la función antes de intentar traducir y enviar un comando de documentos OLE. No es necesario reemplazar esta función para controlar los comandos de documento estándares de OLE, pero debe proporcionar un reemplazo para esta función si desea administrar sus propios comandos personalizados o controlar los comandos que aceptan parámetros o devuelven resultados.  
  
 La mayoría de los comandos no toman argumentos o valores devueltos. Para la mayoría de los comandos que el llamador pueda pasar **NULL**s para `pvarargIn` y `pvarargOut`. Para los comandos que esperan que los valores de entrada, el llamador puede declarar e inicializar un **VARIANTARG** variable y pasar un puntero a la variable `pvarargIn`. Para los comandos que requieren un valor único, el argumento puede almacenarse directamente en el **VARIANTARG** y pasa a la función. Se deben empaquetar varios argumentos dentro de la **VARIANTARG** mediante uno de los tipos compatibles (como `IDispatch` y **SAFEARRAY** ).  
  
 De forma similar, si un comando devuelve argumentos, el llamador debe declarar un **VARIANTARG**, inicialícelo `VT_EMPTY`y pasar su dirección en `pvarargOut`. Si un comando devuelve un valor único, puede almacenar el valor directamente en el objeto `pvarargOut`. Se deben empaquetar varios valores de salida de alguna manera apropiada para el **VARIANTARG**.  
  
 La implementación de la clase base de esta función recorrerá la **OLE_COMMAND_MAP** estructuras asociadas con el destino del comando e intente enviar el comando a un controlador adecuado. Implementación de la clase base solo funciona con los comandos que no aceptan argumentos o valores devueltos. Si necesita controlar los comandos que aceptan argumentos o valores devueltos, debe reemplazar esta función y trabajar con el `pvarargIn` y `pvarargOut` parámetros usted mismo.  
  
##  <a name="onframewindowactivate"></a>COleServerDoc::OnFrameWindowActivate  
 El marco de trabajo llama a esta función cuando se activa o se desactiva la ventana de marco de la aplicación contenedora.  
  
```  
virtual void OnFrameWindowActivate(BOOL bActivate);
```  
  
### <a name="parameters"></a>Parámetros  
 `bActivate`  
 Especifica si la ventana de marco está activado o desactivado.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada, cancela la ventana de marco puede estar en cualquier modo de ayuda. Reemplace esta función si desea realizar un procesamiento especial cuando se activa o desactiva la ventana de marco.  
  
 Para obtener más información, vea el artículo [activación](../../mfc/activation-cpp.md)...  
  
##  <a name="ongetembeddeditem"></a>COleServerDoc:: OnGetEmbeddedItem  
 Llamado por el marco cuando una aplicación llama a la aplicación de servidor para crear o editar un elemento incrustado.  
  
```  
virtual COleServerItem* OnGetEmbeddedItem() = 0;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un elemento que representa el documento completo; **NULL** si la operación ha fallado.  
  
### <a name="remarks"></a>Comentarios  
 No hay ninguna implementación predeterminada. Debe reemplazar esta función para devolver un objeto que representa el documento completo. El valor devuelto debe ser un objeto de un `COleServerItem`-clase derivada.  
  
##  <a name="onreactivateandundo"></a>COleServerDoc::OnReactivateAndUndo  
 El marco de trabajo llama a esta función cuando el usuario decide deshacer los cambios realizados en los elementos que se han activado en su lugar, cambiar y desactiva posteriormente.  
  
```  
virtual BOOL OnReactivateAndUndo();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada no hace nada excepto retorno **FALSE** para indicar el error.  
  
 Reemplace esta función si la aplicación admite deshacer. Suele realizar la operación de deshacer y activar el elemento mediante una llamada a `ActivateInPlace`. Si la aplicación está escrita con la biblioteca Microsoft Foundation Class, llamada `COleClientItem::ReactivateAndUndo` hace que llamen a esta función.  
  
##  <a name="onresizeborder"></a>COleServerDoc::OnResizeBorder  
 El marco de trabajo llama a esta función cuando cambian de tamaño de ventanas de marco de la aplicación contenedora.  
  
```  
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,  
    LPOLEINPLACEUIWINDOW lpUIWindow,  
    BOOL bFrame);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpRectBorder`  
 Puntero a un `RECT` estructura o un `CRect` objeto que especifica las coordenadas del borde.  
  
 `lpUIWindow`  
 Puntero a un objeto de clase **IOleInPlaceUIWindow** que posee la sesión de edición en el contexto actual.  
  
 *fotogramas b*  
 **TRUE** si `lpUIWindow` apunta a la ventana de marco de nivel superior de la aplicación contenedora, o **FALSE** si `lpUIWindow` apunta a la ventana de marco de nivel de documento de la aplicación contenedora.  
  
### <a name="remarks"></a>Comentarios  
 Esta función cambia de tamaño y ajusta las barras de herramientas y otros elementos de interfaz de usuario según el nuevo tamaño de ventana.  
  
 Para obtener más información, consulte [IOleInPlaceUIWindow](http://msdn.microsoft.com/library/windows/desktop/ms680716) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 Avanzada reemplazable.  
  
##  <a name="onsethostnames"></a>COleServerDoc::OnSetHostNames  
 Llamado por el marco de trabajo cuando el contenedor establece o cambia los nombres de host para este documento.  
  
```  
virtual void OnSetHostNames(
    LPCTSTR lpszHost,  
    LPCTSTR lpszHostObj);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszHost`  
 Puntero a una cadena que especifica el nombre de la aplicación contenedora.  
  
 `lpszHostObj`  
 Puntero a una cadena que especifica el nombre del contenedor para el documento.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada, cambia el título del documento para todas las vistas que hacen referencia a este documento.  
  
 Reemplace esta función si la aplicación establece los títulos a través de un mecanismo diferente.  
  
##  <a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects  
 El marco de trabajo llama a esta función para situar la ventana de marco de edición en contexto dentro de la ventana de marco de la aplicación contenedora.  
  
```  
virtual void OnSetItemRects(
    LPCRECT lpPosRect,  
    LPCRECT lpClipRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPosRect`  
 Puntero a un `RECT` estructura o un `CRect` objeto que especifica la posición de la ventana de marco en contexto con respecto al área de cliente de la aplicación contenedora.  
  
 `lpClipRect`  
 Puntero a un `RECT` estructura o un `CRect` objeto que especifica el rectángulo de recorte de la ventana de marco en contexto con respecto al área de cliente de la aplicación contenedora.  
  
### <a name="remarks"></a>Comentarios  
 Reemplazar esta función para actualizar el factor de zoom de la vista, si es necesario.  
  
 Esta función normalmente se llama en respuesta a un `RequestPositionChange` llamar, aunque se puede llamar en cualquier momento por el contenedor para solicitar un cambio en la posición del elemento en el contexto.  
  
##  <a name="onshowcontrolbars"></a>COleServerDoc::OnShowControlBars  
 El marco de trabajo llama a esta función para mostrar u ocultar las barras de control de la aplicación de servidor asociadas a la ventana de marco identificada por `pFrameWnd`.  
  
```  
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,  
    BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 `pFrameWnd`  
 Puntero a la ventana de marco cuyas barras de control deben estar ocultas o se muestra.  
  
 `bShow`  
 Determina si se muestran barras de control o se oculta.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada enumera todas las barras de controles que pertenecen a esa ventana de marco y oculta o muestra.  
  
##  <a name="onshowdocument"></a>COleServerDoc::OnShowDocument  
 El marco llama el `OnShowDocument` funcionar cuando el documento de servidor debe ser oculto o se muestra.  
  
```  
virtual void OnShowDocument(BOOL bShow);
```  
  
### <a name="parameters"></a>Parámetros  
 `bShow`  
 Especifica si la interfaz de usuario al documento deben mostrarse u ocultarse.  
  
### <a name="remarks"></a>Comentarios  
 Si `bShow` es **TRUE**, la implementación predeterminada activa la aplicación de servidor, si es necesario y hace que la aplicación de contenedor desplazar la ventana para que el elemento está visible. Si `bShow` es **FALSE**, la implementación predeterminada desactiva el elemento mediante una llamada a `OnDeactivate`, destruye u oculta todas las ventanas de marco que se han creado para el documento, excepto el primero. Si no queda ningún documento visible, la implementación predeterminada oculta la aplicación de servidor.  
  
##  <a name="onupdatedocument"></a>COleServerDoc::OnUpdateDocument  
 Llamado por el marco al guardar un documento que es un elemento incrustado en un documento compuesto.  
  
```  
virtual BOOL OnUpdateDocument();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el documento se actualizó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama el [COleServerDoc::NotifySaved](#notifysaved) y [COleServerDoc::SaveEmbedding](#saveembedding) las funciones de miembro y, a continuación, marca el documento como limpio. Reemplace esta función si desea realizar el procesamiento cuando se actualiza un elemento incrustado especial.  
  
##  <a name="requestpositionchange"></a>COleServerDoc::RequestPositionChange  
 Llame a esta función miembro para que la aplicación cambie la posición del elemento.  
  
```  
void RequestPositionChange(LPCRECT lpPosRect);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpPosRect`  
 Puntero a un `RECT` estructura o un `CRect` objeto que contiene la posición del elemento nuevo.  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se denomina (junto con `UpdateAllItems`) cuando ha cambiado los datos de un elemento de activo en contexto. Después de esta llamada, el contenedor puede o no se puede realizar el cambio mediante una llamada a `OnSetItemRects`. La posición resultante podría ser diferente del solicitado.  
  
##  <a name="saveembedding"></a>COleServerDoc::SaveEmbedding  
 Llame a esta función para indicar a la aplicación para guardar el objeto incrustado.  
  
```  
void SaveEmbedding();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función se invoca automáticamente desde `OnUpdateDocument`. Tenga en cuenta que esta función hace que el elemento se actualice en el disco, por lo que normalmente se llama sólo como resultado de una acción de usuario específico.  
  
##  <a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy  
 Llame a la `ScrollContainerBy` función miembro a la cantidad, en píxeles, de desplazamiento del documento contenedor indicado por `sizeScroll`.  
  
```  
BOOL ScrollContainerBy(CSize sizeScroll);
```  
  
### <a name="parameters"></a>Parámetros  
 `sizeScroll`  
 Indica cuánto se desplaza el documento contenedor.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Los valores positivos indican el desplazamiento hacia abajo y a la derecha. los valores negativos indican el desplazamiento hacia arriba y hacia la izquierda.  
  
##  <a name="updateallitems"></a>COleServerDoc::UpdateAllItems  
 Llame a esta función para notificar a todos los elementos vinculados conectados al documento que ha cambiado el documento.  
  
```  
void UpdateAllItems(
    COleServerItem* pSender,  
    LPARAM lHint = 0L,  
    CObject* pHint = NULL,  
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSender`  
 Puntero al elemento que se modificó el documento, o **NULL** si todos los elementos que se van a actualizarse.  
  
 `lHint`  
 Contiene información acerca de la modificación.  
  
 `pHint`  
 Puntero a un objeto que almacena información sobre la modificación.  
  
 `nDrawAspect`  
 Determina cómo se dibujarse el elemento. Se trata de un valor de la `DVASPECT` (enumeración). Este parámetro puede tener uno de los valores siguientes:  
  
- `DVASPECT_CONTENT`Elemento se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.  
  
- `DVASPECT_THUMBNAIL`Se representa en una representación "miniatura" para que se puede mostrar en una herramienta de exploración.  
  
- `DVASPECT_ICON`Elemento se representa mediante un icono.  
  
- `DVASPECT_DOCPRINT`Elemento se representa como si se imprimiera utilizando el comando Imprimir en el menú archivo.  
  
### <a name="remarks"></a>Comentarios  
 Se suele llamar a esta función cuando el usuario cambie el documento de servidor. Si un elemento OLE está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En aplicaciones de contenedor escritas con la biblioteca Microsoft Foundation Class, el [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) función miembro de `COleClientItem` se llama.  
  
 Esta función llama a la `OnUpdate` función de miembro para cada uno de los elementos del documento excepto el envío, pasando `pHint`, `lHint`, y `nDrawAspect`. Use estos parámetros para pasar información a los artículos acerca de las modificaciones realizadas en el documento. Puede codificar información mediante `lHint` o puede definir un `CObject`-clase derivada para almacenar información sobre las modificaciones y pasar un objeto de esa clase utilizando `pHint`. Invalidar el `OnUpdate` función miembro en su `COleServerItem`-clase derivada para optimizar la actualización de cada elemento dependiendo de si ha cambiado su presentación.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Clase COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [COleDocument (clase)](../../mfc/reference/coledocument-class.md)   
 [Clase COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)   
 [COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)

