---
title: CDragListBox (clase)
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: d8afc5b14f5f52ca7a4d28a3d3c3c5440b7c819f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781593"
---
# <a name="cdraglistbox-class"></a>CDragListBox (clase)

Además de proporcionar la funcionalidad de un cuadro de lista de Windows, la `CDragListBox` clase permite al usuario mover elementos de cuadro de lista, como los nombres de archivo, en el cuadro de lista.

## <a name="syntax"></a>Sintaxis

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|Construye un objeto `CDragListBox`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|Lo llama el marco de trabajo cuando se inicia una operación de arrastre.|
|[CDragListBox::CancelDrag](#canceldrag)|Lo llama el marco de trabajo cuando se ha cancelado una operación de arrastre.|
|[CDragListBox::Dragging](#dragging)|Lo llama el marco de trabajo durante una operación de arrastre.|
|[CDragListBox::DrawInsert](#drawinsert)|Dibuja a la Guía de inserción del cuadro de lista de arrastre.|
|[CDragListBox::Dropped](#dropped)|Lo llama el marco de trabajo después de que se ha quitado el elemento.|
|[CDragListBox::ItemFromPt](#itemfrompt)|Devuelve las coordenadas del elemento que se está arrastrando.|

## <a name="remarks"></a>Comentarios

Cuadros de lista con esta funcionalidad permiten a los usuarios ordenar los elementos en una lista de la manera más útil. De forma predeterminada, el cuadro de lista moverá el elemento a la nueva ubicación en la lista. Sin embargo, `CDragListBox` objetos se pueden personalizar para copiar elementos en lugar de moverlos.

El control de cuadro de lista asociada con el `CDragListBox` clase no debe tener el LBS_SORT o el estilo LBS_MULTIPLESELECT. Para obtener una descripción de los estilos de cuadro de lista, consulte [estilos de cuadro de lista](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Para usar un cuadro de lista de arrastre en un cuadro de diálogo existente de la aplicación, agregue un control de cuadro de lista a la plantilla de cuadro de diálogo con el editor de cuadro de diálogo y, a continuación, asignar una variable miembro (de categoría `Control` y el tipo de Variable `CDragListBox`) correspondiente al cuadro de lista controlar en la plantilla de cuadro de diálogo.

Para obtener más información sobre la asignación de controles a las variables miembro, vea [acceso directo para definir Variables miembro para controles de cuadro de diálogo](../../windows/defining-member-variables-for-dialog-controls.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="begindrag"></a>  CDragListBox::BeginDrag

Lo llama el marco de trabajo cuando produce un evento que pudiera iniciar una operación de arrastre, por ejemplo, al presionar el botón primario del mouse.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas del elemento que se está arrastrando.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la operación de arrastre puede, 0 en caso contrario.

### <a name="remarks"></a>Comentarios

Reemplace esta función si desea controlar lo que ocurre cuando se inicia una operación de arrastre. La implementación predeterminada, captura el mouse y permanece en modo de arrastre hasta que el usuario hace clic en el botón izquierdo o derecho del mouse o presiona ESC, momento en el que se cancela la operación de arrastre.

##  <a name="canceldrag"></a>  CDragListBox::CancelDrag

Lo llama el marco de trabajo cuando se ha cancelado una operación de arrastre.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas del elemento que se está arrastrando.

### <a name="remarks"></a>Comentarios

Reemplace esta función para controlar cualquier procesamiento especial para el control de cuadro de lista.

##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox

Construye un objeto `CDragListBox`.

```
CDragListBox();
```

##  <a name="dragging"></a>  CDragListBox::Dragging

Lo llama el marco de trabajo cuando se arrastra un elemento de cuadro de lista dentro de la `CDragListBox` objeto.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene x e y coordenadas del cursor de la pantalla.

### <a name="return-value"></a>Valor devuelto

El identificador de recurso del cursor que se mostrará. Los valores posibles son:

- DL_COPYCURSOR indica que se copiará el elemento.

- DL_MOVECURSOR indica que se moverá el elemento.

- DL_STOPCURSOR indica que el destino de colocación actual no es aceptable.

### <a name="remarks"></a>Comentarios

El comportamiento predeterminado devuelve DL_MOVECURSOR. Reemplace esta función si desea proporcionar funcionalidad adicional.

##  <a name="drawinsert"></a>  CDragListBox::DrawInsert

Lo llama el marco de trabajo para dibujar a la Guía de inserción antes del elemento con el índice indicado.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
Índice de base cero del punto de inserción.

### <a name="remarks"></a>Comentarios

Un valor de - 1 borra a la Guía de inserción. Reemplace esta función para modificar la apariencia o comportamiento de la Guía de inserción.

##  <a name="dropped"></a>  CDragListBox::Dropped

Lo llama el marco de trabajo cuando se quita un elemento dentro de un `CDragListBox` objeto.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parámetros

*nSrcIndex*<br/>
Especifica el índice de base cero de la cadena quitada.

*pt*<br/>
Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas del sitio de destino.

### <a name="remarks"></a>Comentarios

El comportamiento predeterminado, copia el elemento de cuadro de lista y sus datos a la nueva ubicación y, a continuación, elimina el elemento original. Reemplace esta función para personalizar el comportamiento predeterminado, como la habilitación de copias de los elementos de cuadro de lista arrastrar a otras ubicaciones dentro de la lista.

##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt

Llamada a esta función para recuperar el índice de base cero del elemento de cuadro de lista que se encuentra en *pt*.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parámetros

*pt*<br/>
Un [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto que contiene las coordenadas de un punto en el cuadro de lista.

*bAutoScroll*<br/>
Distinto de cero si se permite el desplazamiento, en caso contrario, 0.

### <a name="return-value"></a>Valor devuelto

Índice de base cero del elemento de cuadro de lista de arrastre.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CListBox (clase)](../../mfc/reference/clistbox-class.md)
