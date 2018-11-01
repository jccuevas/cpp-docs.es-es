---
title: CDocObjectServer (clase)
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: 704d3290df89c327bcf10b9afe7acb8621165863
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509531"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer (clase)

Implementa las interfaces OLE adicionales necesarias para crear un servidor normal de `COleDocument` en un servidor completo de DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`y `IPrint`.

## <a name="syntax"></a>Sintaxis

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Construye un objeto `CDocObjectServer`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Activa el servidor de objetos de documento, pero no se muestra.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|Muestra la vista DocObject.|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Restaura el estado de la vista DocObject.|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Guarda el estado de la vista DocObject.|

## <a name="remarks"></a>Comentarios

`CDocObjectServer` se deriva de `CCmdTarget` y trabaja en estrecha colaboración con `COleServerDoc` para exponer las interfaces.

Puede contener un documento de servidor DocObject [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) objetos que representan la interfaz de servidor a los elementos de DocObject.

Para personalizar el servidor de DocObject, derive su propia clase de `CDocObjectServer` e invalidar sus funciones de configuración de vista [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate), y [OnSaveViewState ](#onsaveviewstate). Deberá proporcionar una nueva instancia de la clase en respuesta a las llamadas de framework.

Para obtener más información sobre DocObjects, consulte [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en el *referencia de MFC*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdocob.h

##  <a name="activatedocobject"></a>  CDocObjectServer::ActivateDocObject

Llame a esta función para activar el servidor de objetos de documento (pero no se muestra).

```
void ActivateDocObject();
```

### <a name="remarks"></a>Comentarios

`ActivateDocObject` las llamadas `IOleDocumentSite`del `ActivateMe` método, pero no muestra la vista porque espera para obtener instrucciones específicas sobre cómo configurar y mostrar la vista, se proporcionan en la llamada a [CDocObjectServer::OnActivateView](#onactivateview).

Juntos, `ActivateDocObject` y `OnActivateView` activar y mostrar la vista DocObject. Activación de DocObject difiere de otros tipos de activación de OLE en contexto. Activación de DocObject omite la visualización de los bordes de sombreado en contexto y los elementos gráficos de objeto (por ejemplo, controladores de tamaño), omite las funciones de extensión de objeto y dibuja las barras de desplazamiento dentro del rectángulo de la vista en lugar de dibujo de fuera del rectángulo (como en normal activación en contexto).

##  <a name="cdocobjectserver"></a>  CDocObjectServer::CDocObjectServer

Construye e inicializa un objeto `CDocObjectServer`.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Parámetros

*pOwner*<br/>
Un puntero al documento de sitio de cliente que es el cliente para el servidor de DocObject.

*pDocSite*<br/>
Un puntero a la `IOleDocumentSite` interfaz implementada por el contenedor.

### <a name="remarks"></a>Comentarios

Cuando DocObject está activo, el cliente del sitio OLE (interfaz) ( `IOleDocumentSite`) es lo que permite que el servidor de DocObject para comunicarse con su cliente (el contenedor). Cuando un servidor de DocObject está activado, en primer lugar comprueba que el contenedor se implementa el `IOleDocumentSite` interfaz. Si es así, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) se llama para ver si el contenedor admite DocObjects. De forma predeterminada, `GetDocObjectServer` devuelve NULL. Debe invalidar `COleServerDoc::GetDocObjectServer` para crear un nuevo `CDocObjectServer` objeto o un objeto derivado de sus elección, con punteros a la `COleServerDoc` contenedor y su `IOleDocumentSite` interfaz como argumentos al constructor.

##  <a name="onactivateview"></a>  CDocObjectServer::OnActivateView

Llame a esta función para mostrar la vista DocObject.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor de advertencia o error. De forma predeterminada, devuelve NOERROR si se realiza correctamente; en caso contrario, E_FAIL.

### <a name="remarks"></a>Comentarios

Esta función crea una ventana de marco en contexto, dibuja las barras de desplazamiento dentro de la vista, configura los menús el servidor comparte con su contenedor, agrega controles de marco, Establece el objeto activo, a continuación, por último muestra la ventana de marco en contexto y establece el foco.

##  <a name="onapplyviewstate"></a>  CDocObjectServer::OnApplyViewState

Reemplace esta función para restaurar el estado de la vista DocObject.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*cuentas por cobrar*<br/>
Un `CArchive` objeto desde el que se va a serializar el estado de vista.

### <a name="remarks"></a>Comentarios

Esta función se llama cuando se muestra la vista por primera vez después de la creación de instancias. `OnApplyViewState` indica a una vista que se reinicialice según los datos en el `CArchive` guardado anteriormente con el objeto [OnSaveViewState](#onsaveviewstate). La vista debe validar los datos en el `CArchive` porque el contenedor no intenta interpretar los datos de estado de vista de cualquier forma de objeto.

Puede usar `OnSaveViewState` para almacenar información persistente específica al estado de la vista. Si invalida `OnSaveViewState` para almacenar información, desea invalidar `OnApplyViewState` leer esa información y se aplican a la vista cuando recién se activa.

##  <a name="onsaveviewstate"></a>  CDocObjectServer::OnSaveViewState

Reemplace esta función para guardar información de estado adicionales sobre la vista DocObject.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*cuentas por cobrar*<br/>
Un `CArchive` de objeto que se serializa el estado de vista.

### <a name="remarks"></a>Comentarios

El estado puede incluir propiedades como el tipo de vista, factor de zoom, inserción y punto de selección y así sucesivamente. Normalmente, el contenedor llama a esta función antes de desactivar la vista. El estado guardado más adelante puede restaurarse a través de [OnApplyViewState](#onapplyviewstate).

Puede usar `OnSaveViewState` para almacenar información persistente específica al estado de la vista. Si invalida `OnSaveViewState` para almacenar información, desea invalidar `OnApplyViewState` leer esa información y se aplican a la vista cuando recién se activa.

## <a name="see-also"></a>Vea también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem (clase)](../../mfc/reference/cdocobjectserveritem-class.md)
