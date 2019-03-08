---
title: CTabView (clase)
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: 5ac62d04c38dbddda90d2f33a9c14c9c131fcd9c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326600"
---
# <a name="ctabview-class"></a>CTabView (clase)

El `CTabView` clase simplifica el uso de la clase de control de pestaña ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) en las aplicaciones que utilizan la arquitectura documento/vista de MFC.

## <a name="syntax"></a>Sintaxis

```
class CTabbedView : public CView
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTabView::AddView](#addview)|Agrega una nueva vista para el control de ficha.|
|[CTabView::FindTab](#findtab)|Devuelve el índice de la vista especificada en el control de ficha.|
|[CTabView::GetActiveView](#getactiveview)|Devuelve un puntero a la vista activa|
|[CTabView::GetTabControl](#gettabcontrol)|Devuelve una referencia al control de ficha asociado a la vista.|
|[CTabView::RemoveView](#removeview)|Quita la vista del control de ficha.|
|[CTabView::SetActiveView](#setactiveview)|Una vista activa.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CTabView::IsScrollBar](#isscrollbar)|Lo llama el marco de trabajo al crear una vista de ficha para determinar si la vista tiene una barra de desplazamiento horizontal compartida.|
|[CTabView::OnActivateView](#onactivateview)|Lo llama el marco de trabajo cuando se realiza la vista de ficha activo o inactivo.|

## <a name="remarks"></a>Comentarios

Esta clase facilita la poner una vista con pestañas en una aplicación de documento/vista. `CTabView` es un `CView`-clase derivada que contiene incrustado `CMFCTabCtrl` objeto. `CTabView` administra todos los mensajes necesarios para admitir la `CMFCTabCtrl` objeto. Simplemente derive una clase de `CTabView` y conectarlo a la aplicación y, después, agregar `CView`-las clases derivadas utilizando el `AddView` método. El control de ficha mostrará esas vistas como pestañas.

Por ejemplo, podría tener un documento que se puede representar de maneras diferentes: como una hoja de cálculo, un gráfico, un formulario modificable y así sucesivamente. Puede crear vistas individuales de los datos de dibujo según sea necesario, insertarlos en su `CTabView`-objeto derivado y tenerlos por pestañas sin ninguna codificación adicional.

[Ejemplo de TabbedView: Aplicación de vista de MFC con fichas](../../visual-cpp-samples.md) se muestra el uso de `CTabView`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra cómo `CTabView` se usa en el ejemplo TabbedView.

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>Requisitos

**Encabezado:** afxTabView.h

##  <a name="addview"></a>  CTabView::AddView

Agrega una vista para el control de ficha.

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>Parámetros

*pViewClass*<br/>
[in] Un puntero a una clase en tiempo de ejecución de la vista insertada.

*strViewLabel*<br/>
[in] Especifica el texto de la pestaña.

*iIndex*<br/>
[in] Especifica la posición de base cero donde se inserta en la vista. Si la posición es -1 se inserta la nueva pestaña al final.

*pContext*<br/>
[in] Un puntero a la `CCreateContext` de la vista.

### <a name="return-value"></a>Valor devuelto

Un índice de la vista si este método se realiza correctamente. En caso contrario, es -1.

### <a name="remarks"></a>Comentarios

Llame a esta función para agregar una vista para el control de ficha que se incrusta en un marco.

##  <a name="findtab"></a>  CTabView::FindTab

Devuelve el índice de la vista especificada en el control de ficha.

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>Parámetros

*hWndView*<br/>
[in] El identificador de la vista.

### <a name="return-value"></a>Valor devuelto

El índice de la vista si se encuentra; en caso contrario, es -1.

### <a name="remarks"></a>Comentarios

Llame a esta función para recuperar el índice de una vista que tiene un identificador especificado.

##  <a name="getactiveview"></a>  CTabView::GetActiveView

Devuelve un puntero a la vista activa actualmente.

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero válido a la vista activa, o NULL si no hay ninguna vista activa.

### <a name="remarks"></a>Comentarios

##  <a name="gettabcontrol"></a>  CTabView::GetTabControl

Devuelve una referencia al control de ficha asociado a la vista.

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>Valor devuelto

Una referencia al control de ficha asociado a la vista.

##  <a name="isscrollbar"></a>  CTabView::IsScrollBar

Lo llama el marco de trabajo al crear una vista de ficha para determinar si la vista tiene una barra de desplazamiento horizontal compartida.

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la vista debe crearse junto con una barra de desplazamiento compartido. En caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El marco llama a este método cuando un *CTabView* se está creando el objeto.

Invalidar el *IsScrollBar* método en un *CTabView*-clase derivada y devuelve TRUE si desea crear una vista que tiene una barra de desplazamiento horizontal compartida.

##  <a name="onactivateview"></a>  CTabView::OnActivateView

Lo llama el marco de trabajo cuando se realiza la vista de ficha activo o inactivo.

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>Parámetros

*view*<br/>
[in] Un puntero a la vista.

### <a name="remarks"></a>Comentarios

La implementación predeterminada no hace nada. Invalide este método en un `CTabView`-clase derivada para procesar esta notificación.

##  <a name="removeview"></a>  CTabView::RemoveView

Quita la vista del control de ficha.

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>Parámetros

*iTabNum*<br/>
[in] El índice de la vista para quitar.

### <a name="return-value"></a>Valor devuelto

El índice de la vista quitado si este método se realiza correctamente. En caso contrario,-1.

### <a name="remarks"></a>Comentarios

##  <a name="setactiveview"></a>  CTabView::SetActiveView

Una vista activa.

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>Parámetros

*iTabNum*<br/>
[in] Índice de base cero de la vista de ficha.

### <a name="return-value"></a>Valor devuelto

TRUE si la vista especificada se realizó activa, es FALSE si el índice de la vista no es válido.

### <a name="remarks"></a>Comentarios

Para obtener más información, consulte [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab).

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView (clase)](../../mfc/reference/cview-class.md)
