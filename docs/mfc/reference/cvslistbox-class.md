---
title: CVSListBox (clase)
ms.date: 11/19/2018
f1_keywords:
- CVSListBox
- AFXVSLISTBOX/CVSListBox
- AFXVSLISTBOX/CVSListBox::CVSListBox
- AFXVSLISTBOX/CVSListBox::AddItem
- AFXVSLISTBOX/CVSListBox::EditItem
- AFXVSLISTBOX/CVSListBox::GetCount
- AFXVSLISTBOX/CVSListBox::GetItemData
- AFXVSLISTBOX/CVSListBox::GetItemText
- AFXVSLISTBOX/CVSListBox::GetSelItem
- AFXVSLISTBOX/CVSListBox::RemoveItem
- AFXVSLISTBOX/CVSListBox::SelectItem
- AFXVSLISTBOX/CVSListBox::SetItemData
- AFXVSLISTBOX/CVSListBox::GetListHwnd
helpviewer_keywords:
- CVSListBox [MFC], CVSListBox
- CVSListBox [MFC], AddItem
- CVSListBox [MFC], EditItem
- CVSListBox [MFC], GetCount
- CVSListBox [MFC], GetItemData
- CVSListBox [MFC], GetItemText
- CVSListBox [MFC], GetSelItem
- CVSListBox [MFC], RemoveItem
- CVSListBox [MFC], SelectItem
- CVSListBox [MFC], SetItemData
- CVSListBox [MFC], GetListHwnd
ms.assetid: c79be7b4-46ed-4af8-a41e-68962782d8ef
ms.openlocfilehash: 4ea48a263a01133419067979ee5fa3e62105c7f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373187"
---
# <a name="cvslistbox-class"></a>CVSListBox (clase)

La `CVSListBox` clase admite un control de lista editable.

## <a name="syntax"></a>Sintaxis

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|Construye un objeto `CVSListBox`.|
|`CVSListBox::~CVSListBox`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|Agrega una cadena a un control de lista. (Invalida `CVSListBoxBase::AddItem`).|
|[CVSListBox::EditItem](#edititem)|Inicia una operación de edición en el texto de un elemento de control de lista. (Invalida `CVSListBoxBase::EditItem`).|
|[CVSListBox::GetCount](#getcount)|Recupera el número de cadenas en un control de lista editable. (Invalida `CVSListBoxBase::GetCount`).|
|[CVSListBox::GetItemData](#getitemdata)|Recupera un valor de 32 bits específico de la aplicación que está asociado a un elemento de control de lista editable. (Invalida `CVSListBoxBase::GetItemData`).|
|[CVSListBox::GetItemText](#getitemtext)|Recupera el texto de un elemento de control de lista editable. (Invalida `CVSListBoxBase::GetItemText`).|
|[CVSListBox::GetSelItem](#getselitem)|Recupera el índice de base cero del elemento seleccionado actualmente en un control de lista editable. (Invalida `CVSListBoxBase::GetSelItem`).|
|`CVSListBox::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se distribuyan a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage.](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Para obtener más información y sintaxis de método, vea [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CVSListBoxBase::PreTranslateMessage`).|
|[CVSListBox::RemoveItem](#removeitem)|Quita un elemento de un control de lista editable. (Invalida `CVSListBoxBase::RemoveItem`).|
|[CVSListBox::SelectItem](#selectitem)|Selecciona una cadena de control de lista editable. (Invalida `CVSListBoxBase::SelectItem`).|
|[CVSListBox::SetItemData](#setitemdata)|Asocia un valor de 32 bits específico de la aplicación con un elemento de control de lista editable. (Invalida `CVSListBoxBase::SetItemData`).|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Devuelve el identificador al control de vista de lista incrustado actual.|

## <a name="remarks"></a>Observaciones

La `CVSListBox` clase proporciona un conjunto de botones de edición que permiten al usuario crear, modificar, eliminar o reorganizar los elementos de un control de lista.

A continuación se muestra una imagen del control de lista editable. La segunda entrada de lista, que se titula "Item2", se selecciona para su edición.

![Control CVSListBox](../../mfc/reference/media/cvslistbox.png "Control CVSListBox")

Si utiliza el editor de recursos para agregar un control de lista editable, observe que el panel Cuadro de **herramientas** del editor no proporciona un control de lista editable predefinido. En su lugar, agregue un control estático como el control **Cuadro** de grupo. El marco de trabajo utiliza el control estático como marcador de posición para especificar el tamaño y la posición del control de lista editable.

Para utilizar un control de lista editable `CVSListBox` en una plantilla de cuadro de diálogo, declare una variable en la clase de cuadro de diálogo. Para admitir el intercambio de datos entre `DDX_Control` la variable `DoDataExchange` y el control, defina una entrada de macro en el método del cuadro de diálogo. De forma predeterminada, el control de lista editable se crea sin botones de edición. Utilice el método heredado CVSListBoxBase::SetStandardButtons para habilitar los botones de edición.

Para obtener más información, consulte `New Controls` el directorio Samples, el ejemplo, los archivos Page3.cpp y Page3.h.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxvslistbox.h

## <a name="cvslistboxadditem"></a><a name="additem"></a>CVSListBox::AddItem

Agrega una cadena a un control de lista.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*strIext*<br/>
[en] Una referencia a una cadena.

*dwData*<br/>
[en] Un valor de 32 bits específico de la aplicación que está asociado a la cadena. El valor predeterminado es 0.

*iIndex*<br/>
[en] El índice de base cero de la posición que contendrá la cadena. Si el parámetro *iIndex* es -1, la cadena se agrega al final de la lista. El valor predeterminado es -1.

### <a name="return-value"></a>Valor devuelto

El índice de base cero de la posición de la cadena en el control de lista.

### <a name="remarks"></a>Observaciones

Utilice el método [CVSListBox::GetItemData](#getitemdata) para recuperar el valor especificado por el parámetro *dwData.* Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.

## <a name="cvslistboxcvslistbox"></a><a name="cvslistbox"></a>CVSListBox::CVSListBox

Construye un objeto `CVSListBox`.

```
CVSListBox();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cvslistboxedititem"></a><a name="edititem"></a>CVSListBox::EditItem

Inicia una operación de edición en el texto de un elemento de control de lista.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento de control de lista.

### <a name="return-value"></a>Valor devuelto

TRUESi la operación de edición se inicia correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

El usuario inicia una operación de edición haciendo doble clic en la etiqueta de un elemento o presionando la tecla **F2** o **BARRA ESPACIADORA** cuando un elemento tiene el foco.

## <a name="cvslistboxgetcount"></a><a name="getcount"></a>CVSListBox::GetCount

Recupera el número de cadenas en un control de lista editable.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos en el control de lista.

### <a name="remarks"></a>Observaciones

Tenga en cuenta que el recuento es uno mayor que el valor de índice del último elemento porque el índice se basa en cero.

## <a name="cvslistboxgetitemdata"></a><a name="getitemdata"></a>CVSListBox::GetItemData

Recupera un valor de 32 bits específico de la aplicación que está asociado a un elemento de control de lista editable.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento de control de lista editable.

### <a name="return-value"></a>Valor devuelto

El valor de 32 bits asociado al elemento especificado.

### <a name="remarks"></a>Observaciones

Utilice el método [CVSListBox::SetItemData](#setitemdata) o [CVSListBox::AddItem](#additem) para asociar el valor de 32 bits con el elemento de control de lista. Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.

## <a name="cvslistboxgetitemtext"></a><a name="getitemtext"></a>CVSListBox::GetItemText

Recupera el texto de un elemento de control de lista editable.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento de control de lista editable.

### <a name="return-value"></a>Valor devuelto

Un [CString](../../atl-mfc-shared/reference/cstringt-class.md) objeto que contiene el texto del elemento especificado.

### <a name="remarks"></a>Observaciones

## <a name="cvslistboxgetlisthwnd"></a><a name="getlisthwnd"></a>CVSListBox::GetListHwnd

Devuelve el identificador al control de vista de lista incrustado actual.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del control de vista de lista incrustado.

### <a name="remarks"></a>Observaciones

Utilice este método para recuperar un identificador para el `CVSListBox` control de vista de lista incrustado que admite la clase.

## <a name="cvslistboxgetselitem"></a><a name="getselitem"></a>CVSListBox::GetSelItem

Recupera el índice de base cero del elemento seleccionado actualmente en un control de lista editable.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Valor devuelto

Si este método se realiza correctamente, el índice de base cero del elemento seleccionado actualmente; de lo contrario, -1.

### <a name="remarks"></a>Observaciones

## <a name="cvslistboxremoveitem"></a><a name="removeitem"></a>CVSListBox::RemoveItem

Quita un elemento de un control de lista editable.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento de control de lista editable.

### <a name="return-value"></a>Valor devuelto

TRUESi se quita el elemento especificado; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

## <a name="cvslistboxselectitem"></a><a name="selectitem"></a>CVSListBox::SelectItem

Selecciona una cadena de control de lista editable.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Parámetros

*iItem*<br/>
[en] El índice de base cero de un elemento de control de lista editable.

### <a name="return-value"></a>Valor devuelto

TRUESi este método se realiza correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método selecciona el elemento especificado y, si es necesario, desplaza el elemento a la vista.

## <a name="cvslistboxsetitemdata"></a><a name="setitemdata"></a>CVSListBox::SetItemData

Asocia un valor de 32 bits específico de la aplicación con un elemento de control de lista editable.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
[en] El índice de base cero de un elemento de control de lista editable.

*dwData*<br/>
[en] Un valor de 32 bits. Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
