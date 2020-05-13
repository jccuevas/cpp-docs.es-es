---
title: CRichEditDoc (clase)
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 587cf65543e24e586fb8b2336481d6e841473134
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368257"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc (clase)

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control de edición enriquecida en el contexto de la arquitectura de vista de documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Se llama para realizar la limpieza del documento.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Indica si la entrada y la salida de la secuencia deben incluir información de formato.|
|[CRichEditDoc::GetView](#getview)|Recupera el objeto [CRichEditView](../../mfc/reference/cricheditview-class.md) asssociado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Indica si la E/S de secuencia debe incluir formato.|

## <a name="remarks"></a>Observaciones

Un "control de edición enriquecido" es una ventana en la que el usuario puede introducir y editar texto. Al texto se le puede asignar formato de carácter y párrafo, y puede incluir objetos OLE incrustados. Los controles de edición enriquecidos proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de la interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario.

`CRichEditView`mantiene el texto y la característica de formato del texto. `CRichEditDoc`mantiene la lista de elementos de cliente que se encuentran en la vista. `CRichEditCntrItem`proporciona acceso del lado contenedor a los elementos de cliente OLE.

Este control común de Windows (y, por lo tanto, [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y clases relacionadas) solo está disponible para los programas que se ejecutan en Windows 95/98 y Windows NT versiones 3.51 y posteriores.

Para obtener un ejemplo del uso de un documento de edición enriquecido en una aplicación MFC, vea la aplicación de ejemplo [WORDPAD.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrich.h

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a>CRichEditDoc::CreateClientItem

Llame a esta `CRichEditCntrItem` función para crear un objeto y agregarlo a este documento.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parámetros

*preo*<br/>
Puntero a una estructura [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) que describe un elemento OLE. El `CRichEditCntrItem` nuevo objeto se construye alrededor de este elemento OLE. Si *preo* es NULL, el nuevo elemento de cliente está vacío.

### <a name="return-value"></a>Valor devuelto

Puntero a un nuevo [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto que se ha agregado a este documento.

### <a name="remarks"></a>Observaciones

Esta función no realiza ninguna inicialización OLE.

Para obtener más información, consulte la estructura [REOBJECT](/windows/win32/api/richole/ns-richole-reobject) en el Windows SDK.

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat

Llame a esta función para determinar el formato de texto para transmitir el contenido de la edición enriquecida.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Valor devuelto

Una de las siguientes marcas:

- SF_TEXT Indica que el control rich edit no mantiene la información de formato.

- SF_RTF Indica que el control rich edit mantiene la información de formato.

### <a name="remarks"></a>Observaciones

El valor devuelto se basa en el [m_bRTF](#m_brtf) miembro de datos. Esta función `m_bRTF` devuelve SF_RTF if es TRUE; de lo contrario, SF_TEXT.

## <a name="cricheditdocgetview"></a><a name="getview"></a>CRichEditDoc::GetView

Llame a esta función para tener acceso `CRichEditDoc` a la [CRichEditView](../../mfc/reference/cricheditview-class.md) objeto asociado a este objeto.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al `CRichEditView` objeto asociado al documento.

### <a name="remarks"></a>Observaciones

El texto y la información `CRichEditView` de formato se encuentran dentro del objeto. El `CRichEditDoc` objeto mantiene los elementos OLE para la serialización. Debe haber sólo `CRichEditView` uno `CRichEditDoc`para cada .

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a>CRichEditDoc::m_bRTF

Cuando TRUE, indica que [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) y [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) deben almacenar características de párrafo y formato de caracteres.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Clase COleServerDoc](../../mfc/reference/coleserverdoc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CRichEditView](../../mfc/reference/cricheditview-class.md)<br/>
[Clase CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument (Clase)](../../mfc/reference/coledocument-class.md)<br/>
[Clase CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)
