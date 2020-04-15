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
ms.openlocfilehash: b8158105d09d5cfc7c25512567a98121b194a82a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368287"
---
# <a name="cricheditcntritem-class"></a>Clase CRichEditCntrItem

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md), proporciona la funcionalidad del control de edición enriquecida en el contexto de la arquitectura de vista de documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CrichEditCntrItem::CrichEditCntrItem](#cricheditcntritem)|Construye un objeto `CRichEditCntrItem`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CrichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Activa el elemento como otro tipo.|

## <a name="remarks"></a>Observaciones

Un "control de edición enriquecido" es una ventana en la que el usuario puede introducir y editar texto. Al texto se le puede asignar formato de carácter y párrafo, y puede incluir objetos OLE incrustados. Los controles de edición enriquecidos proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de la interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario.

`CRichEditView`mantiene el texto y la característica de formato del texto. `CRichEditDoc`mantiene la lista de elementos de cliente OLE que se encuentran en la vista. `CRichEditCntrItem`proporciona acceso del lado contenedor al elemento de cliente OLE.

Este control común de Windows (y, por lo tanto, [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y clases relacionadas) solo está disponible para los programas que se ejecutan en Windows 95/98 y Windows NT versiones 3.51 y posteriores.

Para obtener un ejemplo del uso de elementos de contenedor de edición enriquecidos en una aplicación MFC, vea la aplicación de ejemplo [WORDPAD.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrich.h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>CrichEditCntrItem::CrichEditCntrItem

Llame a esta `CRichEditCntrItem` función para crear un objeto y agregarlo al documento contenedor.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parámetros

*preo*<br/>
Puntero a una estructura [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) que describe un elemento OLE. El `CRichEditCntrItem` nuevo objeto se construye alrededor de este elemento OLE. Si *preo* es NULL, el elemento de cliente está vacío.

*pContainer*<br/>
Puntero al documento contenedor que contendrá este elemento. Si *pContainer* es NULL, debe llamar explícitamente [a COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) para agregar este elemento de cliente a un documento.

### <a name="remarks"></a>Observaciones

Esta función no realiza ninguna inicialización OLE.

Para obtener más información, consulte la estructura [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) en el Windows SDK.

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>CrichEditCntrItem::SyncToRichEditObject

Llame a esta función para sincronizar el `CRichEditCntrltem` aspecto del dispositivo, [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), de esto con el especificado por *reo*.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parámetros

*Reo*<br/>
Referencia a una estructura [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) que describe un elemento OLE.

### <a name="remarks"></a>Observaciones

Para obtener más información, consulte [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Clase COleClientItem](../../mfc/reference/coleclientitem-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc (clase)](../../mfc/reference/cricheditdoc-class.md)<br/>
[Clase CRichEditView](../../mfc/reference/cricheditview-class.md)
