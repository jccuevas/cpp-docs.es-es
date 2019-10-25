---
title: Clase CRichEditCntrItem
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: 8e242504c8ab0f59f6dec0602d4a5352a2d84867
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502726"
---
# <a name="cricheditcntritem-class"></a>Clase CRichEditCntrItem

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), proporciona la funcionalidad del control Rich Edit en el contexto de la arquitectura de la vista del documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Construye un objeto `CRichEditCntrItem`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Activa el elemento como otro tipo.|

## <a name="remarks"></a>Comentarios

Un "control Rich Edit" es una ventana en la que el usuario puede escribir y editar texto. El texto puede tener asignado un formato de carácter y de párrafo, y puede incluir objetos OLE incrustados. Los controles Rich Edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario.

`CRichEditView`mantiene el texto y la característica de formato del texto. `CRichEditDoc`mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem`proporciona acceso de contenedor al elemento de cliente OLE.

Este control común de Windows (y, por tanto, la clase [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas) solo está disponible para programas que se ejecutan en Windows 95/98 y en las versiones 3,51 y posteriores de Windows NT.

Para obtener un ejemplo del uso de elementos de contenedor de edición enriquecida en una aplicación MFC, vea la aplicación de ejemplo de [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrich. h

##  <a name="cricheditcntritem"></a>  CRichEditCntrItem::CRichEditCntrItem

Llame a esta función para crear `CRichEditCntrItem` un objeto y agregarlo al documento contenedor.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parámetros

*preo*<br/>
Puntero a una estructura de [reobjeto](/windows/win32/api/richole/ns-richole-reobject) que describe un elemento OLE. El nuevo `CRichEditCntrItem` objeto se construye en torno a este elemento OLE. Si *preo* es null, el elemento de cliente está vacío.

*pContainer*<br/>
Puntero al documento contenedor que contendrá este elemento. Si *que pcontainer sea* es null, debe llamar explícitamente a [COleDocument:: AddItem](../../mfc/reference/coledocument-class.md#additem) para agregar este elemento de cliente a un documento.

### <a name="remarks"></a>Comentarios

Esta función no realiza ninguna inicialización OLE.

Para obtener más información, vea la estructura de [reobjeto](/windows/win32/api/richole/ns-richole-reobject) en el Windows SDK.

##  <a name="synctoricheditobject"></a>  CRichEditCntrItem::SyncToRichEditObject

Llame a esta función para sincronizar el aspecto del dispositivo, [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), de este `CRichEditCntrltem` con el especificado por *reo*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parámetros

*reo*<br/>
Referencia a una estructura de [reobjeto](/windows/win32/api/richole/ns-richole-reobject) que describe un elemento OLE.

### <a name="remarks"></a>Comentarios

Para obtener más información, vea [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) en el Windows SDK.

## <a name="see-also"></a>Vea también

[WORDPAD de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem (clase)](../../mfc/reference/coleclientitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc (clase)](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)
