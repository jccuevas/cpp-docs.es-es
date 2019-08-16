---
title: COleDocObjectItem (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: c6e00bf42cf20b46c949c218efe1820cc7ce0f9b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504011"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem (clase)

Implementa la contención del documento activo.

## <a name="syntax"></a>Sintaxis

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDocObjectItem::COleDocObjectItem](#coledocobjectitem)|Construye un `COleDocObject` elemento.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Imprime el documento de la aplicación contenedora con la configuración de impresora predeterminada.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Ejecuta el comando especificado por el usuario.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Recupera la vista activa del documento.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Recupera el número de páginas del documento de la aplicación contenedora.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Prepara el documento de la aplicación contenedor para la impresión.|
|[COleDocObjectItem::OnPrint](#onprint)|Imprime el documento de la aplicación contenedora.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Consulta el estado de uno o más comandos generados por eventos de interfaz de usuario.|
|[COleDocObjectItem::Release](#release)|Libera la conexión a un elemento vinculado OLE y lo cierra si estaba abierto. No destruye el elemento de cliente.|

## <a name="remarks"></a>Comentarios

En MFC, un documento activo se trata de forma similar a una incrustación editable en contexto normal, con las siguientes diferencias:

- La `COleDocument`clase derivada de mantiene todavía una lista de los elementos incrustados actualmente; sin embargo, estos elementos `COleDocObjectItem`pueden ser elementos derivados de.

- Cuando un documento activo está activo, ocupa todo el área cliente de la vista cuando está activo en contexto.

- Un contenedor de documentos activo tiene control total sobre el menú **ayuda** .

- El menú **ayuda** contiene los elementos de menú para el contenedor y el servidor de documentos activos.

Dado que el contenedor del documento activo posee el menú **ayuda** , el contenedor es responsable de reenviar los mensajes del menú **ayuda** del servidor al servidor. Controla esta integración `COleDocObjectItem`.

Para obtener más información sobre la combinación de menús y la activación de documentos activos, consulte información general de la contención de [documentos activos](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole. h

##  <a name="coledocobjectitem"></a>  COleDocObjectItem::COleDocObjectItem

Llame a esta función miembro para inicializar el `COleDocObjectItem` objeto.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parámetros

*pContainerDoc*<br/>
Puntero al `COleDocument` objeto que actúa como contenedor del documento activo. Este parámetro debe ser NULL para habilitar IMPLEMENT_SERIALIZE. Normalmente, los elementos OLE se construyen con un puntero de documento que no es NULL.

##  <a name="dodefaultprinting"></a>  COleDocObjectItem::DoDefaultPrinting

Lo llama el marco de trabajo a un documento con la configuración predeterminada.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pCaller*<br/>
Un puntero a un objeto [CView](../../mfc/reference/cview-class.md) que está enviando el comando Print.

*pInfo*<br/>
Un puntero a un objeto [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo que se va a imprimir.

##  <a name="execcommand"></a>  COleDocObjectItem::ExecCommand

Llame a esta función miembro para ejecutar el comando especificado por el usuario.

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>Parámetros

*nCmdID*<br/>
Identificador del comando que se va a ejecutar. Debe estar en el grupo identificado por *pguidCmdGroup*.

*nCmdExecOpt*<br/>
Especifica las opciones de ejecución de comandos. De forma predeterminada, establezca para ejecutar el comando sin preguntar al usuario. Consulte [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) para obtener una lista de valores.

*pguidCmdGroup*<br/>
Identificador único del grupo de comandos. De forma predeterminada, es NULL, que especifica el grupo estándar. El comando que se pasa en *nCmdID* debe pertenecer al grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente; de lo contrario, devuelve uno de los siguientes códigos de error.

|Value|DESCRIPCIÓN|
|-----------|-----------------|
|E_UNEXPECTED|Error inesperado.|
|E_FAIL|Se produjo un error.|
|E_NOTIMPL|Indica que MFC debe intentar traducir y distribuir el comando.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* no es null, pero no especifica un grupo de comandos reconocido.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* no se reconoce como un comando válido en el grupo pGroup.|
|OLECMDERR_DISABLED|El comando identificado por *nCmdID* está deshabilitado y no se puede ejecutar.|
|OLECMDERR_NOHELP|El autor de la llamada solicitó ayuda sobre el comando identificado por *nCmdID* , pero no hay ayuda disponible.|
|OLECMDERR_CANCELLED|El usuario canceló la ejecución.|

### <a name="remarks"></a>Comentarios

Los parámetros *pguidCmdGroup* y *nCmdID* juntos identifican de forma única el comando que se va a invocar. El parámetro *nCmdExecOpt* especifica la acción exacta que se debe llevar a cabo.

##  <a name="getactiveview"></a>  COleDocObjectItem::GetActiveView

Llame a esta función miembro para obtener un puntero a `IOleDocumentView` la interfaz de la vista activa actualmente.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) de la vista activa actualmente. Si no hay ninguna vista actual, devuelve NULL.

### <a name="remarks"></a>Comentarios

El recuento de referencias del `IOleDocumentView` puntero devuelto no se incrementa antes de que esta función lo devuelva.

##  <a name="getpagecount"></a>  COleDocObjectItem::GetPageCount

Llame a esta función miembro para recuperar el número de páginas del documento.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parámetros

*pnFirstPage*<br/>
Puntero al número de la primera página del documento. Puede ser NULL, lo que indica que el autor de la llamada no necesita este número.

*pcPages*<br/>
Puntero al número total de páginas del documento. Puede ser NULL, lo que indica que el autor de la llamada no necesita este número.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="onprepareprinting"></a>  COleDocObjectItem::OnPreparePrinting

El marco de trabajo llama a esta función miembro para preparar un documento para la impresión.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pCaller*<br/>
Un puntero a un objeto [CView](../../mfc/reference/cview-class.md) que está enviando el comando Print.

*pInfo*<br/>
Un puntero a un objeto [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo que se va a imprimir.

*bPrintAll*<br/>
Especifica si se va a imprimir todo el documento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="onprint"></a>  COleDocObjectItem::OnPrint

El marco de trabajo llama a esta función miembro para imprimir un documento.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pCaller*<br/>
Un puntero a un objeto CView que está enviando el comando Print.

*pInfo*<br/>
Un puntero a un objeto [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) que describe el trabajo que se va a imprimir.

*bPrintAll*<br/>
Especifica si se va a imprimir todo el documento.

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

*nCmdID*<br/>
identificador del comando que se va a consultar.

*pdwStatus*<br/>
Puntero a las marcas devueltas como resultado de la consulta. Para obtener una lista de los valores posibles, vea [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Puntero a una estructura [OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext) en la que se va a devolver información de nombre y estado para un solo comando. Puede ser NULL para indicar que el llamador no necesita esta información.

*pguidCmdGroup*<br/>
Identificador único del grupo de comandos; puede ser NULL para especificar el grupo estándar.

### <a name="return-value"></a>Valor devuelto

Para obtener una lista completa de los valores devueltos, consulte [IOLECommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Esta función miembro emula la funcionalidad del método [IOLECommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) , como se describe en el Windows SDK.

##  <a name="release"></a>  COleDocObjectItem::Release

Libera la conexión a un elemento vinculado OLE y lo cierra si estaba abierto. No destruye el elemento de cliente.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parámetros

*dwCloseOption*<br/>
Marca que especifica en qué circunstancias se guarda el elemento OLE cuando vuelve al estado de carga. Para obtener una lista de los valores posibles, vea [COleClientItem:: Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Comentarios

No destruye el elemento de cliente.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem (clase)](../../mfc/reference/cdocobjectserveritem-class.md)
