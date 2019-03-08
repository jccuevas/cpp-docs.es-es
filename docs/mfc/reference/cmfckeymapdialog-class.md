---
title: CMFCKeyMapDialog (clase)
ms.date: 11/04/2016
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
ms.openlocfilehash: 94c6968d2f534ed0b6d247420e67910ecf906b05
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57294608"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog (clase)

La `CMFCKeyMapDialog` clase es compatible con un control que asigna comandos a teclas del teclado.

## <a name="syntax"></a>Sintaxis

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Construye un objeto `CMFCKeyMapDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CMFCKeyMapDialog::DoModal](#domodal)|Muestra un cuadro de diálogo de asignación de teclado.|

### <a name="protected-methods"></a>Métodos protegidos

|Name|Descripción|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Lo llama el marco de trabajo para generar una cadena que describe la asignación de claves. De forma predeterminada, la cadena contiene el nombre de comando, usa las teclas de método abreviado y la descripción de la clave de acceso directo.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Recupera una cadena que contiene una lista de teclas de método abreviado asociada con el comando especificado.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Lo llama el marco de trabajo antes de que se inserta un nuevo elemento en el control de lista interna que admite el control de asignación de teclado.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Lo llama el marco de trabajo para imprimir el encabezado para la asignación de teclado en una página nueva.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Lo llama el marco de trabajo para imprimir un elemento de asignación de teclado.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Lo llama el marco de trabajo para establecer los títulos de las columnas en el control de lista interna que admite el control de asignación de teclado.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Lo llama el marco cuando un usuario hace clic en el **impresión** botón.|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Lo llama el marco de trabajo para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.|

## <a name="remarks"></a>Comentarios

Use la `CMFCKeyMapDialog` clase para implementar un cuadro de diálogo de asignación de teclado de tamaño ajustable. El cuadro de diálogo, usa un control de vista de lista para mostrar los métodos abreviados de teclado y sus comandos asociados.

Para usar el `CMFCKeyMapDialog` de clases en una aplicación, pase un puntero a la ventana de marco principal como un parámetro a la `CMFCKeyMapDialog` constructor. A continuación, llame a la `DoModal` método para iniciar un cuadro de diálogo modal.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxkeymapdialog.h

##  <a name="cmfckeymapdialog"></a>  CMFCKeyMapDialog::CMFCKeyMapDialog

Construye un objeto `CMFCKeyMapDialog`.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Parámetros

*pWndParentFrame*<br/>
[in] Un puntero a la ventana primaria de la `CMFCKeyMapDialog` objeto.

*bEnablePrint*<br/>
[in] TRUE si se puede imprimir la lista de teclas de aceleración; en caso contrario, FALSE. El valor predeterminado es FALSE.

### <a name="remarks"></a>Comentarios

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto de la `CMFCKeyMapDialog` clase. Este ejemplo forma parte de la [ejemplo de demostración de Visual Studio](../../visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

##  <a name="domodal"></a>  CMFCKeyMapDialog::DoModal

Muestra un cuadro de diálogo de asignación de teclado.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Un entero con signo, como IDOK o IDCANCEL, que se pasa a la [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) método. El método, a su vez, cierra el cuadro de diálogo. Para obtener más información, consulte [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Comentarios

El cuadro de diálogo de asignación de teclado permite seleccionar y asignar teclas de aceleración a distintas categorías de comandos. Además, puede copiar las teclas de aceleración seleccionado y su descripción en el Portapapeles.

##  <a name="formatitem"></a>  CMFCKeyMapDialog::FormatItem

Lo llama el marco de trabajo para generar una cadena que describe la asignación de claves. De forma predeterminada, la cadena contiene el nombre de comando, usa las teclas de método abreviado y la descripción de la clave de acceso directo.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
[in] Índice de base cero de un elemento de la lista interna de asignaciones de clave.

### <a name="return-value"></a>Valor devuelto

Un `CString` objeto que contiene el texto del elemento con formato.

### <a name="remarks"></a>Comentarios

##  <a name="getcommandkeys"></a>  CMFCKeyMapDialog::GetCommandKeys

Recupera un valor de cadena. La cadena contiene una lista de teclas de método abreviado asociadas a un comando especificado.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[in] Un identificador de comando.

### <a name="return-value"></a>Valor devuelto

Delimitado por un punto y coma (';') lista de teclas de método abreviado que está asociado con el comando especificado.

### <a name="remarks"></a>Comentarios

##  <a name="oninsertitem"></a>  CMFCKeyMapDialog::OnInsertItem

Lo llama el marco de trabajo antes de que se inserta un nuevo elemento en un control de lista interna que admite el control de asignación de teclado.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
[in] Un puntero a un botón de barra de herramientas que se utiliza para asignar una combinación de teclas del teclado para un nombre de comando y una descripción. El elemento de mapa de claves se almacena en un control de lista interna.

*nItem*<br/>
[in] Índice de base cero que especifica dónde se va a insertar el nuevo elemento de mapa de claves en el control de lista interna.

### <a name="remarks"></a>Comentarios

##  <a name="onprintheader"></a>  CMFCKeyMapDialog::OnPrintHeader

Lo llama el marco de trabajo para imprimir el encabezado para la asignación de teclado en una página nueva.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
[in] El contexto de dispositivo para la impresora.

*nPage*<br/>
[in] El número de página para imprimir.

*cx*<br/>
[in] El desplazamiento horizontal del encabezado, en píxeles.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, el alto del texto impreso. Para obtener más información, vea la sección de valor devuelto de [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Comentarios

El marco de trabajo usa este método para imprimir el mapa de teclado. De forma predeterminada, este método imprime el número de página, el nombre de la aplicación y el título del cuadro de diálogo.

##  <a name="onprintitem"></a>  CMFCKeyMapDialog::OnPrintItem

Lo llama el marco de trabajo para imprimir un elemento de asignación de teclado.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
[in] El contexto de dispositivo de la impresora.

*nItem*<br/>
[in] Índice de base cero del elemento que se va a imprimir.

*y*<br/>
[in] El desplazamiento vertical entre la parte superior de la página y la posición del elemento.

*cx*<br/>
[in] El desplazamiento horizontal entre la izquierda de la página y la posición del elemento.

*bCalcHeight*<br/>
[in] TRUE para calcular el alto mejor para el elemento de impresión; FALSE para truncar el elemento de impresión para que se ajuste el espacio predeterminado.

### <a name="return-value"></a>Valor devuelto

El alto del elemento impreso.

### <a name="remarks"></a>Comentarios

El marco llama a este método para imprimir un elemento del cuadro de diálogo de mapa de claves. De forma predeterminada, este método imprime el nombre de comando del elemento, teclas de método abreviado y descripción del comando.

##  <a name="onsetcolumns"></a>  CMFCKeyMapDialog::OnSetColumns

Lo llama el marco de trabajo para establecer los títulos de las columnas en el control de lista interna que admite el control de asignación de teclado.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Comentarios

De forma predeterminada, este método obtiene los títulos de las columnas de tres recursos. El título de la columna comando proviene IDS_AFXBARRES_COMMAND, el título de columna de clave es de IDS_AFXBARRES_KEYS y el título de la columna descripción proviene IDS_AFXBARRES_DESCRIPTION.

##  <a name="printkeymap"></a>  CMFCKeyMapDialog::PrintKeyMap

Lo llama el marco cuando un usuario hace clic en el **impresión** botón.

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Comentarios

El `PrintKeyMap` método imprime el mapa de claves. Se inicia un nuevo trabajo de impresión y, a continuación, se llama repetidamente el [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) y [CMFCKeyMapDialog::OnPrintItem](#onprintitem) métodos hasta que se imprimen todas las asignaciones de clave.

##  <a name="setcolumnswidth"></a>  CMFCKeyMapDialog::SetColumnsWidth

Lo llama el marco de trabajo para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Comentarios

Este método establece la lista interna columnas del control para los anchos de forma predeterminada. En primer lugar, se calcula el ancho de la columna de las teclas de método abreviado. A continuación, un tercio del ancho restante se asigna a la columna de comando y los dos tercios restantes se asigna a la columna Descripción.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager (clase)](../../mfc/reference/ckeyboardmanager-class.md)
