---
title: Clase COleServerItem | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
dev_langs:
- C++
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3165a11aace54ce2062a6321acc7f911fbdc39
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="coleserveritem-class"></a>Clase COleServerItem
Proporciona la interfaz del servidor a elementos OLE.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleServerItem : public CDocItem  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="protected-constructors"></a>Constructores protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::COleServerItem](#coleserveritem)|Construye un objeto `COleServerItem`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::AddOtherClipboardData](#addotherclipboarddata)|Coloca los formatos de presentación y conversión en un `COleDataSource` objeto.|  
|[COleServerItem::CopyToClipboard](#copytoclipboard)|Copia el elemento en el Portapapeles.|  
|[COleServerItem:: DoDragDrop](#dodragdrop)|Realiza una operación de arrastrar y colocar.|  
|[COleServerItem::GetClipboardData](#getclipboarddata)|Obtiene el origen de datos para su uso en la transferencia de datos (arrastrar y colocar o Portapapeles).|  
|[COleServerItem::GetDocument](#getdocument)|Devuelve el documento de servidor que contiene el elemento.|  
|[COleServerItem::GetEmbedSourceData](#getembedsourcedata)|Obtiene el **CF_EMBEDSOURCE** datos de un elemento OLE.|  
|[COleServerItem::GetItemName](#getitemname)|Devuelve el nombre del elemento. Usar solo los elementos vinculados.|  
|[COleServerItem::GetLinkSourceData](#getlinksourcedata)|Obtiene el `CF_LINKSOURCE` datos de un elemento OLE.|  
|[COleServerItem::GetObjectDescriptorData](#getobjectdescriptordata)|Obtiene el **CF_OBJECTDESCRIPTOR** datos de un elemento OLE.|  
|[COleServerItem::IsConnected](#isconnected)|Indica si el elemento está actualmente conectado a un contenedor activo.|  
|[COleServerItem::IsLinkedItem](#islinkeditem)|Indica si el elemento representa un elemento vinculado de OLE.|  
|[COleServerItem::NotifyChanged](#notifychanged)|Actualiza todos los contenedores con actualización automática de vínculos.|  
|[COleServerItem::OnDoVerb](#ondoverb)|Se llama para ejecutar un verbo.|  
|[COleServerItem:: OnDraw](#ondraw)|Se llama cuando el contenedor solicita para dibujar el elemento; implementación necesaria.|  
|[COleServerItem::OnDrawEx](#ondrawex)|Se llama para dibujar elemento especializadas.|  
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|Lo llama el marco para obtener los datos que se van a copiar en el Portapapeles.|  
|[COleServerItem::OnGetExtent](#ongetextent)|Lo llama el marco de trabajo para recuperar el tamaño del elemento OLE.|  
|[COleServerItem::OnInitFromData](#oninitfromdata)|Lo llama el marco para inicializar un elemento OLE utilizando el contenido del objeto de transferencia de datos especificado.|  
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|Se llama para determinar si los elementos vinculados requieren actualización.|  
|[COleServerItem::OnRenderData](#onrenderdata)|Recupera los datos como parte de la representación aplazada.|  
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|Recupera los datos en un `CFile` objeto como parte de la representación aplazada.|  
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|Recupera los datos en un `HGLOBAL` como parte de la representación aplazada.|  
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|Se llama para establecer la combinación de colores del elemento.|  
|[COleServerItem::OnSetData](#onsetdata)|Se llama para establecer los datos del artículo.|  
|[COleServerItem::OnSetExtent](#onsetextent)|Lo llama el marco para establecer el tamaño del elemento OLE.|  
|[COleServerItem::OnUpdate](#onupdate)|Cuando alguna parte del documento, el elemento pertenece a se cambia la llama.|  
|[COleServerItem::OnUpdateItems](#onupdateitems)|Se llama para actualizar la caché de presentación de todos los elementos en el documento de servidor.|  
|[COleServerItem::SetItemName](#setitemname)|Establece el nombre del elemento. Usar solo los elementos vinculados.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::GetDataSource](#getdatasource)|Obtiene el objeto que se usa para almacenar los formatos de conversión.|  
|[COleServerItem::OnHide](#onhide)|Lo llama el marco para ocultar el elemento OLE.|  
|[COleServerItem::OnOpen](#onopen)|Lo llama el marco de trabajo para mostrar el elemento OLE en su propia ventana de nivel superior.|  
|[COleServerItem::OnShow](#onshow)|Se llama cuando el contenedor solicita para mostrar el elemento.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleServerItem::m_sizeExtent](#m_sizeextent)|Informa al servidor acerca de la cantidad del elemento OLE está visible.|  
  
## <a name="remarks"></a>Comentarios  
 Puede representar un elemento vinculado algunos o todos de un documento de servidor. Un elemento incrustado siempre representa un documento de todo el servidor.  
  
 La `COleServerItem` clase define varias funciones miembro reemplazables que se llaman a las bibliotecas de vínculos dinámicos de sistema OLE (DLL), normalmente en respuesta a las solicitudes de la aplicación contenedora. Estas funciones miembro que la aplicación de contenedor manipular el elemento indirectamente de varias maneras, como mostrarlo, ejecutando sus verbos o recuperar sus datos en diferentes formatos.  
  
 Usar `COleServerItem`, derive una clase de él e implementar la [OnDraw](#ondraw) y [Serialize](../../mfc/reference/cobject-class.md#serialize) funciones miembro. El `OnDraw` función proporciona la representación del metarchivo de un elemento, lo que permite que se muestre cuando una aplicación de contenedor abre un documento compuesto. El `Serialize` función de `CObject` proporciona la representación nativa de un elemento, lo que permite un elemento incrustado para transferirse entre las aplicaciones de servidor y un contenedor. [OnGetExtent](#ongetextent) proporciona el tamaño natural del elemento en el contenedor, lo que permite el contenedor cambiar el tamaño del elemento.  
  
 Para obtener más información acerca de los servidores y otros temas relacionados, vea el artículo [servidores: implementar un servidor](../../mfc/servers-implementing-a-server.md) y "Crear una aplicación de contenedor y servidor" en el artículo [contenedores: características avanzadas](../../mfc/containers-advanced-features.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 `COleServerItem`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="addotherclipboarddata"></a>  COleServerItem::AddOtherClipboardData  
 Llame a esta función para colocar los formatos de presentación y conversión para el elemento OLE especificado `COleDataSource` objeto.  
  
```  
void AddOtherClipboardData(COleDataSource* pDataSource);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDataSource`  
 Puntero a la `COleDataSource` objeto en que se deben colocar los datos.  
  
### <a name="remarks"></a>Comentarios  
 Se debe haber implementado el [OnDraw](#ondraw) función de miembro para proporcionar el formato de presentación (una imagen de metarchivo) para el elemento. Para admitir otros formatos de conversión, regístrelos con el [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto devuelto por [GetDataSource](#getdatasource) e invalide el [OnRenderData](#onrenderdata) función miembro proporcionar datos en los formatos que desee admitir.  
  
##  <a name="coleserveritem"></a>  COleServerItem::COleServerItem  
 Construye un `COleServerItem` objeto y lo agrega a la colección del documento de servidor de elementos de documento.  
  
```  
COleServerItem(
    COleServerDoc* pServerDoc,  
    BOOL bAutoDelete);
```  
  
### <a name="parameters"></a>Parámetros  
 `pServerDoc`  
 Puntero al documento que contendrá el nuevo elemento.  
  
 `bAutoDelete`  
 Marca que indica si se puede eliminar el objeto cuando se suelta un vínculo a él. Establezca esta propiedad en **FALSE** si la `COleServerItem` objeto es una parte integral de los datos del documento que deben eliminar. Establezca esta propiedad en **TRUE** si el objeto es una estructura secundaria que se usa para identificar un intervalo en los datos del documento que se pueden eliminar mediante el marco de trabajo.  
  
##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard  
 Llame a esta función para copiar el elemento OLE en el Portapapeles.  
  
```  
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bIncludeLink`  
 Establezca esta propiedad en **TRUE** si vincular datos deben copiarse en el Portapapeles. Establezca esta propiedad en **FALSE** si la aplicación de servidor no admite vínculos.  
  
### <a name="remarks"></a>Comentarios  
 La función utiliza la [OnGetClipboardData](#ongetclipboarddata) función de miembro para crear un [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto que contiene los datos del elemento OLE en los formatos admitidos. La función, a continuación, coloca el `COleDataSource` objeto en el Portapapeles mediante el uso de la [COleDataSource:: SetClipboard](../../mfc/reference/coledatasource-class.md#setclipboard) función. El `COleDataSource` objeto incluye datos nativos del elemento y su representación en `CF_METAFILEPICT` formato, así como datos en los formatos de conversión decide admitir. Se debe haber implementado [Serialize](../../mfc/reference/cobject-class.md#serialize) y [OnDraw](#ondraw) para esta función miembro para que funcione.  
  
##  <a name="dodragdrop"></a>  COleServerItem:: DoDragDrop  
 Llame a la `DoDragDrop` función de miembro para realizar una operación de arrastrar y colocar.  
  
```  
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,  
    CPoint ptOffset,  
    BOOL bIncludeLink = FALSE,  
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,  
    LPCRECT lpRectStartDrag = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *lpRectItem*  
 Rectángulo del elemento en la pantalla, en píxeles, respecto al área de cliente.  
  
 `ptOffset`  
 El desplazamiento de `lpItemRect` que era la posición del mouse en el momento de la operación de arrastre.  
  
 `bIncludeLink`  
 Establezca esta propiedad en **TRUE** si vincular datos deben copiarse en el Portapapeles. Establézcalo en **FALSE** si la aplicación no admite vínculos.  
  
 `dwEffects`  
 Determina los efectos que permitirá al origen de arrastre en la operación de arrastre (una combinación de copiar, mover y vínculo).  
  
 `lpRectStartDrag`  
 Puntero al rectángulo que define donde realmente comienza la operación de arrastre. Para obtener más información, vea la sección Comentarios que se muestra más adelante.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor de la enumeración `DROPEFFECT`. Si es `DROPEFFECT_MOVE`, se deben quitar los datos originales.  
  
### <a name="remarks"></a>Comentarios  
 No se inicie inmediatamente la operación de arrastrar y colocar. Espera hasta que el cursor del mouse deja el rectángulo especificado por `lpRectStartDrag` o hasta que un número especificado de milisegundos transcurridos. Si `lpRectStartDrag` es **NULL**, un rectángulo predeterminado se utiliza para que la operación de arrastrar se inicia cuando el cursor del mouse mueve un píxel.  
  
 El tiempo de retraso especificado por un valor de una clave del registro. Puede cambiar el tiempo de retraso mediante una llamada a [CWinApp::WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) o [CWinApp:: Writeprofileint](../../mfc/reference/cwinapp-class.md#writeprofileint). Si no especifica el tiempo de retardo, se utiliza un valor predeterminado de 200 milisegundos. Tiempo de retardo de arrastre se almacena como sigue:  
  
-   Tiempo de retardo de arrastre de Windows NT se almacena en HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay.  
  
-   Tiempo de retardo de arrastre de Windows 3.x se almacena en el archivo WIN. Archivo INI, en la [sección Windows}.  
  
-   Tiempo de retardo de arrastre de Windows 95 ó 98 se almacena en una versión en caché de WIN. INI.  
  
 Para obtener más información acerca de cómo arrastrar información de retraso se almacena en el registro o la. El archivo INI, consulte [WriteProfileString](http://msdn.microsoft.com/library/windows/desktop/ms725504) en el SDK de Windows.  
  
##  <a name="getclipboarddata"></a>  COleServerItem::GetClipboardData  
 Llame a esta función para rellenar especificado [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto con todos los datos que se van a copiar en el Portapapeles si llamado [CopyToClipboard](#copytoclipboard) (también se transferirán los mismos datos si se llama a [DoDragDrop](#dodragdrop)).  
  
```  
void GetClipboardData(
    COleDataSource* pDataSource,  
    BOOL bIncludeLink = FALSE,  
    LPPOINT lpOffset = NULL,  
    LPSIZE lpSize = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDataSource`  
 Puntero a la `COleDataSource` objeto que recibirá los datos del elemento OLE en todos los formatos admitidos.  
  
 `bIncludeLink`  
 **TRUE** si vincular datos deben copiarse en el Portapapeles. **FALSE** si la aplicación de servidor no admite vínculos.  
  
 `lpOffset`  
 El desplazamiento, en píxeles, del cursor del mouse desde el origen del objeto.  
  
 `lpSize`  
 El tamaño del objeto en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Esta función llama a la [GetEmbedSourceData](#getembedsourcedata) función de miembro para obtener los datos nativos para el elemento OLE y llama el [AddOtherClipboardData](#addotherclipboarddata) para obtener el formato de presentación y cualquier función miembro admite los formatos de conversión. Si `bIncludeLink` es **TRUE**, también llama a la función [GetLinkSourceData](#getlinksourcedata) para obtener los datos de enlace para el elemento.  
  
 Reemplace esta función si desea colocar formatos un `COleDataSource` objeto antes o después de los formatos proporcionados por `CopyToClipboard`.  
  
##  <a name="getdatasource"></a>  COleServerItem::GetDataSource  
 Llame a esta función para obtener el [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto que se usa para almacenar los formatos de conversión que admite la aplicación de servidor.  
  
```  
COleDataSource* GetDataSource();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `COleDataSource` objeto que se usa para almacenar los formatos de conversión.  
  
### <a name="remarks"></a>Comentarios  
 Si desea que la aplicación de servidor para ofrecer datos en una variedad de formatos durante la transferencia de datos de operaciones, registrar estos formatos con la `COleDataSource` objeto devuelto por esta función. Por ejemplo, si desea proporcionar un **CF_TEXT** representación del elemento OLE para las operaciones de arrastrar y colocar o Portapapeles, debería registrar el formato con el `COleDataSource` esta función devuelve el objeto y, a continuación, reemplace el  **OnRenderXxxData** función de miembro para proporcionar los datos.  
  
##  <a name="getdocument"></a>  COleServerItem::GetDocument  
 Llame a esta función para obtener un puntero al documento que contiene el elemento.  
  
```  
COleServerDoc* GetDocument() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al documento que contiene el elemento; **NULL** si el elemento no forma parte de un documento.  
  
### <a name="remarks"></a>Comentarios  
 Esto permite el acceso al documento del servidor que se pasa como un argumento a la `COleServerItem` constructor.  
  
##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData  
 Llame a esta función para obtener el **CF_EMBEDSOURCE** datos de un elemento OLE.  
  
```  
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStgMedium`  
 Puntero a la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura que va a recibir el **CF_EMBEDSOURCE** datos para el elemento OLE.  
  
### <a name="remarks"></a>Comentarios  
 Este formato incluye los datos del elemento nativo. Se debe haber implementado el `Serialize` función de miembro para esta función para que funcione correctamente.  
  
 El resultado puede agregarse a un origen de datos mediante [:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Esta función se invoca automáticamente [COleServerItem::OnGetClipboardData](#ongetclipboarddata).  
  
 Para obtener más información, consulte [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) del SDK de Windows.  
  
##  <a name="getitemname"></a>  COleServerItem::GetItemName  
 Llame a esta función para obtener el nombre del elemento.  
  
```  
const CString& GetItemName() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Nombre del elemento.  
  
### <a name="remarks"></a>Comentarios  
 Se suele llamar a esta función solo para los elementos vinculados.  
  
##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData  
 Llame a esta función para obtener el `CF_LINKSOURCE` datos de un elemento OLE.  
  
```  
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpStgMedium`  
 Puntero a la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura que va a recibir el `CF_LINKSOURCE` datos para el elemento OLE.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Este formato incluye el CLSID que describe el tipo de elemento OLE y la información necesaria para buscar el documento que contiene el elemento OLE.  
  
 A continuación, el resultado puede agregarse a un origen de datos con [:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata). Esta función se invoca automáticamente [OnGetClipboardData](#ongetclipboarddata).  
  
 Para obtener más información, consulte [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) del SDK de Windows.  
  
##  <a name="getobjectdescriptordata"></a>  COleServerItem::GetObjectDescriptorData  
 Llame a esta función para obtener el **CF_OBJECTDESCRIPTOR** datos de un elemento OLE.  
  
```  
void GetObjectDescriptorData(
    LPPOINT lpOffset,  
    LPSIZE lpSize,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpOffset`  
 Haga clic en un desplazamiento del mouse en la esquina superior izquierda del elemento OLE. Puede ser **NULL**.  
  
 `lpSize`  
 Tamaño del elemento OLE. Puede ser **NULL**.  
  
 `lpStgMedium`  
 Puntero a la [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura que va a recibir el **CF_OBJECTDESCRIPTOR** datos para el elemento OLE.  
  
### <a name="remarks"></a>Comentarios  
 La información se copia en el **STGMEDIUM** estructura que señala `lpStgMedium`. Este formato incluye la información necesaria para el cuadro de diálogo Pegado especial.  
  
 Para obtener más información, consulte [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) del SDK de Windows.  
  
##  <a name="isconnected"></a>  COleServerItem::IsConnected  
 Llame a esta función para ver si está conectado el elemento OLE.  
  
```  
BOOL IsConnected() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento está conectado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Se considera un elemento OLE conectado si uno o varios contenedores tienen referencias al elemento. Está conectado a un elemento si su recuento de referencias es mayor que 0 o si es un elemento incrustado.  
  
##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem  
 Llame a esta función para ver si el elemento OLE es un elemento vinculado.  
  
```  
BOOL IsLinkedItem() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento es un elemento vinculado; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si el elemento es válido y no se devuelve en la lista del documento de los elementos incrustados, está enlazado un elemento. Un elemento vinculado podría o no esté conectado a un contenedor.  
  
 Es habitual usar la misma clase para elementos vinculados e incrustados. `IsLinkedItem` le permite hacer que los elementos vinculados se comportan de forma diferente a los elementos incrustados, aunque hay muchas veces el código común.  
  
##  <a name="m_sizeextent"></a>  COleServerItem::m_sizeExtent  
 Este miembro indica al servidor la cantidad del objeto está visible en el documento contenedor.  
  
```  
CSize m_sizeExtent;  
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de [OnSetExtent](#onsetextent) establece este miembro.  
  
##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged  
 Llame a esta función después de que se ha cambiado el elemento vinculado.  
  
```  
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```  
  
### <a name="parameters"></a>Parámetros  
 `nDrawAspect`  
 Un valor comprendido entre el `DVASPECT` enumeración que indica qué aspecto del elemento OLE ha cambiado. Este parámetro puede tener cualquiera de los siguientes valores:  
  
- `DVASPECT_CONTENT` Elemento se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.  
  
- `DVASPECT_THUMBNAIL` Elemento se representa en una representación en forma de "vista en miniatura", por lo que puede mostrarse en una herramienta de exploración.  
  
- `DVASPECT_ICON` Elemento se representa mediante un icono.  
  
- `DVASPECT_DOCPRINT` Elemento se representa como si se imprimiera utilizando el comando Imprimir en el menú archivo.  
  
### <a name="remarks"></a>Comentarios  
 Si un elemento contenedor está vinculado al documento con un vínculo automático, el elemento se actualiza para reflejar los cambios. En las aplicaciones de contenedor escritas mediante la biblioteca Microsoft Foundation Class, [COleClientItem](../../mfc/reference/coleclientitem-class.md#onchange) se llama en respuesta.  
  
##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb  
 Lo llama el marco de trabajo para ejecutar el verbo especificado.  
  
```  
virtual void OnDoVerb(LONG iVerb);
```  
  
### <a name="parameters"></a>Parámetros  
 `iVerb`  
 Especifica el verbo que se ejecute. Puede ser cualquiera de las siguientes acciones:  
  
|Valor|Significado|Símbolo|  
|-----------|-------------|------------|  
|0|verbo principal|`OLEIVERB_PRIMARY`|  
|1|Verbo secundario|(Ninguno)|  
|- 1|Elemento para mostrar para su edición|`OLEIVERB_SHOW`|  
|- 2|Editar elemento en una ventana independiente|`OLEIVERB_OPEN`|  
|- 3|Ocultar elementos|`OLEIVERB_HIDE`|  
  
 El valor-1 normalmente es un alias para otro verbo. Si no se admite la edición abierta, -2 tiene el mismo efecto que -1. Para los valores adicionales, consulte [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) del SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, esta función se invoca cuando el [COleClientItem::Activate](../../mfc/reference/coleclientitem-class.md#activate) función de miembro de los correspondientes `COleClientItem` se denomina objeto. La implementación predeterminada llama el [OnShow](#onshow) miembro funcionar si el verbo principal o `OLEIVERB_SHOW` se especifica, [OnOpen](#onopen) si el verbo secundario o `OLEIVERB_OPEN` se especifica y [OnHide](#onhide) si `OLEIVERB_HIDE` se especifica. La implementación predeterminada llama `OnShow` si `iVerb` no es uno de los verbos mencionados anteriormente.  
  
 Reemplace esta función si el verbo principal no muestra el elemento. Por ejemplo, si el elemento es una grabación de sonido y su verbo principal es reproducir, no tendría que mostrar la aplicación de servidor para reproducir el elemento.  
  
 Para obtener más información, consulte [DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) del SDK de Windows.  
  
##  <a name="ondraw"></a>  COleServerItem:: OnDraw  
 Lo llama el marco de trabajo para representar el elemento OLE en un metarchivo.  
  
```  
virtual BOOL OnDraw(
    CDC* pDC,  
    CSize& rSize) = 0;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Un puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto en el que se va a dibujar el elemento. El contexto de presentación se conecta automáticamente al contexto de presentación del atributo es posible llamar a funciones de atributo, aunque al hacerlo por lo que haría que el metarchivo específico del dispositivo.  
  
 `rSize`  
 Cambiar el tamaño, en **HIMETRIC** unidades, en el que se va a dibujar el metarchivo.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento se ha dibujado correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La representación del metarchivo del elemento OLE se utiliza para mostrar el elemento en la aplicación contenedora. Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, metarchivo utilizan el [dibujar](../../mfc/reference/coleclientitem-class.md#draw) función de miembro de los correspondientes [COleClientItem](../../mfc/reference/coleclientitem-class.md) objeto. No hay ninguna implementación predeterminada. Se debe reemplazar esta función para dibujar el elemento en el contexto de dispositivo especificado.  
  
##  <a name="ondrawex"></a>  COleServerItem::OnDrawEx  
 Lo llama el marco de trabajo para todos los dibujos.  
  
```  
virtual BOOL OnDrawEx(
    CDC* pDC,  
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDC`  
 Un puntero a la [CDC](../../mfc/reference/cdc-class.md) objeto en el que se va a dibujar el elemento. El controlador de dominio se conecta automáticamente el atributo de controlador de dominio es posible llamar a funciones de atributo, aunque al hacerlo por lo que haría que el metarchivo específico del dispositivo.  
  
 `nDrawAspect`  
 Un valor de la enumeración `DVASPECT`. Este parámetro puede tener cualquiera de los siguientes valores:  
  
- `DVASPECT_CONTENT` Elemento se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.  
  
- `DVASPECT_THUMBNAIL` Elemento se representa en una representación en forma de "vista en miniatura", por lo que puede mostrarse en una herramienta de exploración.  
  
- `DVASPECT_ICON` Elemento se representa mediante un icono.  
  
- `DVASPECT_DOCPRINT` Elemento se representa como si se imprimiera utilizando el comando Imprimir en el menú archivo.  
  
 `rSize`  
 Tamaño del elemento en **HIMETRIC** unidades.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el elemento se ha dibujado correctamente; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama `OnDraw` cuando `DVASPECT` es igual a `DVASPECT_CONTENT`; en caso contrario, se produce un error.  
  
 Reemplace esta función para proporcionar datos de la presentación para aspectos distintos de `DVASPECT_CONTENT`, como `DVASPECT_ICON` o `DVASPECT_THUMBNAIL`.  
  
##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData  
 Lo llama el marco para obtener un `COleDataSource` objeto que contiene todos los datos que se van a colocar en el Portapapeles mediante una llamada a la [CopyToClipboard](#copytoclipboard) función miembro.  
  
```  
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,  
    LPPOINT lpOffset,  
    LPSIZE lpSize);
```  
  
### <a name="parameters"></a>Parámetros  
 `bIncludeLink`  
 Establezca esta propiedad en **TRUE** si vincular datos deben copiarse en el Portapapeles. Establezca esta propiedad en **FALSE** si la aplicación de servidor no admite vínculos.  
  
 `lpOffset`  
 El desplazamiento del cursor del mouse desde el origen del objeto en píxeles.  
  
 `lpSize`  
 El tamaño del objeto en píxeles.  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [COleDataSource](../../mfc/reference/coledatasource-class.md) objeto que contiene los datos del Portapapeles.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función llama [GetClipboardData](#getclipboarddata).  
  
##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent  
 Lo llama el marco para recuperar el tamaño, en **HIMETRIC** unidades del elemento OLE.  
  
```  
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,  
    CSize& rSize);
```  
  
### <a name="parameters"></a>Parámetros  
 `nDrawAspect`  
 Especifica el aspecto del producto OLE cuyos límites se van a recuperar. Este parámetro puede tener cualquiera de los siguientes valores:  
  
- `DVASPECT_CONTENT` Elemento se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.  
  
- `DVASPECT_THUMBNAIL` Elemento se representa en una representación en forma de "vista en miniatura", por lo que puede mostrarse en una herramienta de exploración.  
  
- `DVASPECT_ICON` Elemento se representa mediante un icono.  
  
- `DVASPECT_DOCPRINT` Elemento se representa como si se imprimiera utilizando el comando Imprimir en el menú archivo.  
  
 `rSize`  
 Referencia a un `CSize` objeto que va a recibir el tamaño del elemento OLE.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, esta función se invoca cuando el [GetExtent](../../mfc/reference/coleclientitem-class.md#getextent) función de miembro de los correspondientes `COleClientItem` se denomina objeto. La implementación predeterminada no hace nada. Debe implementar, usted mismo. Reemplace esta función si desea realizar un procesamiento especial cuando controla una solicitud para el tamaño del elemento OLE.  
  
##  <a name="onhide"></a>  COleServerItem::OnHide  
 Lo llama el marco para ocultar el elemento OLE.  
  
```  
virtual void OnHide();
```  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas de forma predeterminada **COleServerDoc::OnShowDocument (FALSE)**. La función también notifica al contenedor que se ha ocultado el elemento OLE. Reemplace esta función si desea realizar un procesamiento especial cuando cuando se oculta un elemento OLE.  
  
##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData  
 Lo llama el marco para inicializar un elemento OLE mediante el contenido de `pDataObject`.  
  
```  
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,  
    BOOL bCreation);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDataObject`  
 Puntero a un objeto de datos OLE que contiene los datos en diferentes formatos para inicializar el elemento OLE.  
  
 `bCreation`  
 **TRUE** si la función se llama para inicializar un elemento OLE recién creando una aplicación de contenedor. **FALSE** si se llama a la función para reemplazar el contenido de un elemento OLE ya existente.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si `bCreation` es **TRUE**, esta función se invoca si un contenedor implementa Insertar nuevo objeto basándose en la selección actual. Los datos seleccionados se utilizan al crear el nuevo elemento OLE. Por ejemplo, al seleccionar un rango de celdas en un programa de hoja de cálculo y, a continuación, usa Insertar nuevo objeto para crear un gráfico según los valores en el intervalo seleccionado. La implementación predeterminada no hace nada. Reemplace esta función para elegir un formato aceptable de las proporcionadas por `pDataObject` e inicializar el elemento OLE basándose en los datos proporcionados. Avanzada reemplazable.  
  
 Para obtener más información, consulte [IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) en el SDK de Windows.  
  
##  <a name="onopen"></a>  COleServerItem::OnOpen  
 Lo llama el marco de trabajo para mostrar el elemento OLE en una instancia independiente de la aplicación de servidor, en lugar de en su lugar.  
  
```  
virtual void OnOpen();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada activa la primera ventana de marco mostrar el documento que contiene el elemento OLE; Si la aplicación es un servidor mínima, la implementación predeterminada muestra la ventana principal. La función también notifica al contenedor que se ha abierto el elemento OLE.  
  
 Reemplace esta función si desea realizar un procesamiento especial al abrir un elemento OLE. Esto es especialmente frecuente con los elementos vinculados en la que desea establecer la selección en el vínculo cuando se abre.  
  
 Para obtener más información, consulte [IOleClientSite::OnShowWindow](http://msdn.microsoft.com/library/windows/desktop/ms688658) en el SDK de Windows.  
  
##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems  
 Lo llama el marco de trabajo para determinar si los elementos vinculados en el documento del servidor actual no están actualizados.  
  
```  
virtual BOOL OnQueryUpdateItems();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el documento tiene elementos que necesitan actualizaciones; 0 si todos los elementos estén actualizados.  
  
### <a name="remarks"></a>Comentarios  
 Un elemento está anticuado si se cambió su documento de origen, pero el elemento vinculado no se ha actualizado para reflejar los cambios en el documento.  
  
##  <a name="onrenderdata"></a>  COleServerItem::OnRenderData  
 Lo llama el marco de trabajo para recuperar datos en el formato especificado.  
  
```  
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `lpStgMedium`  
 Apunta a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura en la que los datos se va a devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una establecidas anteriormente en el `COleDataSource` objeto mediante la [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) o [DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata) función de miembro para la representación aplazada. La implementación predeterminada de esta función llama [OnRenderFileData](#onrenderfiledata) o [OnRenderGlobalData](#onrenderglobaldata), respectivamente, si el medio de almacenamiento proporcionado es un archivo o la memoria. Si no se proporciona ninguno de estos formatos, la implementación predeterminada devuelve 0 y no hace nada.  
  
 Si `lpStgMedium` ->  *tymed* es **TYMED_NULL**, **STGMEDIUM** debe asignar y se rellena según lo especificado por *lpFormatEtc -> TYMED*. Si no **TYMED_NULL**, **STGMEDIUM** debe rellenarse en lugar de con los datos.  
  
 Avanzada reemplazable. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede que desee invalidar una de las otras versiones de esta función en su lugar. Si los datos son pequeños y un tamaño fijo, invalidar `OnRenderGlobalData`. Si los datos en un archivo, o es de tamaño variable, invalidar `OnRenderFileData`.  
  
 Para obtener más información, consulte [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431), [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), y [TYMED](http://msdn.microsoft.com/library/windows/desktop/ms691227) del SDK de Windows.  
  
##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData  
 Lo llama el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento es un archivo.  
  
```  
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,  
    CFile* pFile);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `pFile`  
 Apunta a un `CFile` objeto en el que se va a representar los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una establecidas anteriormente en el `COleDataSource` objeto mediante la [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función de miembro para la representación aplazada. La implementación predeterminada de esta función devuelve simplemente **FALSE**.  
  
 Avanzada reemplazable. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos en un archivo, o es de tamaño variable, invalidar [OnRenderFileData](#onrenderfiledata).  
  
 Para obtener más información, consulte [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) del SDK de Windows.  
  
##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData  
 Lo llama el marco de trabajo para recuperar datos en el formato especificado cuando el medio de almacenamiento especificado es una memoria global.  
  
```  
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,  
    HGLOBAL* phGlobal);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Apunta a la [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato en el que se solicita información.  
  
 `phGlobal`  
 Apunta a un identificador de memoria global en el que los datos son va a devolver. Si no se ha asignado ninguna memoria, este parámetro puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El formato especificado es una establecidas anteriormente en el `COleDataSource` objeto mediante la [DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata) función de miembro para la representación aplazada. La implementación predeterminada de esta función devuelve simplemente **FALSE**.  
  
 Si `phGlobal` es **NULL**, a continuación, un nuevo `HGLOBAL` debe asignar y se devuelve en `phGlobal`. En caso contrario, el `HGLOBAL` especificado por `phGlobal` debe rellenarse con los datos. La cantidad de datos se coloca en el `HGLOBAL` no debe superar el tamaño actual del bloque de memoria. Además, el bloque no se pueden reasignar a un tamaño mayor.  
  
 Avanzada reemplazable. Reemplace esta función para proporcionar los datos en el formato solicitado y medio. Dependiendo de los datos, puede que desee invalidar una de las otras versiones de esta función en su lugar. Si desea controlar varios medios de almacenamiento, reemplace [OnRenderData](#onrenderdata). Si los datos en un archivo, o es de tamaño variable, invalidar [OnRenderFileData](#onrenderfiledata).  
  
 Para obtener más información, consulte [IDataObject:: GetData](http://msdn.microsoft.com/library/windows/desktop/ms678431) y [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) del SDK de Windows.  
  
##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme  
 Lo llama el marco de trabajo para especificar una paleta de colores que se utilizará al editar el elemento OLE.  
  
```  
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpLogPalette`  
 Puntero a una ventana de [LOGPALETTE](http://msdn.microsoft.com/library/windows/desktop/dd145040) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si se usa la paleta de colores; en caso contrario es 0.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación contenedora se ha escrito utilizando la biblioteca Microsoft Foundation Class, esta función se invoca cuando el [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) función de los correspondientes `COleClientItem` se denomina objeto. La implementación predeterminada devuelve **FALSE**. Reemplace esta función si desea utilizar la paleta recomendada. La aplicación de servidor no tiene que utilizar la paleta sugerida.  
  
 Para obtener más información, consulte [IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) en el SDK de Windows.  
  
##  <a name="onsetdata"></a>  COleServerItem::OnSetData  
 Lo llama el marco de trabajo para reemplazar los datos del elemento OLE con los datos especificados.  
  
```  
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,  
    LPSTGMEDIUM lpStgMedium,  
    BOOL bRelease);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpFormatEtc`  
 Puntero a un [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177) estructura que especifica el formato de los datos.  
  
 `lpStgMedium`  
 Puntero a un [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812) estructura en la que residen los datos.  
  
 `bRelease`  
 Indica que tiene una propiedad del medio de almacenamiento después de completar la llamada de función. El llamador decide quién es responsable de liberar los recursos asignados en nombre del medio de almacenamiento. El llamador para ello, establezca `bRelease`. Si `bRelease` es distinto de cero, el elemento del servidor toma la propiedad, el medio que libera cuando termina de usarla. Cuando `bRelease` es 0, el llamador conserva la propiedad y el elemento del servidor sólo puede utilizar el medio de almacenamiento para la duración de la llamada.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 El elemento del servidor no tomar posesión de los datos hasta que obtuvo correctamente. Es decir, no tienen la propiedad si devuelve 0. Si el origen de datos toma posesión, libera el medio de almacenamiento mediante una llamada a la [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) función.  
  
 La implementación predeterminada no hace nada. Reemplace esta función para reemplazar los datos del elemento OLE con los datos especificados. Avanzada reemplazable.  
  
 Para obtener más información, consulte [STGMEDIUM](http://msdn.microsoft.com/library/windows/desktop/ms683812), [FORMATETC](http://msdn.microsoft.com/library/windows/desktop/ms682177), y [ReleaseStgMedium](http://msdn.microsoft.com/library/windows/desktop/ms693491) del SDK de Windows.  
  
##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent  
 Lo llama el marco de trabajo para indicar que el elemento OLE cuánto espacio hay disponible en el documento contenedor.  
  
```  
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,  
    const CSize& size);
```  
  
### <a name="parameters"></a>Parámetros  
 `nDrawAspect`  
 Especifica el aspecto del elemento OLE cuyos límites se especifican. Este parámetro puede tener cualquiera de los siguientes valores:  
  
- `DVASPECT_CONTENT` Elemento se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.  
  
- `DVASPECT_THUMBNAIL` Elemento se representa en una representación en forma de "vista en miniatura", por lo que puede mostrarse en una herramienta de exploración.  
  
- `DVASPECT_ICON` Elemento se representa mediante un icono.  
  
- `DVASPECT_DOCPRINT` Elemento se representa como si se imprimiera utilizando el comando Imprimir en el menú archivo.  
  
 `size`  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md) estructura que especifica el nuevo tamaño del elemento OLE.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Si la aplicación contenedora se escribió con la biblioteca Microsoft Foundation Class, esta función se invoca cuando el [SetExtent](../../mfc/reference/coleclientitem-class.md#setextent) función de miembro de los correspondientes `COleClientItem` se denomina objeto. La implementación predeterminada configura el [m_sizeExtent](#m_sizeextent) miembro al tamaño especificado si `nDrawAspect` es `DVASPECT_CONTENT`; en caso contrario, devuelve 0. Reemplace esta función para realizar un procesamiento especial cuando se cambia el tamaño del elemento.  
  
##  <a name="onshow"></a>  COleServerItem::OnShow  
 Lo llama el marco para indicar a la aplicación de servidor para mostrar el elemento OLE en contexto.  
  
```  
virtual void OnShow();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función normalmente se llama cuando el usuario de la aplicación contenedora crea un elemento o ejecuta un verbo, como editar, requiere que el elemento que se mostrará. La implementación predeterminada intenta realizar la activación en contexto. Si se produce un error, las llamadas a funciones el `OnOpen` función de miembro para mostrar el elemento OLE en una ventana independiente.  
  
 Reemplace esta función si desea realizar un procesamiento especial cuando se muestre un elemento OLE.  
  
##  <a name="onupdate"></a>  COleServerItem::OnUpdate  
 Llamado por el marco de trabajo cuando se ha modificado un elemento.  
  
```  
virtual void OnUpdate(
    COleServerItem* pSender,  
    LPARAM lHint,  
    CObject* pHint,  
    DVASPECT nDrawAspect);
```  
  
### <a name="parameters"></a>Parámetros  
 `pSender`  
 Puntero al elemento que se modificó el documento. Puede ser **NULL**.  
  
 `lHint`  
 Contiene información sobre la modificación.  
  
 `pHint`  
 Puntero a un objeto que almacena información sobre la modificación.  
  
 `nDrawAspect`  
 Un valor de la enumeración `DVASPECT`. Este parámetro puede tener uno de los siguientes valores:  
  
- `DVASPECT_CONTENT` Elemento se representa de manera que puede mostrarse como un objeto incrustado dentro de su contenedor.  
  
- `DVASPECT_THUMBNAIL` Elemento se representa en una representación en forma de "vista en miniatura", por lo que puede mostrarse en una herramienta de exploración.  
  
- `DVASPECT_ICON` Elemento se representa mediante un icono.  
  
- `DVASPECT_DOCPRINT` Elemento se representa como si se imprimiera utilizando el comando Imprimir en el menú archivo.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama [NotifyChanged](#notifychanged), independientemente de la sugerencia o remitente.  
  
##  <a name="onupdateitems"></a>  COleServerItem::OnUpdateItems  
 Lo llama el marco de trabajo para actualizar todos los elementos en el documento de servidor.  
  
```  
virtual void OnUpdateItems();
```  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada llama [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) para todos los `COleClientItem` objetos en el documento.  
  
##  <a name="setitemname"></a>  COleServerItem::SetItemName  
 Llame a esta función cuando se crea un elemento vinculado para establecer su nombre.  
  
```  
void SetItemName(LPCTSTR lpszItemName);
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszItemName`  
 Puntero para el nuevo nombre del elemento.  
  
### <a name="remarks"></a>Comentarios  
 El nombre debe ser único dentro del documento. Cuando se llama a una aplicación de servidor para editar un elemento vinculado, la aplicación utiliza este nombre para buscar el elemento. No es necesario llamar a esta función para los elementos incrustados.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo HIERSVR](../../visual-cpp-samples.md)   
 [Clase CDocItem](../../mfc/reference/cdocitem-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clase de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Clase COleServerDoc](../../mfc/reference/coleserverdoc-class.md)   
 [COleTemplateServer (clase)](../../mfc/reference/coletemplateserver-class.md)
