---
title: CMFCKeyMapDialog (Clase)
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
ms.openlocfilehash: 22aa006ce214ca720192bb761e2ff2b35a64fce3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374412"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog (Clase)

La `CMFCKeyMapDialog` clase admite un control que asigna comandos a las teclas del teclado.

## <a name="syntax"></a>Sintaxis

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Construye un objeto `CMFCKeyMapDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCKeyMapDialog::DoModal](#domodal)|Muestra un cuadro de diálogo de asignación de teclado.|

### <a name="protected-methods"></a>Métodos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Llamado por el marco de trabajo para crear una cadena que describe una asignación de claves. De forma predeterminada, la cadena contiene el nombre del comando, las teclas de método abreviado utilizadas y la descripción de la tecla de método abreviado.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Recupera una cadena que contiene una lista de teclas de método abreviado asociadas con el comando especificado.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Llamado por el marco de trabajo antes de que se inserte un nuevo elemento en el control de lista interna que admite el control de asignación de teclado.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Llamado por el marco de trabajo para imprimir el encabezado para el mapa de teclado en una nueva página.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Llamado por el marco de trabajo para imprimir un elemento de asignación de teclado.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Llamado por el marco de trabajo para establecer subtítulos para las columnas en el control de lista interna que admite el control de asignación de teclado.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Llamado por el marco de trabajo cuando un usuario hace clic en el botón **Imprimir.**|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Llamado por el marco de trabajo para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.|

## <a name="remarks"></a>Observaciones

Utilice `CMFCKeyMapDialog` la clase para implementar un cuadro de diálogo de asignación de teclado redimensionable. El cuadro de diálogo utiliza un control de vista de lista para mostrar los métodos abreviados de teclado y sus comandos asociados.

Para usar `CMFCKeyMapDialog` la clase en una aplicación, pase un puntero a `CMFCKeyMapDialog` la ventana de marco principal como parámetro al constructor. A continuación, llame al `DoModal` método para iniciar un cuadro de diálogo modal.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxkeymapdialog.h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog

Construye un objeto `CMFCKeyMapDialog`.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Parámetros

*pWndParentFrame*<br/>
[en] Un puntero a la `CMFCKeyMapDialog` ventana primaria del objeto.

*bEnablePrint*<br/>
[en] TRUESi se puede imprimir la lista de teclas de aceleración; de lo contrario, FALSE. El valor predeterminado es FALSE.

### <a name="remarks"></a>Observaciones

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCKeyMapDialog` cómo construir un objeto de la clase. Este ejemplo forma parte del [ejemplo de demostración](../../overview/visual-cpp-samples.md)de Visual Studio.

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFCKeyMapDialog::DoModal

Muestra un cuadro de diálogo de asignación de teclado.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

Un entero con signo, como IDOK o IDCANCEL, que se pasa al método [CDialog::EndDialog](../../mfc/reference/cdialog-class.md#enddialog) . El método, a su vez, cierra el cuadro de diálogo. Para obtener más información, vea [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Observaciones

El cuadro de diálogo de asignación de teclado le permite seleccionar y asignar teclas de aceleración a varias categorías de comandos. Además, puede copiar las teclas de aceleración seleccionadas y su descripción en el portapapeles.

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFCKeyMapDialog::FormatItem

Llamado por el marco de trabajo para crear una cadena que describe una asignación de claves. De forma predeterminada, la cadena contiene el nombre del comando, las teclas de método abreviado utilizadas y la descripción de la tecla de método abreviado.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Parámetros

*nItem*<br/>
[en] El índice de base cero de un elemento en la lista interna de asignaciones de claves.

### <a name="return-value"></a>Valor devuelto

Objeto `CString` que contiene el texto del elemento con formato.

### <a name="remarks"></a>Observaciones

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys

Recupera un valor de cadena. La cadena contiene una lista de teclas de método abreviado asociadas a un comando especificado.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[en] Un identificador de comando.

### <a name="return-value"></a>Valor devuelto

Una lista delimitada por punto y coma (';') de teclas de método abreviado asociada según el comando especificado.

### <a name="remarks"></a>Observaciones

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem

Llamado por el marco de trabajo antes de que se inserte un nuevo elemento en un control de lista interna que admita el control de asignación de teclado.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Parámetros

*pButton*<br/>
[en] Puntero a un botón de barra de herramientas que se utiliza para asignar una combinación de teclas de teclado a un nombre de comando y una descripción. El elemento de mapa de claves se almacena en un control de lista interno.

*nItem*<br/>
[en] Un índice de base cero que especifica dónde insertar el nuevo elemento de mapa de claves en el control de lista interno.

### <a name="remarks"></a>Observaciones

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader

Llamado por el marco de trabajo para imprimir el encabezado para el mapa de teclado en una nueva página.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
[en] El contexto del dispositivo para la impresora.

*nPage*<br/>
[en] El número de página que se va a imprimir.

*Cx*<br/>
[en] El desplazamiento horizontal del encabezado, en píxeles.

### <a name="return-value"></a>Valor devuelto

Si se realiza correctamente, la altura del texto impreso. Para obtener más información, consulte la sección Valor devuelto de [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Observaciones

El marco de trabajo utiliza este método para imprimir el mapa del teclado. De forma predeterminada, este método imprime el número de página, el nombre de la aplicación y el título del cuadro de diálogo.

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem

Llamado por el marco de trabajo para imprimir un elemento de asignación de teclado.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
[en] El contexto del dispositivo de la impresora.

*nItem*<br/>
[en] El índice de base cero del elemento que se va a imprimir.

*y y*<br/>
[en] El desplazamiento vertical entre la parte superior de la página y la posición del elemento.

*Cx*<br/>
[en] El desplazamiento horizontal entre la izquierda de la página y la posición del elemento.

*bCalcHeight*<br/>
[en] TRUE para calcular la mejor altura para el elemento de impresión; FALSE para truncar el elemento de impresión de modo que se ajuste al espacio predeterminado.

### <a name="return-value"></a>Valor devuelto

La altura del elemento impreso.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a este método para imprimir un elemento de cuadro de diálogo de mapa de claves. De forma predeterminada, este método imprime el nombre del comando, las teclas de método abreviado y la descripción del comando del elemento.

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns

Llamado por el marco de trabajo para establecer subtítulos para las columnas en el control de lista interna que admite el control de asignación de teclado.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Observaciones

De forma predeterminada, este método obtiene los subtítulos de las columnas de tres recursos. El título de columna de comando es de IDS_AFXBARRES_COMMAND, el título de columna de clave es de IDS_AFXBARRES_KEYS y el título de columna de descripción es de IDS_AFXBARRES_DESCRIPTION.

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap

Llamado por el marco de trabajo cuando un usuario hace clic en el botón **Imprimir.**

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Observaciones

El `PrintKeyMap` método imprime el mapa de claves. Inicia un nuevo trabajo de impresión y, a continuación, llama repetidamente a la [CMFCKeyMapDialog::OnPrintHeader](#onprintheader) y [CMFCKeyMapDialog::OnPrintItem](#onprintitem) métodos hasta que se imprimen todas las asignaciones de claves.

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth

Llamado por el marco de trabajo para establecer el ancho de las columnas en el control de lista interna que admite el control de asignación de teclado.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Observaciones

Este método establece las columnas del control de lista interna en anchos predeterminados. En primer lugar, se calcula el ancho de la columna de teclas de método abreviado. A continuación, un tercio del ancho restante se asigna a la columna de comandos y los dos tercios restantes se asignan a la columna de descripción.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[Clase CKeyboardManager](../../mfc/reference/ckeyboardmanager-class.md)
