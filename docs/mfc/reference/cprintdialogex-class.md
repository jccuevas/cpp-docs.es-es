---
title: Clase CPrintDialogEx
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
ms.openlocfilehash: 76c3968b20a66e9653fd769339e23ede2a756bbd
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741330"
---
# <a name="cprintdialogex-class"></a>Clase CPrintDialogEx

Encapsula los servicios proporcionados por la hoja de propiedades de impresión de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Construye un objeto `CPrintDialogEx`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora sin mostrar el cuadro de diálogo Imprimir.|
|[CPrintDialogEx::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar selecciones.|
|[CPrintDialogEx::GetCopies](#getcopies)|Recupera el número de copias solicitadas.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Recupera los valores predeterminados del dispositivo sin mostrar un cuadro de diálogo.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Recupera el nombre del dispositivo de impresora seleccionado actualmente.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Recupera la `DEVMODE` estructura.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Recupera el nombre del controlador de dispositivo de impresora definido por el sistema.|
|[CPrintDialogEx::GetPortName](#getportname)|Recupera el nombre del puerto de impresora seleccionado actualmente.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Recupera un identificador para el contexto del dispositivo de impresora.|
|[CPrintDialogEx::PrintAll](#printall)|Determina si se van a imprimir todas las páginas del documento.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Determina si se solicitan las copias intercaladas.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Determina si se va a imprimir la página actual del documento.|
|[CPrintDialogEx::PrintRange](#printrange)|Determina si se va a imprimir solo un intervalo de páginas especificado.|
|[CPrintDialogEx::PrintSelection](#printselection)|Determina si se van a imprimir solo los elementos seleccionados actualmente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Estructura utilizada para personalizar un `CPrintDialogEx` objeto.|

## <a name="remarks"></a>Comentarios

Puede confiar en el marco de trabajo para administrar muchos aspectos del proceso de impresión de la aplicación. Para obtener más información sobre cómo usar el marco de trabajo para controlar las tareas de impresión, vea el artículo [Imprimir](../../mfc/printing.md).

Si desea que la aplicación controle la impresión sin la implicación del marco de trabajo, puede `CPrintDialogEx` usar la clase "tal cual" con el constructor proporcionado o puede derivar su propia clase de `CPrintDialogEx` cuadro de diálogo de y escribir un constructor para satisfacer sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como los cuadros de diálogo de MFC estándar `CCommonDialog`, ya que se derivan de la clase.

Para usar un `CPrintDialogEx` objeto, primero cree el objeto mediante el `CPrintDialogEx` constructor. Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la estructura [m_pdex](#m_pdex) para inicializar los valores de los controles del cuadro de diálogo. La `m_pdex` estructura es de tipo [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw). Para obtener más información sobre esta estructura, vea el Windows SDK.

Si no proporciona sus propios `m_pdex` identificadores en para los `hDevMode` miembros y `hDevNames` , asegúrese de llamar a la función `GlobalFree` de Windows para estos controladores cuando haya terminado con el cuadro de diálogo.

Después de inicializar los controles de cuadro de `DoModal` diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir que el usuario seleccione las opciones de impresión. Cuando `DoModal` devuelve, puede determinar si el usuario seleccionó el botón Aceptar, aplicar o cancelar.

Si el usuario presionó aceptar, puede usar `CPrintDialogEx`las funciones miembro de para recuperar la información introducida por el usuario.

La `CPrintDialogEx::GetDefaults` función miembro es útil para recuperar los valores predeterminados de la impresora actual sin mostrar un cuadro de diálogo. Este método no requiere ninguna interacción del usuario.

Puede usar la función de `CommDlgExtendedError` Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, vea el Windows SDK.

Para obtener más información sobre `CPrintDialogEx`el uso de, vea [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

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

**Encabezado:** afxdlgs. h

##  <a name="cprintdialogex"></a>  CPrintDialogEx::CPrintDialogEx

Crea una hoja de propiedades de impresión de Windows.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Una o varias marcas que puede usar para personalizar la configuración del cuadro de diálogo, combinada mediante el operador bit a bit or. Por ejemplo, la marca PD_ALLPAGES establece el intervalo de impresión predeterminado en todas las páginas del documento. Vea la estructura [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) en el Windows SDK para obtener más información acerca de estas marcas.

*pParentWnd*<br/>
Puntero a la ventana primaria o propietaria del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Esta función miembro solo construye el objeto. Utilice la `DoModal` función miembro para mostrar el cuadro de diálogo.

##  <a name="createprinterdc"></a>  CPrintDialogEx::CreatePrinterDC

Crea un contexto de dispositivo de impresora (DC) a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto de dispositivo de impresora recién creado.

### <a name="remarks"></a>Comentarios

El controlador de dominio devuelto también se `hDC` almacena en el miembro de [m_pdex](#m_pdex).

Se supone que este controlador de dominio es el controlador de dominio de la impresora actual y se deben eliminar todos los controladores de dominio de impresora obtenidos previamente. Se puede llamar a esta función y se usa el controlador de dominio resultante, sin mostrar nunca el cuadro de diálogo Imprimir.

##  <a name="domodal"></a>  CPrintDialogEx::DoModal

Llame a esta función para mostrar la hoja de propiedades impresión de Windows y permitir que el usuario seleccione varias opciones de impresión, como el número de copias, el intervalo de páginas y si se deben intercalar las copias.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

En realidad, el valor devuelto de INT_PTR es HRESULT. Vea la sección valores devueltos de [PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Comentarios

Si desea inicializar las diversas opciones del cuadro de diálogo de impresión estableciendo los `m_pdex` miembros de la estructura, debe hacerlo antes `DoModal`de llamar a, pero después de que se construya el objeto de cuadro de diálogo.

Después de `DoModal`llamar a, puede llamar a otras funciones miembro para recuperar la información de configuración o la entrada del usuario en el cuadro de diálogo.

Si se usa la marca PD_RETURNDC cuando se `DoModal`llama a, se devolverá un controlador `hDC` de dominio de impresora en el miembro de [m_pdex](#m_pdex). Este DC debe liberarse con una llamada a [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) por el autor de la llamada `CPrintDialogEx`de.

##  <a name="getcopies"></a>  CPrintDialogEx::GetCopies

Llame a esta función después `DoModal` de llamar a para recuperar el número de copias solicitadas.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valor devuelto

Número de copias solicitadas.

##  <a name="getdefaults"></a>  CPrintDialogEx::GetDefaults

Llame a esta función para recuperar los valores predeterminados del dispositivo de la impresora predeterminada sin mostrar un cuadro de diálogo.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valor devuelto

TRUE si es correcto; de lo contrario, FALSE.

### <a name="remarks"></a>Comentarios

Crea un contexto de dispositivo de impresora (DC) a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

`GetDefaults`no muestra la hoja de propiedades de impresión. En su lugar, establece los `hDevNames` miembros `hDevMode` y de [m_pdex](#m_pdex) en los identificadores de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) que se inicializan para la impresora predeterminada del sistema. Y deben ser null o `GetDefaults` produce un error. `hDevMode` `hDevNames`

Si se establece la marca PD_RETURNDC, esta función no `hDevNames` solo devolverá `hDevMode` y (se `m_pdex.hDevNames` ubica `m_pdex.hDevMode`en y) al autor de la llamada, sino que también devolverá un controlador de dominio de impresora en `m_pdex.hDC`. Es responsabilidad del autor de la llamada eliminar el controlador de dominio de la impresora y llamar a la función [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) de Windows en los identificadores cuando `CPrintDialogEx` haya terminado con el objeto.

##  <a name="getdevicename"></a>  CPrintDialogEx::GetDeviceName

Llame a esta función después de llamar a [DoModal](#domodal) para recuperar el nombre de la impresora seleccionada actualmente o después de llamar a [GetDefaults](#getdefaults) para recuperar el nombre de la impresora predeterminada.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre de la impresora seleccionada actualmente.

### <a name="remarks"></a>Comentarios

`CString` Use un puntero al objeto devuelto por `GetDeviceName` como el valor de `lpszDeviceName` en una llamada a [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getdevmode"></a>  CPrintDialogEx::GetDevMode

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar información sobre el dispositivo de impresión.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

La estructura de datos [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria tomada por esta estructura con la función [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, que se describe en el Windows SDK.

##  <a name="getdrivername"></a>  CPrintDialogEx::GetDriverName

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del controlador de dispositivo de impresora definido por el sistema.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Que `CString` especifica el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Comentarios

`CString` Use un puntero al objeto devuelto por `GetDriverName` como el valor de *lpszDriverName* en una llamada a [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getportname"></a>  CPrintDialogEx::GetPortName

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del puerto de impresora seleccionado actualmente.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del puerto de impresora seleccionado actualmente.

##  <a name="getprinterdc"></a>  CPrintDialogEx::GetPrinterDC

Devuelve un identificador para el contexto del dispositivo de impresora.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto del dispositivo de impresora.

### <a name="remarks"></a>Comentarios

Debe llamar a la función [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) de Windows para eliminar el contexto de dispositivo cuando termine de usarlo.

##  <a name="m_pdex"></a>  CPrintDialogEx::m_pdex

Estructura PRINTDLGEX cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Comentarios

Después de construir un `CPrintDialogEx` objeto, puede utilizar `m_pdex` para establecer diversos aspectos del cuadro de diálogo antes de llamar a la función miembro [DoModal](#domodal) . Para obtener más información sobre `m_pdex` la estructura, vea [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) en el Windows SDK.

Si modifica el miembro `m_pdex` de datos directamente, invalidará el comportamiento predeterminado.

##  <a name="printall"></a>  CPrintDialogEx::PrintAll

Llame a esta función después `DoModal` de llamar a para determinar si se van a imprimir todas las páginas del documento.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se van a imprimir todas las páginas del documento; en caso contrario, FALSE.

##  <a name="printcollate"></a>  CPrintDialogEx::PrintCollate

Llame a esta función después `DoModal` de llamar a para determinar si la impresora debe intercalar todas las copias impresas del documento.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si el usuario activa la casilla COLLATE en el cuadro de diálogo; en caso contrario, FALSE.

##  <a name="printcurrentpage"></a>  CPrintDialogEx::PrintCurrentPage

Llame a esta función después `DoModal` de llamar a para determinar si se va a imprimir la página actual en el documento.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si la **página Imprimir actual** está seleccionada en el cuadro de diálogo Imprimir; en caso contrario, FALSE.

##  <a name="printrange"></a>  CPrintDialogEx::PrintRange

Llame a esta función después `DoModal` de llamar a para determinar si se va a imprimir solo un intervalo de páginas del documento.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si solo se va a imprimir un intervalo de páginas del documento; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Los intervalos de páginas especificados se pueden determinar a partir de [m_pdex](#m_pdex) (vea `nPageRanges`, `nMaxPageRanges` y `lpPageRanges` en la estructura [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) del Windows SDK).

##  <a name="printselection"></a>  CPrintDialogEx::PrintSelection

Llame a esta función después `DoModal` de llamar a para determinar si se van a imprimir solo los elementos seleccionados actualmente.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si solo se van a imprimir los elementos seleccionados; en caso contrario, FALSE.

## <a name="see-also"></a>Vea también

[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo (estructura)](../../mfc/reference/cprintinfo-structure.md)
