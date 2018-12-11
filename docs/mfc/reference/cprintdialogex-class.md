---
title: CPrintDialogEx (clase)
ms.date: 11/04/2016
f1_keywords:
- CPrintDialogEx
- AFXDLGS/CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CPrintDialogEx
- AFXDLGS/CPrintDialogEx::CreatePrinterDC
- AFXDLGS/CPrintDialogEx::DoModal
- AFXDLGS/CPrintDialogEx::GetCopies
- AFXDLGS/CPrintDialogEx::GetDefaults
- AFXDLGS/CPrintDialogEx::GetDeviceName
- AFXDLGS/CPrintDialogEx::GetDevMode
- AFXDLGS/CPrintDialogEx::GetDriverName
- AFXDLGS/CPrintDialogEx::GetPortName
- AFXDLGS/CPrintDialogEx::GetPrinterDC
- AFXDLGS/CPrintDialogEx::PrintAll
- AFXDLGS/CPrintDialogEx::PrintCollate
- AFXDLGS/CPrintDialogEx::PrintCurrentPage
- AFXDLGS/CPrintDialogEx::PrintRange
- AFXDLGS/CPrintDialogEx::PrintSelection
- AFXDLGS/CPrintDialogEx::m_pdex
helpviewer_keywords:
- CPrintDialogEx [MFC], CPrintDialogEx
- CPrintDialogEx [MFC], CreatePrinterDC
- CPrintDialogEx [MFC], DoModal
- CPrintDialogEx [MFC], GetCopies
- CPrintDialogEx [MFC], GetDefaults
- CPrintDialogEx [MFC], GetDeviceName
- CPrintDialogEx [MFC], GetDevMode
- CPrintDialogEx [MFC], GetDriverName
- CPrintDialogEx [MFC], GetPortName
- CPrintDialogEx [MFC], GetPrinterDC
- CPrintDialogEx [MFC], PrintAll
- CPrintDialogEx [MFC], PrintCollate
- CPrintDialogEx [MFC], PrintCurrentPage
- CPrintDialogEx [MFC], PrintRange
- CPrintDialogEx [MFC], PrintSelection
- CPrintDialogEx [MFC], m_pdex
ms.assetid: 1d506703-ee1c-44cc-b4ce-4e778fec26b8
ms.openlocfilehash: fb88cc39ddaffe51b80484bbe8460507a1d0aecb
ms.sourcegitcommit: 975098222db3e8b297607cecaa1f504570a11799
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "53178452"
---
# <a name="cprintdialogex-class"></a>CPrintDialogEx (clase)

Encapsula los servicios proporcionados por la hoja de propiedades de impresión de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Construye un objeto `CPrintDialogEx`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora sin mostrar el cuadro de diálogo Imprimir.|
|[CPrintDialogEx::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar selecciones.|
|[CPrintDialogEx::GetCopies](#getcopies)|Recupera el número de copias solicitadas.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Recupera los valores predeterminados del dispositivo sin mostrar un cuadro de diálogo.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Recupera el nombre del dispositivo de impresora actualmente seleccionada.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Recupera el `DEVMODE` estructura.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Recupera el nombre del controlador del dispositivo de impresora definido por el sistema.|
|[CPrintDialogEx::GetPortName](#getportname)|Recupera el nombre del puerto de impresora actualmente seleccionada.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Recupera un identificador para el contexto de dispositivo de impresora.|
|[CPrintDialogEx::PrintAll](#printall)|Determina si se va a imprimir todas las páginas del documento.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Determina si se intercalan copias se solicitan.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Determina si se va a imprimir la página actual del documento.|
|[CPrintDialogEx::PrintRange](#printrange)|Determina si se imprime sólo un intervalo de páginas especificado.|
|[CPrintDialogEx::PrintSelection](#printselection)|Determina si se imprime sólo los elementos seleccionados actualmente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Una estructura utilizada para personalizar un `CPrintDialogEx` objeto.|

## <a name="remarks"></a>Comentarios

Puede confiar en el marco de trabajo para controlar muchos aspectos del proceso de impresión de la aplicación. Para obtener más información sobre cómo usar el marco de trabajo para controlar las tareas de impresión, consulte el artículo [impresión](../../mfc/printing.md).

Si desea que la aplicación para controlar la impresión sin la participación de .NET framework, puede usar el `CPrintDialogEx` clase "tal cual" con el constructor proporcionado, o puede derivar su propia clase de cuadro de diálogo de `CPrintDialogEx` y escribir un constructor para satisfacer sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como cuadros de diálogo MFC estándar, ya que se deriven de la clase `CCommonDialog`.

Para usar un `CPrintDialogEx` , primero cree el objeto con el `CPrintDialogEx` constructor. Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la [m_pdex](#m_pdex) estructura para inicializar los valores de los controles del cuadro de diálogo. El `m_pdex` estructura es de tipo [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa). Para obtener más información sobre esta estructura, consulte el SDK de Windows.

Si no proporciona sus propios controladores en `m_pdex` para el `hDevMode` y `hDevNames` miembros, no olvide llamar a la función de Windows `GlobalFree` para estos identificadores cuando haya terminado con el cuadro de diálogo.

Después de inicializar los controles de cuadro de diálogo, llame a la `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar las opciones de impresión. Cuando `DoModal` devuelve, puede determinar si el usuario seleccionó el botón Aceptar, aplicar o Cancelar.

Si el usuario presionó Aceptar, puede usar `CPrintDialogEx`de funciones de miembro para recuperar la información de entrada por el usuario.

El `CPrintDialogEx::GetDefaults` función miembro es útil para recuperar los valores predeterminados de impresora actuales sin mostrar un cuadro de diálogo. Este método requiere ninguna interacción del usuario.

Puede usar el Windows `CommDlgExtendedError` función para determinar si se produjo un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, consulte el SDK de Windows.

Para obtener más información sobre el uso de `CPrintDialogEx`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`IObjectWithSite`

`IPrintDialogCallback`

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialogEx`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

Construye una hoja de propiedades de impresión de Windows.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Uno o más marcadores que puede usar para personalizar la configuración del cuadro de diálogo combinada mediante el operador OR bit a bit. Por ejemplo, la marca PD_ALLPAGES establece el intervalo de impresión predeterminada para todas las páginas del documento. Consulte la [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) estructura en el SDK de Windows para obtener más información sobre estas marcas.

*pParentWnd*<br/>
Un puntero a la ventana de principal o propietaria del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Esta función miembro solo construye el objeto. Use el `DoModal` función miembro para mostrar el cuadro de diálogo.

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

Crea un contexto de dispositivo (DC) de impresora desde la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) y [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) estructuras.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto de dispositivo de impresora recién creado.

### <a name="remarks"></a>Comentarios

El controlador de dominio devuelto se almacena también en el `hDC` miembro de [m_pdex](#m_pdex).

Este controlador de dominio se supone que el controlador de dominio de la impresora actual y cualquier otra impresora que se deben eliminar los controladores de dominio ha obtenido anteriormente. Se puede llamar a esta función y utiliza el controlador de dominio resultante, sin mostrar el cuadro de diálogo Imprimir de alguna vez.

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

Llame a esta función para mostrar la hoja de propiedades de impresión de Windows y permitir al usuario seleccionar diversas opciones de impresión, como el número de copias, el intervalo de páginas, y si deben estar intercaladas copias.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

El INT_PTR valor devuelto es realmente un HRESULT. Vea la sección valores devolver en [PrintDlgEx](https://msdn.microsoft.com/library/windows/desktop/ms646942) en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Si desea inicializar las distintas opciones de diálogo de impresión estableciendo los miembros de la `m_pdex` estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.

Después de llamar a `DoModal`, se puede llamar a otra funciones miembro para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.

Si se utiliza la marca PD_RETURNDC al llamar a `DoModal`, se devolverá un DC de impresora en el `hDC` miembro de [m_pdex](#m_pdex). Este controlador de dominio se debe liberar con una llamada a [DeleteObject](/windows/desktop/api/wingdi/nf-wingdi-deletedc) por el llamador de `CPrintDialogEx`.

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

Llame a esta función después de llamar a `DoModal` para recuperar el número de copias que se solicita.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valor devuelto

El número de copias que se solicita.

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

Llame a esta función para recuperar los valores predeterminados de dispositivo de la impresora predeterminada sin mostrar un cuadro de diálogo.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valor devuelto

TRUE si se realizó correctamente, de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Crea un contexto de dispositivo (DC) de impresora desde la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) y [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) estructuras.

`GetDefaults` no se muestra la hoja de propiedades de impresión. En su lugar, Establece la `hDevNames` y `hDevMode` los miembros de [m_pdex](#m_pdex) a identificadores para el [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) y [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) estructuras que se inicializan para el impresora predeterminada del sistema. Ambos `hDevNames` y `hDevMode` debe ser NULL, o `GetDefaults` se produce un error.

Si se establece la marca PD_RETURNDC, esta función no solo devolverá `hDevNames` y `hDevMode` (ubicado en `m_pdex.hDevNames` y `m_pdex.hDevMode`) al llamador, pero también devolverá un DC de impresora en `m_pdex.hDC`. Es responsabilidad del llamador para eliminar la impresora DC y llamar a la Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) función en los controladores cuando haya terminado con el `CPrintDialogEx` objeto.

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

Llame a esta función después de llamar a [DoModal](#domodal) para recuperar el nombre de la impresora seleccionada, o después de llamar a [GetDefaults](#getdefaults) para recuperar el nombre de la impresora predeterminada.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la impresora seleccionada actualmente.

### <a name="remarks"></a>Comentarios

Utilice un puntero a la `CString` objeto devuelto por `GetDeviceName` como el valor de `lpszDeviceName` en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar información sobre el dispositivo de impresión.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

El [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) estructuras de datos que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria usada por esta estructura con el Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) función, como se describe en el SDK de Windows.

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del controlador del dispositivo de impresora definido por el sistema.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Un `CString` especificando el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Comentarios

Utilice un puntero a la `CString` objeto devuelto por `GetDriverName` como el valor de *lpszDriverName* en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del puerto de impresora actualmente seleccionada.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del puerto de impresora actualmente seleccionada.

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

Devuelve un identificador para el contexto de dispositivo de impresora.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto de dispositivo de impresora.

### <a name="remarks"></a>Comentarios

Debe llamar a la Windows [DeleteObject](/windows/desktop/api/wingdi/nf-wingdi-deletedc) función para eliminar el contexto de dispositivo cuando haya terminado con él.

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

Una estructura PRINTDLGEX cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Comentarios

Después de crear un `CPrintDialogEx` objeto, puede usar `m_pdex` para establecer varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro. Para obtener más información sobre la `m_pdex` estructura, vea [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) en el SDK de Windows.

Si modifica el `m_pdex` miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

Llame a esta función después de llamar a `DoModal` para determinar si se va a imprimir todas las páginas del documento.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valor devuelto

Es TRUE si todas las páginas del documento se imprimirán; en caso contrario, FALSE.

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

Llame a esta función después de llamar a `DoModal` para determinar si la impresora debe intercalar todas las copias del documento.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el usuario selecciona la casilla Intercalar el cuadro de diálogo. en caso contrario, FALSE.

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

Llame a esta función después de llamar a `DoModal` para determinar si se debe imprimir la página actual en el documento.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si **Imprimir página actual** está seleccionado en el cuadro de diálogo de impresión; de lo contrario, FALSE.

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

Llame a esta función después de llamar a `DoModal` para determinar si se debe imprimir sólo un intervalo de páginas del documento.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si solo un intervalo de páginas en el documento se imprimirá; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Los intervalos de páginas especificado se pueden determinar desde [m_pdex](#m_pdex) (consulte `nPageRanges`, `nMaxPageRanges`, y `lpPageRanges` en el [PRINTDLGEX](/windows/desktop/api/commdlg/ns-commdlg-tagpdexa) estructura en el SDK de Windows).

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

Llame a esta función después de llamar a `DoModal` para determinar si se debe imprimir sólo los elementos seleccionados actualmente.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si solo los elementos seleccionados se imprimirá; en caso contrario, FALSE.

## <a name="see-also"></a>Vea también

[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo (estructura)](../../mfc/reference/cprintinfo-structure.md)
