---
title: Clase CRichEditDoc
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
ms.openlocfilehash: def0c55ff1faf12729226aa445c9614119c546c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502675"
---
# <a name="cricheditdoc-class"></a>Clase CRichEditDoc

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control Rich Edit en el contexto de la arquitectura de la vista del documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Se llama para realizar la limpieza del documento.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Indica si la entrada y la salida de la secuencia deben incluir información de formato.|
|[CRichEditDoc::GetView](#getview)|Recupera el objeto asssociated [CRichEditView](../../mfc/reference/cricheditview-class.md) .|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Indica si la e/s de secuencia debe incluir formato.|

## <a name="remarks"></a>Comentarios

Un "control Rich Edit" es una ventana en la que el usuario puede escribir y editar texto. El texto puede tener asignado un formato de carácter y de párrafo, y puede incluir objetos OLE incrustados. Los controles Rich Edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para que las operaciones de formato estén disponibles para el usuario.

`CRichEditView`mantiene el texto y la característica de formato del texto. `CRichEditDoc`mantiene la lista de elementos de cliente que se encuentran en la vista. `CRichEditCntrItem`proporciona acceso de contenedor a los elementos de cliente OLE.

Este control común de Windows (y, por tanto, la clase [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas) solo está disponible para programas que se ejecutan en Windows 95/98 y en las versiones 3,51 y posteriores de Windows NT.

Para obtener un ejemplo del uso de un documento de edición enriquecida en una aplicación MFC, vea la aplicación de ejemplo de [WordPad](../../overview/visual-cpp-samples.md) .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxrich. h

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

Llame a esta función para crear `CRichEditCntrItem` un objeto y agregarlo a este documento.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parámetros

*preo*<br/>
Puntero a una estructura de [reobjeto](/windows/win32/api/richole/ns-richole-reobject) que describe un elemento OLE. El nuevo `CRichEditCntrItem` objeto se construye en torno a este elemento OLE. Si *preo* es null, el nuevo elemento de cliente está vacío.

### <a name="return-value"></a>Valor devuelto

Puntero a un nuevo objeto [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) que se ha agregado a este documento.

### <a name="remarks"></a>Comentarios

Esta función no realiza ninguna inicialización OLE.

Para obtener más información, vea la estructura de [reobjeto](/windows/win32/api/richole/ns-richole-reobject) en el Windows SDK.

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

Llame a esta función para determinar el formato de texto para transmitir por secuencias el contenido de la edición enriquecida.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Valor devuelto

Una de las marcas siguientes:

- SF_TEXT indica que el control Rich Edit no mantiene información de formato.

- SF_RTF indica que el control Rich Edit mantiene la información de formato.

### <a name="remarks"></a>Comentarios

El valor devuelto se basa en el miembro de datos [m_bRTF](#m_brtf) . Esta función devuelve SF_RTF si `m_bRTF` es true; de lo contrario, SF_TEXT.

##  <a name="getview"></a>CRichEditDoc:: GetView (

Llame a esta función para tener acceso al objeto [CRichEditView](../../mfc/reference/cricheditview-class.md) asociado `CRichEditDoc` a este objeto.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero al `CRichEditView` objeto asociado al documento.

### <a name="remarks"></a>Comentarios

El texto y la información de formato están incluidos `CRichEditView` en el objeto. El `CRichEditDoc` objeto mantiene los elementos OLE para la serialización. Solo debe haber uno `CRichEditView` para cada. `CRichEditDoc`

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

Si es TRUE, indica que [CRichEditCtrl:: Streamen](../../mfc/reference/cricheditctrl-class.md#streamin) y [CRichEditCtrl:: StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) deben almacenar características de formato de párrafo y de carácter.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Vea también

[WORDPAD de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc (clase)](../../mfc/reference/coleserverdoc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem (clase)](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument (clase)](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl (clase)](../../mfc/reference/cricheditctrl-class.md)
