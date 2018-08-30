---
title: COleDocObjectItem (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
dev_langs:
- C++
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bebc146994e440d4dbfbd0bd3a5e29f597140d8d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216335"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem (clase)
Implementa la contención del documento activo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class COleDocObjectItem : public COleClientItem  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Construye un `COleDocObject` elemento.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[COleDocObjectItem:: DoDefaultPrinting](#dodefaultprinting)|Imprime el documento de la aplicación de contenedor con la configuración de la impresora predeterminada.|  
|[COleDocObjectItem::ExecCommand](#execcommand)|Ejecuta el comando especificado por el usuario.|  
|[COleDocObjectItem::GetActiveView](#getactiveview)|Recupera la vista activa del documento.|  
|[COleDocObjectItem::GetPageCount](#getpagecount)|Recupera el número de páginas del documento de la aplicación contenedora.|  
|[COleDocObjectItem:: OnPreparePrinting](#onprepareprinting)|Documento de la aplicación contenedora se prepara para la impresión.|  
|[COleDocObjectItem::OnPrint](#onprint)|Imprime el documento de la aplicación contenedora.|  
|[COleDocObjectItem::QueryCommand](#querycommand)|Consulta el estado de uno o más comandos generados por eventos de interfaz de usuario.|  
|[COleDocObjectItem::Release](#release)|Libera la conexión a un elemento vinculado de OLE y se cierra si estaba abierta. No se destruye el elemento de cliente.|  
  
## <a name="remarks"></a>Comentarios  
 En MFC, un documento activo se controla de forma similar a normales, in situ editable la inserción, con las siguientes diferencias:  
  
-   El `COleDocument`-clase derivada mantiene una lista de los elementos incrustados actualmente; sin embargo, estos elementos pueden ser `COleDocObjectItem`-elementos derivados.  
  
-   Cuando un documento activo está activo, ocupa toda el área cliente de la vista cuando está activo en contexto.  
  
-   Un contenedor de documentos activos tiene control total sobre la **ayuda** menú.  
  
-   El **ayuda** menú contiene elementos de menú para el contenedor de documentos activos y el servidor.  
  
 Dado que posee el contenedor de documentos activos el **ayuda** menú, el contenedor es responsable de servidor de reenvío **ayuda** mensajes de menú en el servidor. Esta integración se controla mediante `COleDocObjectItem`.  
  
 Para obtener más información sobre la combinación de menús y la activación del documento activo, consulte información general de [contención de documentos activos](../../mfc/active-document-containment.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CDocItem](../../mfc/reference/cdocitem-class.md)  
  
 [COleClientItem](../../mfc/reference/coleclientitem-class.md)  
  
 `COleDocObjectItem`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxole.h  
  
##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem  
 Llame a esta función miembro para inicializar el `COleDocObjectItem` objeto.  
  
```  
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *pContainerDoc*  
 Un puntero a la `COleDocument` objeto que actúa como el contenedor del documento activo. Este parámetro debe ser NULL para habilitar IMPLEMENT_SERIALIZE. Normalmente, elementos OLE se construyen con un puntero de documento no nulo.  
  
##  <a name="dodefaultprinting"></a>  COleDocObjectItem:: DoDefaultPrinting  
 Lo llama el marco de trabajo a un documento con la configuración predeterminada.  
  
```  
static HRESULT DoDefaultPrinting(
    CView* pCaller,  
    CPrintInfo* pInfo);
```  
  
### <a name="parameters"></a>Parámetros  
 *pCaller*  
 Un puntero a un [CView](../../mfc/reference/cview-class.md) objeto que envía el comando de impresión.  
  
 *pInfo*  
 Un puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se imprimen.  
  
##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand  
 Llame a esta función miembro para ejecutar el comando especificado por el usuario.  
  
```  
HRESULT ExecCommand(
    DWORD nCmdID,  
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,  
    const GUID* pguidCmdGroup = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *nCmdID*  
 El identificador de comando para ejecutar. Debe estar en el grupo identificado por *pguidCmdGroup*.  
  
 *nCmdExecOpt*  
 Especifica las opciones de ejecución del comando. De forma predeterminada, establecido para ejecutar el comando sin preguntar al usuario. Consulte [OLECMDEXECOPT](/windows/desktop/api/docobj/ne-docobj-olecmdexecopt) para obtener una lista de valores.  
  
 *pguidCmdGroup*  
 Identificador único del grupo de comandos. De forma predeterminada, NULL, lo que especifica el grupo estándar. El comando se pasa en *nCmdID* debe pertenecer al grupo.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se realiza correctamente; en caso contrario, devuelve uno de los siguientes códigos de error.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_UNEXPECTED|Se produjo un error inesperado.|  
|E_FAIL|Se produjo un error.|  
|E_NOTIMPL|Indica MFC sí debería intentar traducir y enviar el comando.|  
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* no es NULL, pero no especifica un grupo de comandos reconocido.|  
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* no se reconoce como un comando válido en el grupo de pGroup.|  
|OLECMDERR_DISABLED|El comando identificado por *nCmdID* está deshabilitado y no se puede ejecutar.|  
|OLECMDERR_NOHELP|Llamador pidió ayuda sobre el comando identificado por *nCmdID* pero no hay ayuda disponible.|  
|OLECMDERR_CANCELLED|El usuario canceló la ejecución.|  
  
### <a name="remarks"></a>Comentarios  
 El *pguidCmdGroup* y *nCmdID* parámetros juntos identifican de forma única el comando que se invoca. El *nCmdExecOpt* parámetro especifica la acción exacta que se realizará.  
  
##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView  
 Llame a esta función miembro para obtener un puntero a la `IOleDocumentView` interfaz de la vista activa actualmente.  
  
```  
LPOLEDOCUMENTVIEW GetActiveView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la [IOleDocumentView](/windows/desktop/api/docobj/nn-docobj-ioledocumentview) interfaz de la vista activa actualmente. Si no hay ninguna vista actual, devuelve NULL.  
  
### <a name="remarks"></a>Comentarios  
 El recuento de referencias en el valor devuelto `IOleDocumentView` no se incrementa el puntero antes de ser devuelto por esta función.  
  
##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount  
 Llame a esta función miembro para recuperar el número de páginas del documento.  
  
```  
BOOL GetPageCount(
    LPLONG pnFirstPage,  
    LPLONG pcPages);
```  
  
### <a name="parameters"></a>Parámetros  
 *pnFirstPage*  
 Un puntero al número de la primera página del documento. Puede ser NULL, lo que indica que el llamador no necesita este número.  
  
 *pcPages*  
 Un puntero al número total de páginas del documento. Puede ser NULL, lo que indica que el llamador no necesita este número.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="onprepareprinting"></a>  COleDocObjectItem:: OnPreparePrinting  
 Esta función miembro se llama el marco de trabajo para preparar un documento para su impresión.  
  
```  
static BOOL OnPreparePrinting(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pCaller*  
 Un puntero a un [CView](../../mfc/reference/cview-class.md) objeto que envía el comando de impresión.  
  
 *pInfo*  
 Un puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se imprimen.  
  
 *bPrintAll*  
 Especifica si se van a imprimir todo el documento.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
##  <a name="onprint"></a>  COleDocObjectItem::OnPrint  
 Esta función miembro se llama el marco de trabajo para imprimir un documento.  
  
```  
static void OnPrint(
    CView* pCaller,  
    CPrintInfo* pInfo,  
    BOOL bPrintAll = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *pCaller*  
 Un puntero a un objeto CView que envía el comando de impresión.  
  
 *pInfo*  
 Un puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se imprimen.  
  
 *bPrintAll*  
 Especifica si se van a imprimir todo el documento.  
  
##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand  
 Consulta el estado de uno o más comandos generados por eventos de interfaz de usuario.  
  
```  
HRESULT QueryCommand(
    ULONG nCmdID,  
    DWORD* pdwStatus,  
    OLECMDTEXT* pCmdText =NULL,  
    const GUID* pguidCmdGroup =NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *nCmdID*  
 identificador del comando que se consulta.  
  
 *pdwStatus*  
 Un puntero a los indicadores devueltos como resultado de la consulta. Para obtener una lista de valores posibles, vea [OLECMDF](/windows/desktop/api/docobj/ne-docobj-olecmdf).  
  
 *pCmdText*  
 Puntero a un [OLECMDTEXT](/windows/desktop/api/docobj/ns-docobj-_tagolecmdtext) estructura en la que se va a devolver información de nombre y el estado de un solo comando. Puede ser NULL para indicar que el llamador no necesita esta información.  
  
 *pguidCmdGroup*  
 Identificador único del grupo de comandos; puede ser NULL para especificar el grupo estándar.  
  
### <a name="return-value"></a>Valor devuelto  
 Para obtener una lista completa de los valores devueltos, vea [IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) en el SDK de Windows.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro emula la funcionalidad de la [IOleCommandTarget::QueryStatus](/windows/desktop/api/docobj/nf-docobj-iolecommandtarget-querystatus) método, como se describe en el SDK de Windows.  
  
##  <a name="release"></a>  COleDocObjectItem::Release  
 Libera la conexión a un elemento vinculado de OLE y se cierra si estaba abierta. No se destruye el elemento de cliente.  
  
```  
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```  
  
### <a name="parameters"></a>Parámetros  
 *dwCloseOption*  
 Marca que especifica en qué circunstancias se guarda el elemento OLE cuando vuelve al estado cargado. Para obtener una lista de valores posibles, vea [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).  
  
### <a name="remarks"></a>Comentarios  
 No se destruye el elemento de cliente.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de MFC MFCBIND](../../visual-cpp-samples.md)   
 [COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)   
 [CDocObjectServerItem (clase)](../../mfc/reference/cdocobjectserveritem-class.md)
