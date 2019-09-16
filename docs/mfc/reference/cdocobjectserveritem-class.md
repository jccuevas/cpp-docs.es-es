---
title: Clase CDocObjectServerItem
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
ms.openlocfilehash: 4d44791415626f1a94500b9c3885581d67e8fe42
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506821"
---
# <a name="cdocobjectserveritem-class"></a>Clase CDocObjectServerItem

Implementa verbos de servidor OLE específicamente para servidores de DocObject.

## <a name="syntax"></a>Sintaxis

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Miembros

### <a name="protected-constructors"></a>Constructores protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Construye un objeto `CDocObjectServerItem`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Recupera un puntero al documento que contiene el elemento.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDocObjectServerItem::OnDoVerb](#ondoverb)|Se llama para ejecutar un verbo.|
|[CDocObjectServerItem::OnHide](#onhide)|Produce una excepción si el marco intenta ocultar un elemento DocObject.|
|[CDocObjectServerItem::OnShow](#onshow)|Lo llama el marco de trabajo para que el elemento de DocObject esté activo en contexto. Si el elemento no es un DocObject, llama a [COleServerItem:: show](../../mfc/reference/coleserveritem-class.md#onshow).|

## <a name="remarks"></a>Comentarios

`CDocObjectServerItem`define las funciones miembro reemplazables: [Hide](#onhide), [OnDoVerb](#ondoverb)y [Show](#onshow).

Para usar `CDocObjectServerItem`, asegúrese de que la invalidación de [OnGetEmbeddedItem](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) en la clase derivada de `COleServerDoc` devuelve un nuevo objeto `CDocObjectServerItem`. Si necesita cambiar cualquier funcionalidad del elemento, puede crear una nueva instancia de su propia `CDocObjectServerItem`clase derivada.

Para obtener más información sobre DocObjects, vea [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) y [COleCmdUI](../../mfc/reference/colecmdui-class.md) en la *referencia de MFC*.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdocob. h

##  <a name="cdocobjectserveritem"></a>  CDocObjectServerItem::CDocObjectServerItem

Construye un objeto `CDocObjectServerItem`.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parámetros

*pServerDoc*<br/>
Un puntero al documento que contendrá el nuevo elemento DocObject.

*bAutoDelete*<br/>
Indica si el objeto se puede eliminar cuando se libera un vínculo a él. Establezca el argumento en false si el `CDocObjectServerItem` objeto es una parte integral de los datos del documento. Establézcalo en TRUE si el objeto es una estructura secundaria que se usa para identificar un intervalo en los datos del documento que puede ser eliminado por el marco de trabajo.

##  <a name="getdocument"></a>  CDocObjectServerItem::GetDocument

Recupera un puntero al documento que contiene el elemento.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero al documento que contiene el elemento; Es NULL si el elemento no forma parte de un documento.

### <a name="remarks"></a>Comentarios

Esto permite el acceso al documento de servidor que pasó como argumento al constructor [CDocObjectServerItem](#cdocobjectserveritem) .

##  <a name="ondoverb"></a>  CDocObjectServerItem::OnDoVerb

Lo llama el marco de trabajo para ejecutar el verbo especificado.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parámetros

*iVerb*<br/>
Especifica el verbo que se va a ejecutar. Para ver los valores posibles, consulte [IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) en el Windows SDK.

### <a name="remarks"></a>Comentarios

La implementación predeterminada llama a la función miembro [Show](#onshow) si el elemento es un objeto DocObject y se especifica OLEIVERB_INPLACEACTIVATE o OLEIVERB_SHOW. Si el elemento no es un DocObject o se especifica un verbo diferente, la implementación predeterminada llama a [COleServerItem:: OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb).

##  <a name="onhide"></a>  CDocObjectServerItem::OnHide

Lo llama el marco de trabajo para ocultar el elemento.

```
virtual void OnHide();
```

### <a name="remarks"></a>Comentarios

La implementación predeterminada inicia una excepción si el elemento es un DocObject. No se puede ocultar un elemento DocObject activo porque toma toda la vista. Debe desactivar el elemento DocObject para que desaparezca. Si el elemento no es un DocObject, la implementación predeterminada llama a [COleServerItem:: Ocult](../../mfc/reference/coleserveritem-class.md#onhide).

##  <a name="onshow"></a>  CDocObjectServerItem::OnShow

Lo llama el marco de trabajo para indicar a la aplicación de servidor que active el elemento de DocObject en contexto.

```
virtual void OnShow();
```

### <a name="remarks"></a>Comentarios

Si el elemento no es un DocObject, la implementación predeterminada llama a [COleServerItem:: show](../../mfc/reference/coleserveritem-class.md#onopen). Invalide esta función si desea realizar un procesamiento especial al abrir un elemento DocObject.

## <a name="see-also"></a>Vea también

[COleServerItem (clase)](../../mfc/reference/coleserveritem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer (clase)](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem (clase)](../../mfc/reference/coledocobjectitem-class.md)
