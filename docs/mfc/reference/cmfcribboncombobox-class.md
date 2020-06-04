---
title: CMFCRibbonComboBox (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 5846b1c5590a756f0a0820583af3d0b159968ea2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375224"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox (clase)

La `CMFCRibbonComboBox` clase implementa un control de cuadro combinado que puede agregar a una barra de la cinta de opciones, un panel de la cinta de opciones o un menú emergente de la cinta de opciones.

## <a name="syntax"></a>Sintaxis

```cpp
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>Miembros

### <a name="constructors"></a>Constructores

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|Construye un CMFCRibbonComboBox objeto.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|Anexa un elemento único al cuadro de lista.|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|Elimina un elemento especificado del cuadro de lista.|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|Especifica si el cuadro de lista puede cambiar de tamaño cuando se cae hacia abajo.|
|[CMFCRibbonComboBox::FindItem](#finditem)|Devuelve el índice del primer elemento del cuadro de lista que coincide con una cadena especificada.|
|[CMFCRibbonComboBox::GetCount](#getcount)|Devuelve el número de elementos del cuadro de lista.|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|Obtiene el índice del elemento seleccionado actualmente en el cuadro de lista.|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|Obtiene el alto del cuadro de lista cuando se coloca el cuadro de lista.|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|Devuelve el tamaño del cuadro combinado tal como se muestra en el modo intermedio.|
|[CMFCRibbonComboBox::GetItem](#getitem)|Devuelve la cadena asociada a un elemento en un índice especificado en el cuadro de lista.|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|Devuelve los datos asociados a un elemento en un índice especificado en el cuadro de lista.|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|Indica si el control contiene un cuadro de edición.|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|Indica si se puede cambiar el tamaño del cuadro de lista.|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|Llamado por el marco de trabajo cuando el usuario selecciona un elemento en el cuadro de lista.|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|Elimina todos los elementos del cuadro de lista y borra el cuadro de edición.|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|Selecciona un elemento en el cuadro de lista.|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|Establece la altura del cuadro de lista cuando se deja caer.|

## <a name="remarks"></a>Observaciones

El cuadro combinado de la cinta de opciones consta de un cuadro de lista combinado con una etiqueta estática o una etiqueta que el usuario puede editar. Debe especificar el tipo que desea al crear el cuadro combinado de la cinta de opciones.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCRibbonComboBox` cómo construir un objeto de la clase, agregar un elemento al cuadro combinado, seleccionar un elemento en el cuadro combinado y agregar un cuadro combinado a un panel.

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxribboncombobox.h

## <a name="cmfcribboncomboboxadditem"></a><a name="additem"></a>CMFCRibbonComboBox::AddItem

Anexa un elemento único al cuadro de lista.

```cpp
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parámetros

*lpszItem*<br/>
[en] La cadena del elemento que se va a agregar.

*dwData*<br/>
[en] Los datos asociados con el elemento que se va a agregar.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento anexado.

## <a name="cmfcribboncomboboxcmfcribboncombobox"></a><a name="cmfcribboncombobox"></a>CMFCRibbonComboBox::CMFCRibbonComboBox

Construye un objeto `CMFCRibbonComboBox`.

```cpp
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>Parámetros

*nID*<br/>
[en] El identificador del cuadro combinado.

*bHasEditBox*<br/>
[en] TRUESi desea un cuadro de edición dentro del control; FALSE en caso contrario.

*nAncho*<br/>
[en] Ancho del cuadro combinado en píxeles; o -1 para el ancho predeterminado.

*lpszLabel*<br/>
[en] La etiqueta de visualización del cuadro combinado.

*nImage*<br/>
[en] El pequeño índice de imagen del cuadro combinado.

### <a name="remarks"></a>Observaciones

El ancho predeterminado es de 108 píxeles.

## <a name="cmfcribboncomboboxdeleteitem"></a><a name="deleteitem"></a>CMFCRibbonComboBox::DeleteItem

Elimina un elemento especificado del cuadro de lista.

```cpp
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero del elemento que se va a eliminar.

*dwData*<br/>
[en] Los datos asociados con el elemento que se va a eliminar.

*lpszText*<br/>
[en] La cadena del elemento que se va a eliminar. Si hay varios elementos con la misma cadena, se elimina el primer elemento.

### <a name="return-value"></a>Valor devuelto

TRUESi se ha eliminado el elemento especificado; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxenabledropdownlistresize"></a><a name="enabledropdownlistresize"></a>CMFCRibbonComboBox::EnableDropDownListResize

Especifica si el cuadro de lista puede cambiar de tamaño cuando se cae hacia abajo.

```cpp
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>Parámetros

*bHabilitar*<br/>
[en] TRUE para habilitar el cambio de tamaño; FALSE para deshabilitar el cambio de tamaño.

### <a name="remarks"></a>Observaciones

Cuando se habilita el cambio de tamaño, el cuadro de lista cambiará de tamaño para que se ajuste a los elementos que muestra.

## <a name="cmfcribboncomboboxfinditem"></a><a name="finditem"></a>CMFCRibbonComboBox::FindItem

Devuelve el índice del primer elemento del cuadro de lista que coincide con una cadena especificada.

```cpp
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
[en] La cadena de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento; o -1 si no se encuentra el elemento.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxgetcount"></a><a name="getcount"></a>CMFCRibbonComboBox::GetCount

Devuelve el número de elementos del cuadro de lista.

```cpp
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de elementos del cuadro de lista o 0 si el cuadro de lista no contiene elementos.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxgetcursel"></a><a name="getcursel"></a>CMFCRibbonComboBox::GetCurSel

Obtiene el índice del elemento seleccionado actualmente en el cuadro de lista.

```cpp
int GetCurSel() const;
```

### <a name="return-value"></a>Valor devuelto

El índice de base cero del elemento seleccionado actualmente en el cuadro de lista; o -1 si no se selecciona ningún elemento.

## <a name="cmfcribboncomboboxgetdropdownheight"></a><a name="getdropdownheight"></a>CMFCRibbonComboBox::GetDropDownHeight

Obtiene el alto del cuadro de lista cuando se coloca el cuadro de lista.

```cpp
int GetDropDownHeight();
```

### <a name="return-value"></a>Valor devuelto

Altura, en píxeles, del cuadro de lista.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxgetintermediatesize"></a><a name="getintermediatesize"></a>CMFCRibbonComboBox::GetIntermediateSize

Devuelve el tamaño del cuadro combinado tal como se muestra en el modo intermedio.

```cpp
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
[en] Puntero a un contexto de dispositivo para el cuadro combinado.

### <a name="return-value"></a>Valor devuelto

El tamaño del cuadro combinado.

### <a name="remarks"></a>Observaciones

El tamaño devuelto se basa en el tamaño del cuadro combinado cuando muestra imágenes pequeñas.

## <a name="cmfcribboncomboboxgetitem"></a><a name="getitem"></a>CMFCRibbonComboBox::GetItem

Devuelve la cadena asociada a un elemento en un índice especificado en el cuadro de lista.

```cpp
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Un puntero a la cadena que está asociada con el elemento; de lo contrario, NULL si el parámetro de índice no es válido, o si el parámetro de índice es -1 y no hay ningún elemento seleccionado en el cuadro combinado.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxgetitemdata"></a><a name="getitemdata"></a>CMFCRibbonComboBox::GetItemData

Devuelve los datos asociados a un elemento en un índice especificado en el cuadro de lista.

```cpp
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

Los datos asociados con el elemento; o 0 si el elemento no existe, o si el parámetro de índice es -1 y no hay ningún elemento seleccionado en el cuadro de lista.

## <a name="cmfcribboncomboboxhaseditbox"></a><a name="haseditbox"></a>CMFCRibbonComboBox::HasEditBox

Indica si el control contiene un cuadro de edición.

```cpp
BOOL HasEditBox() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el control contiene un cuadro de edición; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxisresizedropdownlist"></a><a name="isresizedropdownlist"></a>CMFCRibbonComboBox::IsResizeDropDownList

Indica si se puede cambiar el tamaño del cuadro de lista.

```cpp
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se puede cambiar el tamaño del cuadro de lista; de lo contrario FALSO. [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Observaciones

Puede habilitar el cambio de tamaño del cuadro de lista mediante el [método CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize) .

## <a name="cmfcribboncomboboxonselectitem"></a><a name="onselectitem"></a>CMFCRibbonComboBox::OnSelectItem

Llamado por el marco de trabajo cuando un usuario selecciona un elemento en el cuadro de lista.

```cpp
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
[en] El índice del elemento seleccionado.

### <a name="remarks"></a>Observaciones

Invalide este método si desea procesar una selección de entrada de usuario.

## <a name="cmfcribboncomboboxremoveallitems"></a><a name="removeallitems"></a>CMFCRibbonComboBox::RemoveAllItems

Elimina todos los elementos del cuadro de lista y borra el cuadro de edición.

```cpp
void RemoveAllItems();
```

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxselectitem"></a><a name="selectitem"></a>CMFCRibbonComboBox::SelectItem

Selecciona un elemento en el cuadro de lista.

```cpp
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento en el cuadro de lista.

*dwData*<br/>
[en] Los datos asociados a un elemento en el cuadro de lista.

*lpszText*<br/>
[en] La cadena de un elemento en el cuadro de lista.

### <a name="return-value"></a>Valor devuelto

TRUESi el método se realizó correctamente; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

## <a name="cmfcribboncomboboxsetdropdownheight"></a><a name="setdropdownheight"></a>CMFCRibbonComboBox::SetDropDownHeight

Establece la altura del cuadro de lista cuando se deja caer.

```cpp
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>Parámetros

*nAltura*<br/>
[en] Altura, en píxeles, del cuadro de lista.

### <a name="remarks"></a>Observaciones

La altura predeterminada es de 150 píxeles.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit Clase](../../mfc/reference/cmfcribbonedit-class.md)
