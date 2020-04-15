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
ms.openlocfilehash: ccd8ddc9f4981b3d9f7f4e1decdf6790cd05b98b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375489"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer (clase)

Implementa las interfaces OLE adicionales necesarias para crear un servidor normal de `COleDocument` en un servidor completo de DocObject: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`y `IPrint`.

## <a name="syntax"></a>Sintaxis

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Construye un objeto `CDocObjectServer`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Activa el servidor de objetos de documento, pero no lo muestra.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|Muestra la vista DocObject.|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Restaura el estado de la vista DocObject.|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Guarda el estado de la vista DocObject.|

## <a name="remarks"></a>Observaciones

`CDocObjectServer`se deriva `CCmdTarget` de y trabaja `COleServerDoc` estrechamente con para exponer las interfaces.

Un documento de servidor DocObject puede contener [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) objetos, que representan la interfaz de servidor para DocObject elementos.

Para personalizar el servidor DocObject, `CDocObjectServer` derive su propia clase e invalide sus funciones de configuración de vista, [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate)y [OnSaveViewState](#onsaveviewstate). Deberá proporcionar una nueva instancia de la clase en respuesta a las llamadas al marco de trabajo.

Para obtener más información sobre DocObjects, vea [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en la *referencia de MFC*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdocob.h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject

Llame a esta función para activar (pero no mostrar) el servidor de objetos de documento.

```
void ActivateDocObject();
```

### <a name="remarks"></a>Observaciones

`ActivateDocObject`llama `IOleDocumentSite`al `ActivateMe` método 's, pero no muestra la vista porque espera instrucciones específicas sobre cómo configurar y mostrar la vista, que se indican en la llamada a [CDocObjectServer::OnActivateView](#onactivateview).

`ActivateDocObject` Juntos, `OnActivateView` y activen y muestren la vista DocObject. La activación de DocObject difiere de otros tipos de activación EN contexto OLE. La activación de DocObject omite la visualización de bordes de sombreado in situ y adornos de objetos (como los identificadores de tamaño), ignora las funciones de extensión de objeto y dibuja barras de desplazamiento dentro del rectángulo de vista en lugar de dibujarlos fuera de ese rectángulo (como en la activación normal in situ).

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer

Construye e inicializa un objeto `CDocObjectServer`.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Parámetros

*pOwner*<br/>
Puntero al documento de sitio cliente que es el cliente para el servidor DocObject.

*pDocSite*<br/>
Un puntero `IOleDocumentSite` a la interfaz implementada por el contenedor.

### <a name="remarks"></a>Observaciones

Cuando un DocObject está activo, la `IOleDocumentSite`interfaz OLE del sitio cliente ( ) es lo que permite que el servidor DocObject se comunique con su cliente (el contenedor). Cuando se activa un servidor DocObject, primero comprueba `IOleDocumentSite` que el contenedor implementa la interfaz. Si es así, [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) se llama para ver si el contenedor admite DocObjects. De forma `GetDocObjectServer` predeterminada, devuelve NULL. Debe reemplazar `COleServerDoc::GetDocObjectServer` para construir `CDocObjectServer` un nuevo objeto o un objeto derivado `COleServerDoc` propio, `IOleDocumentSite` con punteros al contenedor y su interfaz como argumentos para el constructor.

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a>CDocObjectServer::OnActivateView

Llame a esta función para mostrar la vista DocObject.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un valor de error o advertencia. De forma predeterminada, devuelve NOERROR si se realiza correctamente; de lo contrario, E_FAIL.

### <a name="remarks"></a>Observaciones

Esta función crea una ventana de marco in situ, dibuja barras de desplazamiento dentro de la vista, configura los menús que el servidor comparte con su contenedor, agrega controles de marco, establece el objeto activo y, finalmente, muestra la ventana de marco en su lugar y establece el foco.

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState

Reemplace esta función para restaurar el estado de la vista DocObject.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
Objeto `CArchive` desde el que serializar el estado de vista.

### <a name="remarks"></a>Observaciones

Esta función se llama cuando la vista se muestra por primera vez después de su creación de instancias. `OnApplyViewState`indica a una vista que se reinicialice según los datos del `CArchive` objeto guardado anteriormente con [OnSaveViewState](#onsaveviewstate). La vista debe validar `CArchive` los datos del objeto porque el contenedor no intenta interpretar los datos de estado de vista de ninguna manera.

Puede usar `OnSaveViewState` para almacenar información persistente específica del estado de la vista. Si invalida `OnSaveViewState` para almacenar información, `OnApplyViewState` querrá invalidar para leer esa información y aplicarla a la vista cuando se haya activado recientemente.

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState

Reemplace esta función para guardar información de estado adicional sobre la vista DocObject.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Parámetros

*ar*<br/>
Objeto `CArchive` al que se serializa el estado de vista.

### <a name="remarks"></a>Observaciones

El estado puede incluir propiedades como el tipo de vista, el factor de zoom, el punto de inserción y selección, etc. Normalmente, el contenedor llama a esta función antes de desactivar la vista. El estado guardado se puede restaurar más adelante a través de [OnApplyViewState](#onapplyviewstate).

Puede usar `OnSaveViewState` para almacenar información persistente específica del estado de la vista. Si invalida `OnSaveViewState` para almacenar información, `OnApplyViewState` querrá invalidar para leer esa información y aplicarla a la vista cuando se haya activado recientemente.

## <a name="see-also"></a>Consulte también

[CCmdTarget (clase)](../../mfc/reference/ccmdtarget-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem (clase)](../../mfc/reference/cdocobjectserveritem-class.md)
