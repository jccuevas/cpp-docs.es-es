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
ms.openlocfilehash: 52e992cf021a592198daeddf0a4321fcea487f72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364043"
---
# <a name="cprintdialogex-class"></a>Clase CPrintDialogEx

Encapsula los servicios proporcionados por la hoja de propiedades de Windows Print.

## <a name="syntax"></a>Sintaxis

```
class CPrintDialogEx : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialogEx::CPrintDialogEx](#cprintdialogex)|Construye un objeto `CPrintDialogEx`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialogEx::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora sin mostrar el cuadro de diálogo Imprimir.|
|[CPrintDialogEx::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar selecciones.|
|[CPrintDialogEx::GetCopies](#getcopies)|Recupera el número de copias solicitadas.|
|[CPrintDialogEx::GetDefaults](#getdefaults)|Recupera los valores predeterminados del dispositivo sin mostrar un cuadro de diálogo.|
|[CPrintDialogEx::GetDeviceName](#getdevicename)|Recupera el nombre del dispositivo de impresora seleccionado actualmente.|
|[CPrintDialogEx::GetDevMode](#getdevmode)|Recupera la `DEVMODE` estructura.|
|[CPrintDialogEx::GetDriverName](#getdrivername)|Recupera el nombre del controlador de dispositivo de impresora definido por el sistema.|
|[CPrintDialogEx::GetPortName](#getportname)|Recupera el nombre del puerto de impresora seleccionado actualmente.|
|[CPrintDialogEx::GetPrinterDC](#getprinterdc)|Recupera un identificador en el contexto del dispositivo de impresora.|
|[CPrintDialogEx::PrintAll](#printall)|Determina si se deben imprimir todas las páginas del documento.|
|[CPrintDialogEx::PrintCollate](#printcollate)|Determina si se solicitan copias intercaladas.|
|[CPrintDialogEx::PrintCurrentPage](#printcurrentpage)|Determina si se debe imprimir la página actual del documento.|
|[CPrintDialogEx::PrintRange](#printrange)|Determina si se debe imprimir solo un intervalo de páginas especificado.|
|[CPrintDialogEx::PrintSelection](#printselection)|Determina si se deben imprimir solo los elementos seleccionados actualmente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialogEx::m_pdex](#m_pdex)|Estructura utilizada para `CPrintDialogEx` personalizar un objeto.|

## <a name="remarks"></a>Observaciones

Puede confiar en el marco de trabajo para controlar muchos aspectos del proceso de impresión de la aplicación. Para obtener más información sobre el uso del marco de trabajo para gestionar las tareas de impresión, consulte el artículo [Impresión](../../mfc/printing.md).

Si desea que la aplicación controle la impresión sin la implicación del marco de trabajo, puede usar la `CPrintDialogEx` clase "tal cual" con el constructor proporcionado, o puede derivar su propia clase de cuadro de `CPrintDialogEx` diálogo y escribir un constructor que se adapte a sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como `CCommonDialog`cuadros de diálogo MFC estándar porque se derivan de la clase .

Para utilizar `CPrintDialogEx` un objeto, primero `CPrintDialogEx` cree el objeto mediante el constructor. Una vez construido el cuadro de diálogo, puede establecer o modificar cualquier valor de la [estructura m_pdex](#m_pdex) para inicializar los valores de los controles del cuadro de diálogo. La `m_pdex` estructura es de tipo [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw). Para obtener más información sobre esta estructura, consulte el Windows SDK.

Si no proporciona sus `m_pdex` propios `hDevMode` identificadores para el y `hDevNames` los `GlobalFree` miembros, asegúrese de llamar a la función de Windows para estos identificadores cuando haya terminado con el cuadro de diálogo.

Después de inicializar los controles `DoModal` del cuadro de diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar las opciones de impresión. Cuando `DoModal` se devuelve, puede determinar si el usuario ha seleccionado el botón Aceptar, Aplicar o Cancelar.

Si el usuario ha presionado `CPrintDialogEx`Aceptar, puede utilizar las funciones miembro de 's para recuperar la información introducida por el usuario.

La `CPrintDialogEx::GetDefaults` función miembro es útil para recuperar los valores predeterminados de impresora actuales sin mostrar un cuadro de diálogo. Este método no requiere ninguna interacción del usuario.

Puede usar la `CommDlgExtendedError` función de Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, consulte el Windows SDK.

Para obtener más `CPrintDialogEx`información sobre el uso de , vea [Clases](../../mfc/common-dialog-classes.md)de cuadro de diálogo comunes .

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

## <a name="cprintdialogexcprintdialogex"></a><a name="cprintdialogex"></a>CPrintDialogEx::CPrintDialogEx

Construye una hoja de propiedades de Impresión de Windows.

```
CPrintDialogEx(
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS       | PD_HIDEPRINTTOFILE | PD_NOSELECTION | PD_NOCURRENTPAGE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Una o más marcas se pueden utilizar para personalizar la configuración del cuadro de diálogo, combinado mediante el operador OR bit a bit. Por ejemplo, el indicador PD_ALLPAGES establece el intervalo de impresión predeterminado en todas las páginas del documento. Consulte la estructura [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) en el Windows SDK para obtener más información sobre estas marcas.

*pParentWnd*<br/>
Puntero a la ventana principal o propietaria del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Esta función miembro solo construye el objeto. Utilice `DoModal` la función miembro para mostrar el cuadro de diálogo.

## <a name="cprintdialogexcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialogEx::CreatePrinterDC

Crea un contexto de dispositivo de impresora (DC) a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Manipule el contexto del dispositivo de impresora recién creado.

### <a name="remarks"></a>Observaciones

El controlador de dominio `hDC` devuelto también se almacena en el miembro de [m_pdex](#m_pdex).

Se supone que este controlador de dominio es el controlador de dominio de impresora actual y se deben eliminar cualquier otro controlador de dominio de impresora obtenido anteriormente. Se puede llamar a esta función y utilizar el controlador de dominio resultante, sin mostrar nunca el cuadro de diálogo Imprimir.

## <a name="cprintdialogexdomodal"></a><a name="domodal"></a>CPrintDialogEx::DoModal

Llame a esta función para mostrar la hoja de propiedades de Impresión de Windows y permitir al usuario seleccionar varias opciones de impresión, como el número de copias, el intervalo de páginas y si se deben recopilar copias.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

El valor devuelto INT_PTR es en realidad un Valor HRESULT. Consulte la sección Valores devueltos en [PrintDlgEx](/previous-versions/windows/desktop/legacy/ms646942\(v=vs.85\)) en el Windows SDK.

### <a name="remarks"></a>Observaciones

Si desea inicializar las distintas opciones de `m_pdex` cuadro de diálogo de `DoModal`impresión estableciendo miembros de la estructura, debe hacerlo antes de llamar a , pero después de que se construya el objeto de cuadro de diálogo.

Después `DoModal`de llamar a , puede llamar a otras funciones miembro para recuperar la configuración o la información introducida por el usuario en el cuadro de diálogo.

Si se utiliza la `DoModal`marca PD_RETURNDC al llamar a `hDC` , se devolverá un controlador de dominio de impresora en el miembro de [m_pdex](#m_pdex). Este controlador de dominio debe liberarse con una `CPrintDialogEx`llamada a [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) por el autor de la llamada de .

## <a name="cprintdialogexgetcopies"></a><a name="getcopies"></a>CPrintDialogEx::GetCopies

Llame a esta `DoModal` función después de llamar para recuperar el número de copias solicitadas.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valor devuelto

El número de copias solicitadas.

## <a name="cprintdialogexgetdefaults"></a><a name="getdefaults"></a>CPrintDialogEx::GetDefaults

Llame a esta función para recuperar los valores predeterminados del dispositivo de la impresora predeterminada sin mostrar un cuadro de diálogo.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valor devuelto

TRUESi se realiza correctamente, de lo contrario FALSE.

### <a name="remarks"></a>Observaciones

Crea un contexto de dispositivo de impresora (DC) a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

`GetDefaults`no muestra la hoja de propiedades Imprimir. `hDevNames` En su lugar, `hDevMode` establece los miembros y de [m_pdex](#m_pdex) en identificadores de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) que se inicializan para la impresora predeterminada del sistema. Ambos `hDevNames` `hDevMode` y debe ser `GetDefaults` NULL, o se produce un error.

Si se establece el indicador PD_RETURNDC, `hDevNames` esta `hDevMode` función `m_pdex.hDevNames` `m_pdex.hDevMode`no solo devolverá y (ubicado en `m_pdex.hDC`y ) al autor de la llamada, sino que también devolverá un controlador de dominio de impresora en . Es responsabilidad del autor de la llamada eliminar el controlador de dominio de la `CPrintDialogEx` impresora y llamar a la función [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) de Windows en los identificadores cuando haya terminado con el objeto.

## <a name="cprintdialogexgetdevicename"></a><a name="getdevicename"></a>CPrintDialogEx::GetDeviceName

Llame a esta función después de llamar a [DoModal](#domodal) para recuperar el nombre de la impresora seleccionada actualmente o después de llamar a [GetDefaults](#getdefaults) para recuperar el nombre de la impresora predeterminada.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la impresora seleccionada actualmente.

### <a name="remarks"></a>Observaciones

Utilice un puntero `CString` al `GetDeviceName` objeto devuelto `lpszDeviceName` como valor de en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetdevmode"></a><a name="getdevmode"></a>CPrintDialogEx::GetDevMode

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar información sobre el dispositivo de impresión.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

La estructura de datos [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria tomada por esta estructura con la función [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, que se describe en el Windows SDK.

## <a name="cprintdialogexgetdrivername"></a><a name="getdrivername"></a>CPrintDialogEx::GetDriverName

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del controlador de dispositivo de impresora definido por el sistema.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Especificando `CString` el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Observaciones

Utilice un puntero `CString` al `GetDriverName` objeto devuelto por como el valor de *lpszDriverName* en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cprintdialogexgetportname"></a><a name="getportname"></a>CPrintDialogEx::GetPortName

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del puerto de impresora seleccionado actualmente.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del puerto de impresora seleccionado actualmente.

## <a name="cprintdialogexgetprinterdc"></a><a name="getprinterdc"></a>CPrintDialogEx::GetPrinterDC

Devuelve un identificador al contexto del dispositivo de impresora.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el contexto del dispositivo de impresora.

### <a name="remarks"></a>Observaciones

Debe llamar a la función [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) de Windows para eliminar el contexto del dispositivo cuando haya terminado de usarlo.

## <a name="cprintdialogexm_pdex"></a><a name="m_pdex"></a>CPrintDialogEx::m_pdex

Estructura PRINTDLGEX cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PRINTDLGEX m_pdex;
```

### <a name="remarks"></a>Observaciones

Después de `CPrintDialogEx` construir un `m_pdex` objeto, puede usar para establecer varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro. Para obtener más `m_pdex` información sobre la estructura, consulte [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) en el Windows SDK.

Si modifica `m_pdex` el miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

## <a name="cprintdialogexprintall"></a><a name="printall"></a>CPrintDialogEx::PrintAll

Llame a esta `DoModal` función después de llamar para determinar si se deben imprimir todas las páginas del documento.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se van a imprimir todas las páginas del documento; de lo contrario FALSO.

## <a name="cprintdialogexprintcollate"></a><a name="printcollate"></a>CPrintDialogEx::PrintCollate

Llame a esta `DoModal` función después de llamar para determinar si la impresora debe recopilar todas las copias impresas del documento.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi el usuario selecciona la casilla de verificación intercalar en el cuadro de diálogo; de lo contrario FALSO.

## <a name="cprintdialogexprintcurrentpage"></a><a name="printcurrentpage"></a>CPrintDialogEx::PrintCurrentPage

Llame a esta `DoModal` función después de llamar para determinar si se debe imprimir la página actual en el documento.

```
BOOL PrintCurrentPage() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se selecciona **Imprimir página actual** en el cuadro de diálogo de impresión; de lo contrario FALSO.

## <a name="cprintdialogexprintrange"></a><a name="printrange"></a>CPrintDialogEx::PrintRange

Llame a esta `DoModal` función después de llamar para determinar si se debe imprimir solo un intervalo de páginas en el documento.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi solo se va a imprimir un intervalo de páginas del documento; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

Los intervalos de páginas especificados `nPageRanges`se `nMaxPageRanges`pueden `lpPageRanges` determinar a partir de [m_pdex](#m_pdex) (consulte , y en la estructura [PRINTDLGEX](/windows/win32/api/commdlg/ns-commdlg-printdlgexw) en el Windows SDK).

## <a name="cprintdialogexprintselection"></a><a name="printselection"></a>CPrintDialogEx::PrintSelection

Llame a esta `DoModal` función después de llamar para determinar si se deben imprimir solo los elementos seleccionados actualmente.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi solo se van a imprimir los elementos seleccionados; de lo contrario FALSO.

## <a name="see-also"></a>Consulte también

[Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Estructura CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
