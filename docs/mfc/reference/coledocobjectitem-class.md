---
title: Clase COleDocObjectItem
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
ms.openlocfilehash: a696226185dd99b9e277e74d92cbe15c95cc900a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375051"
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
|[COleDocObjectItem::DoDefaultPrinting](#dodefaultprinting)|Imprime el documento de la aplicación contenedora utilizando la configuración predeterminada de la impresora.|
|[COleDocObjectItem::ExecCommand](#execcommand)|Ejecuta el comando especificado por el usuario.|
|[COleDocObjectItem::GetActiveView](#getactiveview)|Recupera la vista activa del documento.|
|[COleDocObjectItem::GetPageCount](#getpagecount)|Recupera el número de páginas del documento de la aplicación contenedora.|
|[COleDocObjectItem::OnPreparePrinting](#onprepareprinting)|Prepara el documento de la aplicación contenedora para imprimir.|
|[COleDocObjectItem::OnPrint](#onprint)|Imprime el documento de la aplicación contenedora.|
|[COleDocObjectItem::QueryCommand](#querycommand)|Consulta el estado de uno o más comandos generados por eventos de interfaz de usuario.|
|[COleDocObjectItem::Release](#release)|Libera la conexión a un elemento vinculado OLE y la cierra si estaba abierta. No destruye el elemento de cliente.|

## <a name="remarks"></a>Observaciones

En MFC, un documento activo se controla de forma similar a una incrustación editable en el lugar normal, con las siguientes diferencias:

- La `COleDocument`clase -derived todavía mantiene una lista de los elementos incrustados actualmente; sin embargo, `COleDocObjectItem`estos elementos pueden ser elementos derivados.

- Cuando un documento activo está activo, ocupa todo el área de cliente de la vista cuando está activo en el lugar.

- Un contenedor de documentos activos tiene el control total del menú **Ayuda.**

- El menú **Ayuda** contiene elementos de menú para el contenedor de documentos activos y el servidor.

Dado que el contenedor de documentos activos es propietario del menú **Ayuda,** el contenedor es responsable de reenviar los mensajes de menú de **Ayuda** del servidor al servidor. Esta integración es `COleDocObjectItem`manejada por .

Para obtener más información sobre la combinación de menús y la activación de documentos activos, consulte Información general sobre la contención de [documentos activos](../../mfc/active-document-containment.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxole.h

## <a name="coledocobjectitemcoledocobjectitem"></a><a name="coledocobjectitem"></a>COleDocObjectItem::COleDocObjectItem

Llame a esta función miembro para inicializar el `COleDocObjectItem` objeto.

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>Parámetros

*pContainerDoc*<br/>
Puntero al `COleDocument` objeto que actúa como contenedor de documentos activo. Este parámetro debe ser NULL para habilitar IMPLEMENT_SERIALIZE. Normalmente, los elementos OLE se construyen con un puntero de documento no NULL.

## <a name="coledocobjectitemdodefaultprinting"></a><a name="dodefaultprinting"></a>COleDocObjectItem::DoDefaultPrinting

Llamado por el marco de trabajo a un documento mediante la configuración predeterminada.

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>Parámetros

*pCaller*<br/>
Puntero a un objeto [CView](../../mfc/reference/cview-class.md) que envía el comando print.

*pInfo*<br/>
Puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se va a imprimir.

## <a name="coledocobjectitemexeccommand"></a><a name="execcommand"></a>COleDocObjectItem::ExecCommand

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
Especifica las opciones de ejecución de comandos. De forma predeterminada, se establece para ejecutar el comando sin preguntar al usuario. Consulte [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) para obtener una lista de valores.

*pguidCmdGroup*<br/>
Identificador único del grupo de comandos. De forma predeterminada, NULL, que especifica el grupo estándar. El comando pasado en *nCmdID* debe pertenecer al grupo.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente; de lo contrario, devuelve uno de los siguientes códigos de error.

|Value|Descripción|
|-----------|-----------------|
|E_UNEXPECTED|Se ha producido un error inesperado.|
|E_FAIL|Se ha producido un error.|
|E_NOTIMPL|Indica que MFC debe intentar traducir y distribuir el comando.|
|OLECMDERR_E_UNKNOWNGROUP|*pguidCmdGroup* no es NULL, pero no especifica un grupo de comandos reconocido.|
|OLECMDERR_E_NOTSUPPORTED|*nCmdID* no se reconoce como un comando válido en el grupo pGroup.|
|OLECMDERR_DISABLED|El comando identificado por *nCmdID* está deshabilitado y no se puede ejecutar.|
|OLECMDERR_NOHELP|El autor de la llamada pidió ayuda en el comando identificado por *nCmdID,* pero no hay ninguna ayuda disponible.|
|OLECMDERR_CANCELLED|El usuario canceló la ejecución.|

### <a name="remarks"></a>Observaciones

Los parámetros *pguidCmdGroup* y *nCmdID* identifican conjuntamente el comando que se va a invocar. El *nCmdExecOpt* parámetro especifica la acción exacta a realizar.

## <a name="coledocobjectitemgetactiveview"></a><a name="getactiveview"></a>COleDocObjectItem::GetActiveView

Llame a esta función miembro `IOleDocumentView` para obtener un puntero a la interfaz de la vista activa actualmente.

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la [IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview) interfaz de la vista activa actualmente. Si no hay ninguna vista actual, devuelve NULL.

### <a name="remarks"></a>Observaciones

El recuento de `IOleDocumentView` referencias en el puntero devuelto no se incrementa antes de que esta función lo devuelva.

## <a name="coledocobjectitemgetpagecount"></a><a name="getpagecount"></a>COleDocObjectItem::GetPageCount

Llame a esta función miembro para recuperar el número de páginas en el documento.

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>Parámetros

*pnFirstPage*<br/>
Un puntero al número de la primera página del documento. Puede ser NULL, lo que indica que el autor de la llamada no necesita este número.

*pcPages*<br/>
Un puntero al número total de páginas del documento. Puede ser NULL, lo que indica que el autor de la llamada no necesita este número.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="coledocobjectitemonprepareprinting"></a><a name="onprepareprinting"></a>COleDocObjectItem::OnPreparePrinting

El marco de trabajo llama a esta función miembro para preparar un documento para la impresión.

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pCaller*<br/>
Puntero a un objeto [CView](../../mfc/reference/cview-class.md) que envía el comando print.

*pInfo*<br/>
Puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se va a imprimir.

*bPrintAll*<br/>
Especifica si se va a imprimir todo el documento.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="coledocobjectitemonprint"></a><a name="onprint"></a>COleDocObjectItem::OnPrint

El marco de trabajo llama a esta función miembro para imprimir un documento.

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>Parámetros

*pCaller*<br/>
Puntero a un objeto CView que envía el comando print.

*pInfo*<br/>
Puntero a un [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) objeto que describe el trabajo que se va a imprimir.

*bPrintAll*<br/>
Especifica si se va a imprimir todo el documento.

## <a name="coledocobjectitemquerycommand"></a><a name="querycommand"></a>COleDocObjectItem::QueryCommand

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
identificador del comando que se está consultando.

*pdwStatus*<br/>
Puntero a las marcas devueltas como resultado de la consulta. Para obtener una lista de valores posibles, vea [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf).

*pCmdText*<br/>
Puntero a una estructura [OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext) en la que se va a devolver información de nombre y estado para un único comando. Puede ser NULL para indicar que el autor de la llamada no necesita esta información.

*pguidCmdGroup*<br/>
Identificador único del grupo de comandos; puede ser NULL para especificar el grupo estándar.

### <a name="return-value"></a>Valor devuelto

Para obtener una lista completa de los valores devueltos, vea [IOleCommandTarget::QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Esta función miembro emula la funcionalidad de la [IOleCommandTarget::QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) método, como se describe en el Windows SDK.

## <a name="coledocobjectitemrelease"></a><a name="release"></a>COleDocObjectItem::Release

Libera la conexión a un elemento vinculado OLE y la cierra si estaba abierta. No destruye el elemento de cliente.

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>Parámetros

*dwCloseOption*<br/>
Marcar especificando en qué circunstancias se guarda el elemento OLE cuando vuelve al estado cargado. Para obtener una lista de valores posibles, vea [COleClientItem::Close](../../mfc/reference/coleclientitem-class.md#close).

### <a name="remarks"></a>Observaciones

No destruye el elemento de cliente.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[Clase COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem (clase)](../../mfc/reference/cdocobjectserveritem-class.md)
