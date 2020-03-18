---
title: Clase CPrintDialog
ms.date: 11/04/2016
f1_keywords:
- CPrintDialog
- AFXDLGS/CPrintDialog
- AFXDLGS/CPrintDialog::CPrintDialog
- AFXDLGS/CPrintDialog::CreatePrinterDC
- AFXDLGS/CPrintDialog::DoModal
- AFXDLGS/CPrintDialog::GetCopies
- AFXDLGS/CPrintDialog::GetDefaults
- AFXDLGS/CPrintDialog::GetDeviceName
- AFXDLGS/CPrintDialog::GetDevMode
- AFXDLGS/CPrintDialog::GetDriverName
- AFXDLGS/CPrintDialog::GetFromPage
- AFXDLGS/CPrintDialog::GetPortName
- AFXDLGS/CPrintDialog::GetPrinterDC
- AFXDLGS/CPrintDialog::GetToPage
- AFXDLGS/CPrintDialog::PrintAll
- AFXDLGS/CPrintDialog::PrintCollate
- AFXDLGS/CPrintDialog::PrintRange
- AFXDLGS/CPrintDialog::PrintSelection
- AFXDLGS/CPrintDialog::m_pd
helpviewer_keywords:
- CPrintDialog [MFC], CPrintDialog
- CPrintDialog [MFC], CreatePrinterDC
- CPrintDialog [MFC], DoModal
- CPrintDialog [MFC], GetCopies
- CPrintDialog [MFC], GetDefaults
- CPrintDialog [MFC], GetDeviceName
- CPrintDialog [MFC], GetDevMode
- CPrintDialog [MFC], GetDriverName
- CPrintDialog [MFC], GetFromPage
- CPrintDialog [MFC], GetPortName
- CPrintDialog [MFC], GetPrinterDC
- CPrintDialog [MFC], GetToPage
- CPrintDialog [MFC], PrintAll
- CPrintDialog [MFC], PrintCollate
- CPrintDialog [MFC], PrintRange
- CPrintDialog [MFC], PrintSelection
- CPrintDialog [MFC], m_pd
ms.assetid: 5bdb2424-adf8-433d-a97c-df11a83bc4e4
ms.openlocfilehash: ccc673d665d6d5beb92f398b21e6ffd313a58fc9
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426532"
---
# <a name="cprintdialog-class"></a>Clase CPrintDialog

Encapsula los servicios proporcionados por el cuadro de diálogo común de Windows para imprimir.

## <a name="syntax"></a>Sintaxis

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Construye un objeto `CPrintDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora sin mostrar el cuadro de diálogo Imprimir.|
|[CPrintDialog::D oModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[CPrintDialog::GetCopies](#getcopies)|Recupera el número de copias solicitadas.|
|[CPrintDialog::GetDefaults](#getdefaults)|Recupera los valores predeterminados del dispositivo sin mostrar un cuadro de diálogo.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Recupera el nombre del dispositivo de impresora seleccionado actualmente.|
|[CPrintDialog::GetDevMode](#getdevmode)|Recupera la estructura de `DEVMODE`.|
|[CPrintDialog:: GetDriverName](#getdrivername)|Recupera el nombre del controlador de impresora seleccionado actualmente.|
|[CPrintDialog::GetFromPage](#getfrompage)|Recupera la página de inicio del intervalo de impresión.|
|[CPrintDialog::GetPortName](#getportname)|Recupera el nombre del puerto de impresora seleccionado actualmente.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Recupera un identificador para el contexto del dispositivo de impresora.|
|[CPrintDialog::GetToPage](#gettopage)|Recupera la página final del intervalo de impresión.|
|[CPrintDialog::P rintAll](#printall)|Determina si se van a imprimir todas las páginas del documento.|
|[CPrintDialog::P rintCollate](#printcollate)|Determina si se solicitan las copias intercaladas.|
|[CPrintDialog::P rintRange](#printrange)|Determina si se va a imprimir solo un intervalo de páginas especificado.|
|[CPrintDialog::P rintSelection](#printselection)|Determina si se van a imprimir solo los elementos seleccionados actualmente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialog:: m_pd](#m_pd)|Estructura utilizada para personalizar un objeto de `CPrintDialog`.|

## <a name="remarks"></a>Observaciones

Los cuadros de diálogo de impresión comunes proporcionan una manera sencilla de implementar cuadros de diálogo de configuración de impresión e impresión de una manera coherente con los estándares de Windows.

> [!NOTE]
>  La clase `CPrintDialogEx` encapsula los servicios proporcionados por la hoja de propiedades de impresión de Windows. Para obtener más información, consulte la información general de [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) .

la funcionalidad de `CPrintDialog`se sustituye por la de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), que está diseñada para proporcionarle un cuadro de diálogo común para la configuración de impresión y la página.

Puede confiar en el marco de trabajo para administrar muchos aspectos del proceso de impresión de la aplicación. En este caso, el marco de trabajo muestra automáticamente el cuadro de diálogo común de Windows para imprimir. También puede tener la impresión de control de marco para la aplicación, pero debe reemplazar el cuadro de diálogo de impresión común por su propio cuadro de diálogo de impresión. Para obtener más información sobre cómo usar el marco de trabajo para controlar las tareas de impresión, vea el artículo [Imprimir](../../mfc/printing.md).

Si desea que la aplicación controle la impresión sin la implicación del marco de trabajo, puede usar la `CPrintDialog` clase "tal cual" con el constructor proporcionado o puede derivar su propia clase de cuadro de diálogo de `CPrintDialog` y escribir un constructor para que se adapte a sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como los cuadros de diálogo de MFC estándar, ya que se derivan de la clase `CCommonDialog`.

Para usar un objeto `CPrintDialog`, primero debe crear el objeto con el constructor `CPrintDialog`. Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la estructura [m_pd](#m_pd) para inicializar los valores de los controles del cuadro de diálogo. La estructura `m_pd` es de tipo [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga). Para obtener más información sobre esta estructura, vea el Windows SDK.

Si no proporciona sus propios identificadores en `m_pd` para los miembros `hDevMode` y `hDevNames`, asegúrese de llamar a la función de Windows `GlobalFree` para estos controladores cuando haya terminado con el cuadro de diálogo. Cuando se usa la implementación de instalación de impresión del marco de trabajo proporcionada por `CWinApp::OnFilePrintSetup`, no es necesario liberar estos identificadores. Los identificadores se mantienen mediante `CWinApp` y se liberan en el destructor del `CWinApp`. Solo es necesario liberar estos identificadores cuando se usa `CPrintDialog` independiente.

Después de inicializar los controles de cuadro de diálogo, llame a la función miembro `DoModal` para mostrar el cuadro de diálogo y permitir que el usuario seleccione las opciones de impresión. `DoModal` devuelve si el usuario seleccionó el botón Aceptar (IDOK) o cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede usar una de las funciones miembro de `CPrintDialog`para recuperar la información introducida por el usuario.

La función miembro `CPrintDialog::GetDefaults` es útil para recuperar los valores predeterminados de la impresora actual sin mostrar un cuadro de diálogo. Esta función miembro no requiere ninguna interacción del usuario.

Puede usar la función `CommDlgExtendedError` de Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, vea el Windows SDK.

`CPrintDialog` se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3,1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase de `CPrintDialog`, proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base. No es necesaria la personalización de la función de enlace.

Para procesar el mismo mensaje de forma distinta en función de si el cuadro de diálogo es imprimir o Configurar impresión, debe derivar una clase para cada cuadro de diálogo. También debe invalidar la función `AttachOnSetup` de Windows, que controla la creación de un nuevo cuadro de diálogo cuando se selecciona el botón Configurar impresión en un cuadro de diálogo Imprimir.

Para obtener más información sobre el uso de `CPrintDialog`, vea [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs. h

##  <a name="cprintdialog"></a>CPrintDialog::CPrintDialog

Construye un objeto de cuadro de diálogo de instalación de impresión o impresión de Windows.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*bPrintSetupOnly*<br/>
Especifica si se muestra el cuadro de diálogo de impresión estándar de Windows o el cuadro de diálogo de configuración de impresión. Establezca este parámetro en TRUE para mostrar el cuadro de diálogo Configuración de impresión estándar de Windows. Establézcalo en FALSE para mostrar el cuadro de diálogo Imprimir de Windows. Si *bPrintSetupOnly* es false, el botón de opción de configuración de impresión sigue mostrándose en el cuadro de diálogo Imprimir.

*dwFlags*<br/>
Una o varias marcas que puede usar para personalizar la configuración del cuadro de diálogo, combinada mediante el operador bit a bit or. Por ejemplo, la marca PD_ALLPAGES establece el intervalo de impresión predeterminado en todas las páginas del documento. Vea la estructura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) en el Windows SDK para obtener más información acerca de estas marcas.

*pParentWnd*<br/>
Puntero a la ventana primaria o propietaria del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Esta función miembro solo construye el objeto. Utilice la función miembro `DoModal` para mostrar el cuadro de diálogo.

Tenga en cuenta que al llamar al constructor con *bPrintSetupOnly* establecido en false, se usa automáticamente la marca PD_RETURNDC. Después de llamar a `DoModal`, `GetDefaults`o `GetPrinterDC`, se devolverá un controlador de dominio de impresora en `m_pd.hDC`. Este DC debe liberarse con una llamada a [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) por el autor de la llamada de `CPrintDialog`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC

Crea un contexto de dispositivo de impresora (DC) a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto de dispositivo de impresora recién creado.

### <a name="remarks"></a>Observaciones

Se supone que este controlador de dominio es el controlador de dominio de la impresora actual y que el usuario debe eliminar cualquier otro DC de impresora obtenido previamente. Se puede llamar a esta función y se usa el controlador de dominio resultante, sin mostrar nunca el cuadro de diálogo Imprimir.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>CPrintDialog::D oModal

Muestra el cuadro de diálogo de impresión común de Windows y permite al usuario seleccionar diversas opciones de impresión, como el número de copias, el intervalo de páginas y si se deben intercalar las copias.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK y IDCANCEL son constantes que indican si el usuario seleccionó el botón Aceptar o cancelar.

### <a name="remarks"></a>Observaciones

Si desea inicializar las diversas opciones del cuadro de diálogo de impresión estableciendo los miembros de la estructura `m_pd`, debe hacerlo antes de llamar a `DoModal`, pero después de que se construya el objeto de cuadro de diálogo.

Después de llamar a `DoModal`, puede llamar a otras funciones miembro para recuperar la información de configuración o la entrada del usuario en el cuadro de diálogo.

Tenga en cuenta que al llamar al constructor con *bPrintSetupOnly* establecido en false, se usa automáticamente la marca PD_RETURNDC. Después de llamar a `DoModal`, `GetDefaults`o `GetPrinterDC`, se devolverá un controlador de dominio de impresora en `m_pd.hDC`. Este DC debe liberarse con una llamada a [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) por el autor de la llamada de `CPrintDialog`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>CPrintDialog::GetCopies

Recupera el número de copias solicitadas.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valor devuelto

Número de copias solicitadas.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a `DoModal` para recuperar el número de copias solicitadas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdefaults"></a>CPrintDialog::GetDefaults

Recupera los valores predeterminados del dispositivo de la impresora predeterminada sin mostrar un cuadro de diálogo.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Los valores recuperados se colocan en la estructura `m_pd`.

En algunos casos, una llamada a esta función llamará al [constructor](#cprintdialog) para `CPrintDialog` con *BPRINTSETUPONLY* establecido en false. En estos casos, se asignan automáticamente un DC de impresora y `hDevNames` y `hDevMode` (dos identificadores ubicados en el miembro de datos de `m_pd`).

Si se llamó al constructor de `CPrintDialog` con *bPrintSetupOnly* establecido en false, esta función no solo devolverá `hDevNames` y `hDevMode` ubicado en `m_pd.hDevNames` y `m_pd.hDevMode`) al autor de la llamada, sino que también devolverá un controlador de dominio de impresora en `m_pd.hDC`. Es responsabilidad del autor de la llamada eliminar el controlador de dominio de la impresora y llamar a la función [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) de Windows en los identificadores cuando haya terminado con el objeto `CPrintDialog`.

### <a name="example"></a>Ejemplo

Este fragmento de código obtiene el contexto de dispositivo de la impresora predeterminada e informa al usuario de la resolución de la impresora en puntos por pulgada. (Este atributo de las capacidades de la impresora se denomina a menudo PPP).

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>CPrintDialog::GetDeviceName

Recupera el nombre del dispositivo de impresora seleccionado actualmente.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre de la impresora seleccionada actualmente.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) para recuperar el nombre de la impresora seleccionada actualmente o después de llamar a [GetDefaults](#getdefaults) para recuperar los valores predeterminados de dispositivo actuales de la impresora predeterminada. Use un puntero al objeto `CString` devuelto por `GetDeviceName` como el valor de `lpszDeviceName` en una llamada a [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Ejemplo

Este fragmento de código muestra el nombre de la impresora predeterminada del usuario y el puerto al que está conectado, junto con el nombre del administrador de trabajos de impresión que utiliza la impresora. El código podría mostrar un cuadro de mensaje que indica que "la impresora predeterminada es HP LaserJet IIIP en \\\server\share con winspool", por ejemplo.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>CPrintDialog::GetDevMode

Recupera la estructura de `DEVMODE`.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

La estructura de datos [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria tomada por esta estructura con la función [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, que se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar información sobre el dispositivo de impresión.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::P rintcollate](#printcollate).

##  <a name="getdrivername"></a>CPrintDialog:: GetDriverName

Recupera el nombre del controlador de impresora seleccionado actualmente.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

`CString` que especifica el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del controlador de dispositivo de impresora definido por el sistema. Use un puntero al objeto `CString` devuelto por `GetDriverName` como el valor de `lpszDriverName` en una llamada a [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>CPrintDialog::GetFromPage

Recupera la página de inicio del intervalo de impresión.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Valor devuelto

Número de la página inicial en el intervalo de páginas que se va a imprimir.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a `DoModal` para recuperar el número de la página inicial en el intervalo de páginas que se va a imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: m_pd](#m_pd).

##  <a name="getportname"></a>CPrintDialog::GetPortName

Recupera el nombre del puerto de impresora seleccionado actualmente.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del puerto de impresora seleccionado actualmente.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del puerto de impresora seleccionado actualmente.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>CPrintDialog::GetPrinterDC

Recupera un identificador para el contexto del dispositivo de impresora.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto del dispositivo de impresora si se realiza correctamente; de lo contrario, NULL.

### <a name="remarks"></a>Observaciones

Si el parámetro *bPrintSetupOnly* del constructor `CPrintDialog` era false (lo que indica que se muestra el cuadro de diálogo Imprimir), `GetPrinterDC` devuelve un identificador al contexto del dispositivo de impresora. Debe llamar a la función [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) de Windows para eliminar el contexto de dispositivo cuando termine de usarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>CPrintDialog::GetToPage

Recupera la página final del intervalo de impresión.

```
int GetToPage() const;
```

### <a name="return-value"></a>Valor devuelto

Número de la página final en el intervalo de páginas que se va a imprimir.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a `DoModal` para recuperar el número de la página final en el intervalo de páginas que se van a imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: m_pd](#m_pd).

##  <a name="m_pd"></a>CPrintDialog:: m_pd

Estructura cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Observaciones

Después de construir un objeto de `CPrintDialog`, puede utilizar `m_pd` para establecer diversos aspectos del cuadro de diálogo antes de llamar a la función miembro [DoModal](#domodal) . Para obtener más información sobre la estructura de `m_pd`, vea [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) en el Windows SDK.

Si modifica el miembro de datos `m_pd` directamente, invalidará el comportamiento predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>CPrintDialog::P rintAll

Determina si se van a imprimir todas las páginas del documento.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se van a imprimir todas las páginas del documento; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a `DoModal` para determinar si se van a imprimir todas las páginas del documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: m_pd](#m_pd).

##  <a name="printcollate"></a>CPrintDialog::P rintCollate

Determina si se solicitan las copias intercaladas.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona la casilla de verificación Intercalar en el cuadro de diálogo; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a `DoModal` para determinar si la impresora debe intercalar todas las copias impresas del documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>CPrintDialog::P rintRange

Determina si se va a imprimir solo un intervalo de páginas especificado.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si solo se va a imprimir un intervalo de páginas del documento; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a `DoModal` para determinar si se va a imprimir solo un intervalo de páginas del documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: m_pd](#m_pd).

##  <a name="printselection"></a>CPrintDialog::P rintSelection

Determina si se van a imprimir solo los elementos seleccionados actualmente.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si solo se van a imprimir los elementos seleccionados; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a `DoModal` para determinar si se van a imprimir solo los elementos seleccionados actualmente.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog:: m_pd](#m_pd).

## <a name="see-also"></a>Consulte también

[DIBLOOK de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo (estructura)](../../mfc/reference/cprintinfo-structure.md)
