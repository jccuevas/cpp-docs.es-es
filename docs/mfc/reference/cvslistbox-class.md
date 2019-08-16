---
title: Clase CVSListBox
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
ms.openlocfilehash: 6a33f5b64c5094bfe2ca2ff259b5cd8654058ed3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502230"
---
# <a name="cvslistbox-class"></a>Clase CVSListBox

La `CVSListBox` clase admite un control de lista modificable.

## <a name="syntax"></a>Sintaxis

```
class CVSListBox : public CVSListBoxBase
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CVSListBox::CVSListBox](#cvslistbox)|Construye un objeto `CVSListBox`.|
|`CVSListBox::~CVSListBox`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CVSListBox::AddItem](#additem)|Agrega una cadena a un control de lista. (Invalida `CVSListBoxBase::AddItem`).|
|[CVSListBox::EditItem](#edititem)|Inicia una operación de edición en el texto de un elemento de control de lista. (Invalida `CVSListBoxBase::EditItem`).|
|[CVSListBox::GetCount](#getcount)|Recupera el número de cadenas de un control de lista modificable. (Invalida `CVSListBoxBase::GetCount`).|
|[CVSListBox::GetItemData](#getitemdata)|Recupera un valor de 32 bits específico de la aplicación que está asociado a un elemento de control de lista modificable. (Invalida `CVSListBoxBase::GetItemData`).|
|[CVSListBox::GetItemText](#getitemtext)|Recupera el texto de un elemento de control de lista modificable. (Invalida `CVSListBoxBase::GetItemText`).|
|[CVSListBox::GetSelItem](#getselitem)|Recupera el índice de base cero del elemento actualmente seleccionado en un control de lista modificable. (Invalida `CVSListBoxBase::GetSelItem`).|
|`CVSListBox::PreTranslateMessage`|Traduce los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . Para obtener más información y la sintaxis de método, vea [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Invalida `CVSListBoxBase::PreTranslateMessage`).|
|[CVSListBox::RemoveItem](#removeitem)|Quita un elemento de un control de lista modificable. (Invalida `CVSListBoxBase::RemoveItem`).|
|[CVSListBox::SelectItem](#selectitem)|Selecciona una cadena de control de lista modificable. (Invalida `CVSListBoxBase::SelectItem`).|
|[CVSListBox::SetItemData](#setitemdata)|Asocia un valor de 32 bits específico de la aplicación con un elemento de control de lista modificable. (Invalida `CVSListBoxBase::SetItemData`).|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CVSListBox::GetListHwnd](#getlisthwnd)|Devuelve el identificador del control de vista de lista incrustado actual.|

## <a name="remarks"></a>Comentarios

La `CVSListBox` clase proporciona un conjunto de botones de edición que permiten al usuario crear, modificar, eliminar o reorganizar los elementos de un control de lista.

A continuación se muestra una imagen del control de lista modificable. La segunda entrada de la lista, que se titula "Item2", se selecciona para su edición.

![Control CVSListBox](../../mfc/reference/media/cvslistbox.png "Control CVSListBox")

Si usa el editor de recursos para agregar un control de lista modificable, tenga en cuenta que el panel **cuadro de herramientas** del editor no proporciona un control de lista modificable predefinido. En su lugar, agregue un control estático, como el control de **cuadro de grupo** . El marco de trabajo utiliza el control estático como un marcador de posición para especificar el tamaño y la posición del control de lista modificable.

Para usar un control de lista modificable en una plantilla de cuadro de `CVSListBox` diálogo, declare una variable en la clase de cuadro de diálogo. Para admitir el intercambio de datos entre la variable y el control, `DDX_Control` defina una entrada de `DoDataExchange` macro en el método del cuadro de diálogo. De forma predeterminada, el control de lista modificable se crea sin botones de edición. Use el método CVSListBoxBase:: SetStandardButtons heredado para habilitar los botones de edición.

Para obtener más información, vea el directorio Samples `New Controls` , el ejemplo, los archivos Page3. cpp y Page3. h.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CStatic](../../mfc/reference/cstatic-class.md)

`CVSListBoxBase`

[CVSListBox](../../mfc/reference/cvslistbox-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxvslistbox. h

##  <a name="additem"></a>  CVSListBox::AddItem

Agrega una cadena a un control de lista.

```
virtual int AddItem(
    const CString& strIext,
    DWORD_PTR dwData=0,
    int iIndex=-1);
```

### <a name="parameters"></a>Parámetros

*strIext*<br/>
de Referencia a una cadena.

*dwData*<br/>
de Valor de 32 bits específico de la aplicación que está asociado a la cadena. El valor predeterminado es 0.

*iIndex*<br/>
de Índice de base cero de la posición que va a contener la cadena. Si el parámetro *iIndex* es-1, la cadena se agrega al final de la lista. El valor predeterminado es -1.

### <a name="return-value"></a>Valor devuelto

Índice de base cero de la posición de la cadena en el control de lista.

### <a name="remarks"></a>Comentarios

Use el método [CVSListBox:: GetItemData](#getitemdata) para recuperar el valor especificado por el parámetro *dwData* . Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.

##  <a name="cvslistbox"></a>  CVSListBox::CVSListBox

Construye un objeto `CVSListBox`.

```
CVSListBox();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="edititem"></a>  CVSListBox::EditItem

Inicia una operación de edición en el texto de un elemento de control de lista.

```
virtual BOOL EditItem(int iIndex);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento de control de lista.

### <a name="return-value"></a>Valor devuelto

TRUE si la operación de edición se inicia correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

El usuario inicia una operación de edición haciendo doble clic en la etiqueta de un elemento o presionando la tecla **F2** o **barra espaciadora** cuando un elemento tiene el foco.

##  <a name="getcount"></a>  CVSListBox::GetCount

Recupera el número de cadenas de un control de lista modificable.

```
virtual int GetCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de elementos en el control de lista.

### <a name="remarks"></a>Comentarios

Tenga en cuenta que el recuento es uno mayor que el valor de índice del último elemento porque el índice está basado en cero.

##  <a name="getitemdata"></a>  CVSListBox::GetItemData

Recupera un valor de 32 bits específico de la aplicación que está asociado a un elemento de control de lista modificable.

```
virtual DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento de control de lista modificable.

### <a name="return-value"></a>Valor devuelto

Valor de 32 bits que está asociado al elemento especificado.

### <a name="remarks"></a>Comentarios

Use el método [CVSListBox:: SetItemData](#setitemdata) o [CVSListBox:: AddItem](#additem) para asociar el valor de 32 bits al elemento de control de lista. Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.

##  <a name="getitemtext"></a>  CVSListBox::GetItemText

Recupera el texto de un elemento de control de lista modificable.

```
virtual CString GetItemText(int iIndex) const;
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento de control de lista modificable.

### <a name="return-value"></a>Valor devuelto

Objeto [CString](../../atl-mfc-shared/reference/cstringt-class.md) que contiene el texto del elemento especificado.

### <a name="remarks"></a>Comentarios

##  <a name="getlisthwnd"></a>  CVSListBox::GetListHwnd

Devuelve el identificador del control de vista de lista incrustado actual.

```
virtual HWND GetListHwnd() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del control de vista de lista incrustado.

### <a name="remarks"></a>Comentarios

Utilice este método para recuperar un identificador del control de vista de lista incrustado que `CVSListBox` admite la clase.

##  <a name="getselitem"></a>  CVSListBox::GetSelItem

Recupera el índice de base cero del elemento actualmente seleccionado en un control de lista modificable.

```
virtual int GetSelItem() const;
```

### <a name="return-value"></a>Valor devuelto

Si este método se realiza correctamente, el índice de base cero del elemento seleccionado actualmente; de lo contrario,-1.

### <a name="remarks"></a>Comentarios

##  <a name="removeitem"></a>  CVSListBox::RemoveItem

Quita un elemento de un control de lista modificable.

```
virtual BOOL RemoveItem(int iIndex);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento de control de lista modificable.

### <a name="return-value"></a>Valor devuelto

TRUE si se quita el elemento especificado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

##  <a name="selectitem"></a>  CVSListBox::SelectItem

Selecciona una cadena de control de lista modificable.

```
virtual BOOL SelectItem(int iItem);
```

### <a name="parameters"></a>Parámetros

*iItem*<br/>
de Índice de base cero de un elemento de control de lista modificable.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método selecciona el elemento especificado y, si es necesario, desplaza el elemento en la vista.

##  <a name="setitemdata"></a>  CVSListBox::SetItemData

Asocia un valor de 32 bits específico de la aplicación con un elemento de control de lista modificable.

```
virtual void SetItemData(
    int iIndex,
    DWORD_PTR dwData);
```

### <a name="parameters"></a>Parámetros

*iIndex*<br/>
de Índice de base cero de un elemento de control de lista modificable.

*dwData*<br/>
de Valor de 32 bits. Este valor puede ser un entero específico de la aplicación o un puntero a otros datos.

### <a name="remarks"></a>Comentarios

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)
