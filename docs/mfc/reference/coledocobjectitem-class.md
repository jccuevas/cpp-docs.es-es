---
title: Clase COleDocObjectItem | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleDocObjectItem
dev_langs:
- C++
helpviewer_keywords:
- COleDocObjectItem class
- document object containment
- containment
- containment, doc object
- doc object containment
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
caps.latest.revision: 23
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
ms.openlocfilehash: 0815454fa4b194e97a2d16a621cfc25da61d5fd0
ms.lasthandoff: 02/24/2017

---
# <a name="coledocobjectitem-class"></a>Clase COleDocObjectItem
Implementa la contención del documento activo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Construye un `COleDocObject` elemento.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleDocObjectItem:: DoDefaultPrinting](#dodefaultprinting)|Imprime el documento de la aplicación contenedora con la configuración de la impresora predeterminada.|  
|[COleDocObjectItem::ExecCommand](#execcommand)|Ejecuta el comando especificado por el usuario.|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|Recupera la vista activa del documento.|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|Recupera el número de páginas de documento de la aplicación contenedora.|  
|[COleDocObjectItem:: OnPreparePrinting](#onprepareprinting)|Documento de la aplicación contenedora se prepara para la impresión.|  
|[COleDocObjectItem::OnPrint](#onprint)|Imprime el documento de la aplicación contenedora.|  
|[COleDocObjectItem::QueryCommand](#querycommand)|Consulta el estado de uno o más comandos generados por eventos de interfaz de usuario.|  
|[COleDocObjectItem::Release](#release)|Libera la conexión a un elemento vinculado de OLE y se cierra si estaba abierto. Destruir el elemento de cliente.|  
  
## <a name="remarks"></a>Comentarios  
 En MFC, un documento activo se controla de forma similar a la una normal, en el lugar editable incrustación, con las siguientes diferencias:  
  
-   El `COleDocument`-clase derivada mantiene una lista de los elementos incrustados actualmente; sin embargo, estos elementos pueden ser `COleDocObjectItem`-elementos derivados.  
  
-   Cuando un documento activo está activo, ocupa toda el área cliente de la vista cuando está activo en contexto.  
  
-   Un contenedor de documentos activos tenga control total sobre la **ayuda** menú.  
  
-   El **ayuda** menú contiene elementos de menú para el contenedor de documentos activos y el servidor.  
  
 Puesto que el contenedor de documentos activos posee el **ayuda** menú, el contenedor es responsable del servidor de reenvío **ayuda** mensajes de menú en el servidor. Esta integración se controla mediante `COleDocObjectItem`.  
  
 Para obtener más información sobre la combinación de menús y la activación del documento activo, consulte información general de [contención de documentos activos](../../mfc/active-document-containment.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="a-namecoledocobjectitema--coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem  
 Llame a esta función miembro para inicializar la `COleDocObjectItem` objeto.  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `pContainerDoc`  
 Un puntero a la `COleDocument` objeto que actúa como contenedor de documentos activos. Este parámetro debe ser **NULL** para habilitar **IMPLEMENT_SERIALIZE**. Normalmente los elementos OLE se construyen con un no **NULL** puntero al documento.  
  
##  <a name="a-namedodefaultprintinga--coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObjectItem:: DoDefaultPrinting  
 Llamado por el marco de trabajo a un documento usando la configuración predeterminada.  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCaller`  
 Un puntero a un [CView](../../mfc/reference/cview-class.md) objeto que envía el comando de impresión.  
  
 `pInfo`  
 Un puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se va a imprimir.  
  
##  <a name="a-nameexeccommanda--coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObjectItem::ExecCommand  
 Llame a esta función miembro para ejecutar el comando especificado por el usuario.  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCmdID`  
 El identificador de comando para ejecutar. Debe estar en el grupo identificado por `pguidCmdGroup`.  
  
 `nCmdExecOpt`  
 Especifica las opciones de ejecución del comando. De forma predeterminada, establecido para ejecutar el comando sin preguntar al usuario. Consulte [OLECMDEXECOPT](http://msdn.microsoft.com/library/windows/desktop/ms683930) para obtener una lista de valores.  
  
 `pguidCmdGroup`  
 Identificador único del grupo de comandos. De forma predeterminada, **NULL**, que especifica el grupo estándar. El comando se pasa en `nCmdID` debe pertenecer al grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente; en caso contrario, devuelve uno de los siguientes códigos de error.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|**E_UNEXPECTED**|Se produjo un error inesperado.|  
|**E_FAIL**|Se produjo un error.|  
|**E_NOTIMPL**|Indica MFC sí debería intentar traducir y enviar el comando.|  
|**OLECMDERR_E_UNKNOWNGROUP**|`pguidCmdGroup`no es **NULL** pero no especifica un grupo de comandos reconocida.|  
|**OLECMDERR_E_NOTSUPPORTED**|`nCmdID`no se reconoce como un comando válido en el pGroup de grupo.|  
|**OLECMDERR_DISABLED**|El comando identificado por `nCmdID` está deshabilitado y no se puede ejecutar.|  
|**OLECMDERR_NOHELP**|Llamador más frecuentes para obtener ayuda sobre el comando identificado por `nCmdID` pero no hay ayuda disponible.|  
|**OLECMDERR_CANCELLED**|El usuario canceló la ejecución.|  
  
### <a name="remarks"></a>Comentarios  
 El `pguidCmdGroup` y `nCmdID` parámetros juntos identificar el comando que se invoca. El `nCmdExecOpt` parámetro especifica la acción exacta a realizar.  
  
##  <a name="a-namegetactiveviewa--coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDocObjectItem::GetActiveView  
 Llame a esta función miembro para obtener un puntero a la `IOleDocumentView` la interfaz de la vista activa.  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [IOleDocumentView](http://msdn.microsoft.com/library/windows/desktop/ms678455) interfaz de la vista activa. Si no hay ninguna vista actual, devuelve **NULL**.  
  
### <a name="remarks"></a>Comentarios  
 El recuento de referencias en el valor devuelto `IOleDocumentView` no se incrementa el puntero antes de ser devuelto por esta función.  
  
##  <a name="a-namegetpagecounta--coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDocObjectItem::GetPageCount  
 Llame a esta función miembro para recuperar el número de páginas del documento.  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>Parámetros  
 *pnFirstPage*  
 Puntero al número de la página del documento primera. Puede ser **NULL**, lo que indica que el llamador no necesita este número.  
  
 *pcPages*  
 Puntero al número total de páginas del documento. Puede ser **NULL**, lo que indica que el llamador no necesita este número.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-nameonprepareprintinga--coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObjectItem:: OnPreparePrinting  
 Esta función miembro se llama el marco de trabajo para preparar un documento para su impresión.  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCaller`  
 Un puntero a un [CView](../../mfc/reference/cview-class.md) objeto que envía el comando de impresión.  
  
 `pInfo`  
 Un puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se va a imprimir.  
  
 `bPrintAll`  
 Especifica si se imprimirá todo el documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="a-nameonprinta--coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObjectItem::OnPrint  
 Esta función miembro se llama el marco de trabajo para imprimir un documento.  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `pCaller`  
 Un puntero a un objeto de CView que envía el comando de impresión.  
  
 `pInfo`  
 Un puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se va a imprimir.  
  
 `bPrintAll`  
 Especifica si se imprimirá todo el documento.  
  
##  <a name="a-namequerycommanda--coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDocObjectItem::QueryCommand  
 Consulta el estado de uno o más comandos generados por eventos de interfaz de usuario.  
  
```  
HRESULT QueryCommand(
    ULONG nCmdID,  
    DWORD* pdwStatus,  
    OLECMDTEXT* pCmdText =NULL,  
    const GUID* pguidCmdGroup =NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `nCmdID`  
 identificador del comando que se va a consultar.  
  
 `pdwStatus`  
 Puntero a los indicadores devueltos como resultado de la consulta. Para obtener una lista de valores posibles, consulte [OLECMDF](http://msdn.microsoft.com/library/windows/desktop/ms695237).  
  
 `pCmdText`  
 Puntero a un [OLECMDTEXT](http://msdn.microsoft.com/library/windows/desktop/ms693314) estructura en la que se va a devolver información de nombre y el estado de un solo comando. Puede ser **NULL** para indicar que el llamador no necesita esta información.  
  
 `pguidCmdGroup`  
 Identificador único del grupo de comandos; puede ser **NULL** para especificar el grupo estándar.  
  
### <a name="return-value"></a>Valor devuelto  
 Para obtener una lista completa de los valores devueltos, consulte [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [IOleCommandTarget::QueryStatus](http://msdn.microsoft.com/library/windows/desktop/ms688491) método, como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namereleasea--coledocobjectitemrelease"></a><a name="release"></a>COleDocObjectItem::Release  
 Libera la conexión a un elemento vinculado de OLE y se cierra si estaba abierto. Destruir el elemento de cliente.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwCloseOption`  
 Marca que especifica en qué circunstancias se guarda el elemento OLE cuando se devuelve al estado cargado. Para obtener una lista de valores posibles, consulte [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).  
  
### <a name="remarks"></a>Comentarios  
 Destruir el elemento de cliente.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC MFCBIND](../../visual-cpp-samples.md)   
 [Clase de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [Clase de COleClientItem](../../mfc/reference/coleclientitem-class.md)   
 [Clase CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)

