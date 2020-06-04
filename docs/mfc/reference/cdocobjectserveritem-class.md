---
title: CDocObjectServerItem (clase)
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 1f0f5cf93aab35a17f7174b2beee0d1398564a3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375523"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem (clase)

Implementa verbos de servidor OLE específicamente para servidores de DocObject.

## <a name="syntax"></a>Sintaxis

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Construye un objeto `CDocObjectServerItem`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Recupera un puntero al documento que contiene el elemento.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Se llama para ejecutar un verbo.|
|[CDocObjectServerItem::OnHide](#onhide)|Produce una excepción si el marco de trabajo intenta ocultar un DocObject elemento.|
|[CDocObjectServerItem::OnShow](#onshow)|Llamado por el marco de trabajo para activar el elemento DocObject in situ. Si el elemento no es un DocObject, llame a [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Observaciones

`CDocObjectServerItem`define las funciones miembro reemplazables: [OnHide](#onhide), [OnDoVerb](#ondoverb)y [OnShow](#onshow).

Para `CDocObjectServerItem`usar , asegúrese de que la `COleServerDoc`invalidación [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) de la clase derivada devuelve un nuevo `CDocObjectServerItem` objeto. Si necesita cambiar cualquier funcionalidad del elemento, puede crear una `CDocObjectServerItem`nueva instancia de su propia clase derivada.

Para obtener más información sobre DocObjects, vea [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en la *referencia MFC*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdocob.h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem

Construye un objeto `CDocObjectServerItem`.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*pServerDoc*<br/>
Puntero al documento que contendrá el nuevo elemento DocObject.

*bAutoDelete*<br/>
Indica si el objeto se puede eliminar cuando se libera un vínculo a él. Establezca el argumento en `CDocObjectServerItem` FALSE si el objeto es una parte integral de los datos del documento. Establézcalo en TRUE si el objeto es una estructura secundaria que se usa para identificar un intervalo en los datos del documento que se pueden eliminar por el marco de trabajo.

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument

Recupera un puntero al documento que contiene el elemento.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento que contiene el elemento; NULL si el elemento no forma parte de un documento.

### <a name="remarks"></a>Observaciones

Esto permite el acceso al documento de servidor que pasó como argumento al constructor [CDocObjectServerItem.](#cdocobjectserveritem)

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a>CDocObjectServerItem::OnDoVerb

Llamado por el marco de trabajo para ejecutar el verbo especificado.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Especifica el verbo que se va a ejecutar. Para ver los valores posibles, vea [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

### <a name="remarks"></a>Observaciones

La implementación predeterminada llama a la [OnShow](#onshow) función miembro si el elemento es un DocObject y se especifica el OLEIVERB_INPLACEACTIVATE o OLEIVERB_SHOW. Si el elemento no es un DocObject o se especifica un verbo diferente, la implementación predeterminada llama [a COleServerItem::OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide

Llamado por el marco de trabajo para ocultar el elemento.

```
virtual void OnHide();
```

### <a name="remarks"></a>Observaciones

La implementación predeterminada produce una excepción si el elemento es un DocObject. No se puede ocultar un elemento DocObject activo porque toma toda la vista. Debe desactivar el elemento DocObject para que desaparezca. Si el elemento no es un DocObject, la implementación predeterminada llama [a COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide).

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow

Llamado por el marco de trabajo para indicar a la aplicación de servidor que active el elemento DocObject in situ.

```
virtual void OnShow();
```

### <a name="remarks"></a>Observaciones

Si el elemento no es un DocObject, la implementación predeterminada llama [a COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen). Reemplace esta función si desea realizar un procesamiento especial al abrir un elemento DocObject.

## <a name="see-also"></a>Consulte también

[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer (clase)](../../mfc/reference/cdocobjectserver-class.md)<br/>
[Clase COleDocObjectItem](../../mfc/reference/coledocobjectitem-class.md)
