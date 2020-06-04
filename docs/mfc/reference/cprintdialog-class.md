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
ms.openlocfilehash: 6490e5488c5ab3b808a02e3608b75541e4063d8f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364060"
---
# <a name="cprintdialog-class"></a>Clase CPrintDialog

Encapsula los servicios proporcionados por el cuadro de diálogo común de Windows para imprimir.

## <a name="syntax"></a>Sintaxis

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Construye un objeto `CPrintDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora sin mostrar el cuadro de diálogo Imprimir.|
|[CPrintDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[CPrintDialog::GetCopies](#getcopies)|Recupera el número de copias solicitadas.|
|[CPrintDialog::GetDefaults](#getdefaults)|Recupera los valores predeterminados del dispositivo sin mostrar un cuadro de diálogo.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Recupera el nombre del dispositivo de impresora seleccionado actualmente.|
|[CPrintDialog::GetDevMode](#getdevmode)|Recupera la `DEVMODE` estructura.|
|[CPrintDialog::GetDriverName](#getdrivername)|Recupera el nombre del controlador de impresora seleccionado actualmente.|
|[CPrintDialog::GetFromPage](#getfrompage)|Recupera la página inicial del intervalo de impresión.|
|[CPrintDialog::GetPortName](#getportname)|Recupera el nombre del puerto de impresora seleccionado actualmente.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Recupera un identificador en el contexto del dispositivo de impresora.|
|[CPrintDialog::GetToPage](#gettopage)|Recupera la página final del intervalo de impresión.|
|[CPrintDialog::PrintAll](#printall)|Determina si se deben imprimir todas las páginas del documento.|
|[CPrintDialog::PrintCollate](#printcollate)|Determina si se solicitan copias intercaladas.|
|[CPrintDialog::PrintRange](#printrange)|Determina si se debe imprimir solo un intervalo de páginas especificado.|
|[CPrintDialog::PrintSelection](#printselection)|Determina si se deben imprimir solo los elementos seleccionados actualmente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Estructura utilizada para `CPrintDialog` personalizar un objeto.|

## <a name="remarks"></a>Observaciones

Los cuadros de diálogo de impresión comunes proporcionan una manera sencilla de implementar los cuadros de diálogo Configuración de impresión e impresión de una manera coherente con los estándares de Windows.

> [!NOTE]
> La `CPrintDialogEx` clase encapsula los servicios proporcionados por la hoja de propiedades de Windows Print. Para obtener más información, consulte la información general [de CPrintDialogEx.](../../mfc/reference/cprintdialogex-class.md)

`CPrintDialog`La funcionalidad es reemplazada por la de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), que está diseñada para proporcionarle un cuadro de diálogo común tanto para la configuración de impresión como para la configuración de página.

Puede confiar en el marco de trabajo para controlar muchos aspectos del proceso de impresión de la aplicación. En este caso, el marco de trabajo muestra automáticamente el cuadro de diálogo común de Windows para imprimir. También puede tener la impresión del identificador de marco de trabajo para la aplicación, pero invalide el cuadro de diálogo Imprimir común con su propio cuadro de diálogo de impresión. Para obtener más información sobre el uso del marco de trabajo para gestionar las tareas de impresión, consulte el artículo [Impresión](../../mfc/printing.md).

Si desea que la aplicación controle la impresión sin la implicación del marco de trabajo, puede usar la `CPrintDialog` clase "tal cual" con el constructor proporcionado, o puede derivar su propia clase de cuadro de `CPrintDialog` diálogo y escribir un constructor que se adapte a sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como `CCommonDialog`cuadros de diálogo MFC estándar porque se derivan de la clase .

Para utilizar `CPrintDialog` un objeto, primero `CPrintDialog` cree el objeto mediante el constructor. Una vez construido el cuadro de diálogo, puede establecer o modificar cualquier valor de la estructura [m_pd](#m_pd) para inicializar los valores de los controles del cuadro de diálogo. La `m_pd` estructura es de tipo [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga). Para obtener más información sobre esta estructura, consulte el Windows SDK.

Si no proporciona sus `m_pd` propios `hDevMode` identificadores para el y `hDevNames` los `GlobalFree` miembros, asegúrese de llamar a la función de Windows para estos identificadores cuando haya terminado con el cuadro de diálogo. Cuando se utiliza la implementación `CWinApp::OnFilePrintSetup`de configuración de impresión del marco de trabajo proporcionada por , no es necesario liberar estos identificadores. Las asas `CWinApp` se mantienen y `CWinApp`se liberan en el destructor 's. Sólo es necesario liberar estos `CPrintDialog` mangos cuando se utiliza de forma independiente.

Después de inicializar los controles `DoModal` del cuadro de diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar las opciones de impresión. `DoModal`devuelve si el usuario ha seleccionado el botón Aceptar (IDOK) o Cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede `CPrintDialog`usar una de las funciones miembro de 's para recuperar la información introducida por el usuario.

La `CPrintDialog::GetDefaults` función miembro es útil para recuperar los valores predeterminados de impresora actuales sin mostrar un cuadro de diálogo. Esta función miembro no requiere ninguna interacción del usuario.

Puede usar la `CommDlgExtendedError` función de Windows para determinar si se ha producido un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, consulte el Windows SDK.

`CPrintDialog`depende del COMMDLG. DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de `CPrintDialog`diálogo, derive una clase de , proporcione una plantilla de cuadro de diálogo personalizada y agregue un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes sin procesar deben pasarse a la clase base. No es necesario personalizar la función de gancho.

Para procesar el mismo mensaje de forma diferente en función de si el cuadro de diálogo es Impresión o Configuración de impresión, debe derivar una clase para cada cuadro de diálogo. También debe reemplazar `AttachOnSetup` la función de Windows, que controla la creación de un nuevo cuadro de diálogo cuando el botón Configuración de impresión está seleccionado en un cuadro de diálogo Imprimir.

Para obtener más `CPrintDialog`información sobre el uso de , vea [Clases](../../mfc/common-dialog-classes.md)de cuadro de diálogo comunes .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="cprintdialogcprintdialog"></a><a name="cprintdialog"></a>CPrintDialog::CPrintDialog

Construye un objeto de cuadro de diálogo Configuración de impresión o impresión de Windows.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*bPrintSetupOnly*<br/>
Especifica si se muestra el cuadro de diálogo Imprimir de Windows estándar o el cuadro de diálogo Configuración de impresión. Establezca este parámetro en TRUE para mostrar el cuadro de diálogo Configuración de impresión de Windows estándar. Establézcalo en FALSE para mostrar el cuadro de diálogo Imprimir de Windows. Si *bPrintSetupOnly* es FALSE, en el cuadro de diálogo Imprimir se sigue mosando un botón de opción Configurar impresión.

*dwFlags*<br/>
Una o más marcas se pueden utilizar para personalizar la configuración del cuadro de diálogo, combinado mediante el operador OR bit a bit. Por ejemplo, el indicador PD_ALLPAGES establece el intervalo de impresión predeterminado en todas las páginas del documento. Consulte la estructura [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) en el Windows SDK para obtener más información sobre estas marcas.

*pParentWnd*<br/>
Puntero a la ventana principal o propietaria del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Esta función miembro solo construye el objeto. Utilice `DoModal` la función miembro para mostrar el cuadro de diálogo.

Tenga en cuenta que cuando se llama al constructor con *bPrintSetupOnly* establecido en FALSE, se utiliza automáticamente la marca PD_RETURNDC. Después `DoModal` `GetDefaults`de `GetPrinterDC`llamar a , , `m_pd.hDC`o , se devolverá un controlador de dominio de impresora en . Este controlador de dominio debe liberarse con una `CPrintDialog`llamada a [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) por el autor de la llamada de .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

## <a name="cprintdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPrintDialog::CreatePrinterDC

Crea un contexto de dispositivo de impresora (DC) a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Manipule el contexto del dispositivo de impresora recién creado.

### <a name="remarks"></a>Observaciones

Se supone que este controlador de dominio es el controlador de dominio de impresora actual y el usuario debe eliminar cualquier otro controlador de dominio de impresora obtenido anteriormente. Se puede llamar a esta función y utilizar el controlador de dominio resultante, sin mostrar nunca el cuadro de diálogo Imprimir.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

## <a name="cprintdialogdomodal"></a><a name="domodal"></a>CPrintDialog::DoModal

Muestra el cuadro de diálogo de impresión común de Windows y permite al usuario seleccionar varias opciones de impresión, como el número de copias, el intervalo de páginas y si se deben intercalar las copias.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK e IDCANCEL son constantes que indican si el usuario ha seleccionado el botón Aceptar o Cancelar.

### <a name="remarks"></a>Observaciones

Si desea inicializar las distintas opciones de `m_pd` cuadro de diálogo de `DoModal`impresión estableciendo miembros de la estructura, debe hacerlo antes de llamar a , pero después de que se construya el objeto de cuadro de diálogo.

Después `DoModal`de llamar a , puede llamar a otras funciones miembro para recuperar la configuración o la información introducida por el usuario en el cuadro de diálogo.

Tenga en cuenta que cuando se llama al constructor con *bPrintSetupOnly* establecido en FALSE, se utiliza automáticamente la marca PD_RETURNDC. Después `DoModal` `GetDefaults`de `GetPrinterDC`llamar a , , `m_pd.hDC`o , se devolverá un controlador de dominio de impresora en . Este controlador de dominio debe liberarse con una `CPrintDialog`llamada a [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) por el autor de la llamada de .

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::CreatePrinterDC](#createprinterdc).

## <a name="cprintdialoggetcopies"></a><a name="getcopies"></a>CPrintDialog::GetCopies

Recupera el número de copias solicitadas.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valor devuelto

El número de copias solicitadas.

### <a name="remarks"></a>Observaciones

Llame a esta `DoModal` función después de llamar para recuperar el número de copias solicitadas.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdefaults"></a><a name="getdefaults"></a>CPrintDialog::GetDefaults

Recupera los valores predeterminados del dispositivo de la impresora predeterminada sin mostrar un cuadro de diálogo.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Los valores recuperados se `m_pd` colocan en la estructura.

En algunos casos, una llamada a [constructor](#cprintdialog) esta `CPrintDialog` función llamará al constructor para con *bPrintSetupOnly* establecido en FALSE. En estos casos, se `hDevNames` `hDevMode` asignan automáticamente un `m_pd` controlador de dominio de impresora y (dos identificadores ubicados en el miembro de datos).

Si el `CPrintDialog` constructor para se llamó con *bPrintSetupOnly* establecido `hDevNames` en `hDevMode` FALSE, `m_pd.hDevMode`esta función no solo devolverá `m_pd.hDC`y se ubicará en `m_pd.hDevNames` y ) al autor de la llamada, sino que también devolverá un controlador de dominio de impresora en . Es responsabilidad del autor de la llamada eliminar el controlador de dominio de la `CPrintDialog` impresora y llamar a la función [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree) de Windows en los identificadores cuando haya terminado con el objeto.

### <a name="example"></a>Ejemplo

Este fragmento de código obtiene el contexto de dispositivo de la impresora predeterminada e informa al usuario de la resolución de la impresora en puntos por pulgada. (Este atributo de las capacidades de la impresora se conoce a menudo como DPI.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

## <a name="cprintdialoggetdevicename"></a><a name="getdevicename"></a>CPrintDialog::GetDeviceName

Recupera el nombre del dispositivo de impresora seleccionado actualmente.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la impresora seleccionada actualmente.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) para recuperar el nombre de la impresora seleccionada actualmente, o después de llamar a [GetDefaults](#getdefaults) para recuperar los valores predeterminados de dispositivo actuales de la impresora predeterminada. Utilice un puntero `CString` al `GetDeviceName` objeto devuelto `lpszDeviceName` como valor de en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Ejemplo

Este fragmento de código muestra el nombre de impresora predeterminado del usuario y el puerto al que está conectado, junto con el nombre de la cola de impresión que utiliza la impresora. El código puede mostrar un cuadro de mensaje que dice: "Su impresora predeterminada es HP LaserJet IIIP en \\el servidor de share usando winspool.", por ejemplo.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

## <a name="cprintdialoggetdevmode"></a><a name="getdevmode"></a>CPrintDialog::GetDevMode

Recupera la `DEVMODE` estructura.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

La estructura de datos [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria tomada por esta estructura con la función [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, que se describe en el Windows SDK.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar información sobre el dispositivo de impresión.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::PrintCollate](#printcollate).

## <a name="cprintdialoggetdrivername"></a><a name="getdrivername"></a>CPrintDialog::GetDriverName

Recupera el nombre del controlador de impresora seleccionado actualmente.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Especificando `CString` el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del controlador de dispositivo de impresora definido por el sistema. Utilice un puntero `CString` al `GetDriverName` objeto devuelto `lpszDriverName` como valor de en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetfrompage"></a><a name="getfrompage"></a>CPrintDialog::GetFromPage

Recupera la página inicial del intervalo de impresión.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Valor devuelto

El número de página inicial en el rango de páginas que se van a imprimir.

### <a name="remarks"></a>Observaciones

Llame a esta `DoModal` función después de llamar para recuperar el número de página inicial en el intervalo de páginas que se van a imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialoggetportname"></a><a name="getportname"></a>CPrintDialog::GetPortName

Recupera el nombre del puerto de impresora seleccionado actualmente.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del puerto de impresora seleccionado actualmente.

### <a name="remarks"></a>Observaciones

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del puerto de impresora seleccionado actualmente.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::GetDeviceName](#getdevicename).

## <a name="cprintdialoggetprinterdc"></a><a name="getprinterdc"></a>CPrintDialog::GetPrinterDC

Recupera un identificador en el contexto del dispositivo de impresora.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el contexto del dispositivo de impresora si se realiza correctamente; NULL.

### <a name="remarks"></a>Observaciones

Si el *bPrintSetupOnly* `CPrintDialog` parámetro del constructor era FALSE (que indica que `GetPrinterDC` se muestra el cuadro de diálogo Imprimir), a continuación, devuelve un identificador al contexto del dispositivo de impresora. Debe llamar a la función [DeleteDC](/windows/win32/api/wingdi/nf-wingdi-deletedc) de Windows para eliminar el contexto del dispositivo cuando haya terminado de usarlo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

## <a name="cprintdialoggettopage"></a><a name="gettopage"></a>CPrintDialog::GetToPage

Recupera la página final del intervalo de impresión.

```
int GetToPage() const;
```

### <a name="return-value"></a>Valor devuelto

El número de página final en el rango de páginas que se van a imprimir.

### <a name="remarks"></a>Observaciones

Llame a esta `DoModal` función después de llamar para recuperar el número de página final en el intervalo de páginas que se van a imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogm_pd"></a><a name="m_pd"></a>CPrintDialog::m_pd

Estructura cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Observaciones

Después de `CPrintDialog` construir un `m_pd` objeto, puede usar para establecer varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro. Para obtener más `m_pd` información sobre la estructura, consulte [PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga) en el Windows SDK.

Si modifica `m_pd` el miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

## <a name="cprintdialogprintall"></a><a name="printall"></a>CPrintDialog::PrintAll

Determina si se deben imprimir todas las páginas del documento.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se van a imprimir todas las páginas del documento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta `DoModal` función después de llamar para determinar si se deben imprimir todas las páginas del documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogprintcollate"></a><a name="printcollate"></a>CPrintDialog::PrintCollate

Determina si se solicitan copias intercaladas.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona la casilla de verificación de intercalación en el cuadro de diálogo; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta `DoModal` función después de llamar para determinar si la impresora debe recopilar todas las copias impresas del documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

## <a name="cprintdialogprintrange"></a><a name="printrange"></a>CPrintDialog::PrintRange

Determina si se debe imprimir solo un intervalo de páginas especificado.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si solo se va a imprimir un intervalo de páginas del documento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta `DoModal` función después de llamar para determinar si se debe imprimir solo un intervalo de páginas en el documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

## <a name="cprintdialogprintselection"></a><a name="printselection"></a>CPrintDialog::PrintSelection

Determina si se deben imprimir solo los elementos seleccionados actualmente.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si solo se van a imprimir los elementos seleccionados; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Llame a esta `DoModal` función después de llamar para determinar si se deben imprimir solo los elementos seleccionados actualmente.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Estructura CPrintInfo](../../mfc/reference/cprintinfo-structure.md)
