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
ms.openlocfilehash: 4cc3af7649d30a153b67cd8269e595c11018833f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372093"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc (clase)

Con [CRichEditView](../../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md), proporciona la funcionalidad del control rich edit en el contexto de la arquitectura de vista de documento de MFC.

## <a name="syntax"></a>Sintaxis

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Se llama para realizar la limpieza del documento.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Indica si la secuencia de entrada y salida deben incluir información de formato.|
|[CRichEditDoc::GetView](#getview)|Recupera los tokens [CRichEditView](../../mfc/reference/cricheditview-class.md) objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Indica si E/S de secuencia deben incluir el formato.|

## <a name="remarks"></a>Comentarios

Un "control rich edit" es una ventana en la que el usuario puede escribir y editar texto. El texto se puede asignar caracteres y el formato de párrafo y puede incluir objetos OLE incrustados. Los controles Rich edit proporcionan una interfaz de programación para dar formato al texto. Sin embargo, una aplicación debe implementar los componentes de interfaz de usuario necesarios para realizar operaciones de formato disponibles para el usuario.

`CRichEditView` mantiene el texto y la característica de formato de texto. `CRichEditDoc` mantiene la lista de elementos de cliente que se encuentran en la vista. `CRichEditCntrItem` proporciona acceso a los elementos de cliente OLE de contenedor.

Este control común de Windows (y por lo tanto, el [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) y las clases relacionadas) está disponible solo para programas que se ejecutan en versiones de Windows 95/98 y Windows NT 3.51 y versiones posteriores.

Para obtener un ejemplo del uso de un documento de edición enriquecida en una aplicación MFC, vea el [WORDPAD](../../overview/visual-cpp-samples.md) aplicación de ejemplo.

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

##  <a name="createclientitem"></a>  CRichEditDoc::CreateClientItem

Llame a esta función para crear un `CRichEditCntrItem` y agregarlo a este documento.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parámetros

*preo*<br/>
Puntero a un [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) estructura que describe un elemento OLE. El nuevo `CRichEditCntrItem` se construye el objeto en torno a esta elemento OLE. Si *preo* es NULL, el nuevo elemento de cliente está vacío.

### <a name="return-value"></a>Valor devuelto

Puntero a un nuevo [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) objeto que se ha agregado a este documento.

### <a name="remarks"></a>Comentarios

Esta función no realiza ninguna inicialización de OLE.

Para obtener más información, consulte el [REOBJECT](/windows/desktop/api/richole/ns-richole-_reobject) estructura en el SDK de Windows.

##  <a name="getstreamformat"></a>  CRichEditDoc::GetStreamFormat

Llame a esta función para determinar el formato de texto para la transmisión por secuencias el contenido de la edición enriquecida.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Valor devuelto

Uno de los siguientes indicadores:

- SF_TEXT indica que el control de edición de la amplia no mantiene información de formato.

- SF_RTF indica que el control de edición de la amplia mantener la información de formato.

### <a name="remarks"></a>Comentarios

El valor devuelto se basa en el [m_bRTF](#m_brtf) miembro de datos. Esta función devuelve SF_RTF si `m_bRTF` es TRUE; en caso contrario, SF_TEXT.

##  <a name="getview"></a>  CRichEditDoc::GetView

Llame a esta función para obtener acceso a la [CRichEditView](../../mfc/reference/cricheditview-class.md) objeto asociado a este `CRichEditDoc` objeto.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la `CRichEditView` objeto asociado con el documento.

### <a name="remarks"></a>Comentarios

El texto y la información de formato se encuentran en el `CRichEditView` objeto. La `CRichEditDoc` objeto mantiene los elementos OLE para la serialización. Debe haber solo un `CRichEditView` para cada `CRichEditDoc`.

##  <a name="m_brtf"></a>  CRichEditDoc::m_bRTF

Cuando es TRUE, indica que [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) y [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) debe almacenar las características de formato de caracteres y de párrafo.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Vea también

[Ejemplo de MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc (clase)](../../mfc/reference/coleserverdoc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView (clase)](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem (clase)](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument (clase)](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl (clase)](../../mfc/reference/cricheditctrl-class.md)
