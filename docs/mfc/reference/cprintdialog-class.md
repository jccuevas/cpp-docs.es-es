---
title: CPrintDialog (clase)
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
ms.openlocfilehash: b6fd633a39f7038be45a8776c9b4673138cc34b5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274952"
---
# <a name="cprintdialog-class"></a>CPrintDialog (clase)

Encapsula los servicios proporcionados por el cuadro de diálogo común de Windows para imprimir.

## <a name="syntax"></a>Sintaxis

```
class CPrintDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPrintDialog::CPrintDialog](#cprintdialog)|Construye un objeto `CPrintDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPrintDialog::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresora sin mostrar el cuadro de diálogo Imprimir.|
|[CPrintDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[CPrintDialog::GetCopies](#getcopies)|Recupera el número de copias solicitadas.|
|[CPrintDialog::GetDefaults](#getdefaults)|Recupera los valores predeterminados del dispositivo sin mostrar un cuadro de diálogo.|
|[CPrintDialog::GetDeviceName](#getdevicename)|Recupera el nombre del dispositivo de impresora actualmente seleccionada.|
|[CPrintDialog::GetDevMode](#getdevmode)|Recupera el `DEVMODE` estructura.|
|[CPrintDialog::GetDriverName](#getdrivername)|Recupera el nombre del controlador de impresora seleccionada actualmente.|
|[CPrintDialog::GetFromPage](#getfrompage)|Recupera la página de inicio del intervalo de impresión.|
|[CPrintDialog::GetPortName](#getportname)|Recupera el nombre del puerto de impresora actualmente seleccionada.|
|[CPrintDialog::GetPrinterDC](#getprinterdc)|Recupera un identificador para el contexto de dispositivo de impresora.|
|[CPrintDialog::GetToPage](#gettopage)|Recupera la página final del intervalo de impresión.|
|[CPrintDialog::PrintAll](#printall)|Determina si se va a imprimir todas las páginas del documento.|
|[CPrintDialog::PrintCollate](#printcollate)|Determina si se intercalan copias se solicitan.|
|[CPrintDialog::PrintRange](#printrange)|Determina si se imprime sólo un intervalo de páginas especificado.|
|[CPrintDialog::PrintSelection](#printselection)|Determina si se imprime sólo los elementos seleccionados actualmente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPrintDialog::m_pd](#m_pd)|Una estructura utilizada para personalizar un `CPrintDialog` objeto.|

## <a name="remarks"></a>Comentarios

Los cuadros de diálogo de impresión comunes proporcionan una manera fácil de implementar cuadros de diálogo de impresión y el programa de instalación de impresión de una manera coherente con los estándares de Windows.

> [!NOTE]
>  La `CPrintDialogEx` clase encapsula los servicios proporcionados por la hoja de propiedades de impresión de Windows. Para obtener más información, consulte el [CPrintDialogEx](../../mfc/reference/cprintdialogex-class.md) información general.

`CPrintDialog`de funcionalidad se ha reemplazado por el de [CPageSetupDialog](../../mfc/reference/cpagesetupdialog-class.md), que está diseñada para proporcionarle un cuadro de diálogo común para tanto el programa de instalación y configuración de página de la impresión.

Puede confiar en el marco de trabajo para controlar muchos aspectos del proceso de impresión de la aplicación. En este caso, el marco de trabajo muestra automáticamente el cuadro de diálogo comunes de Windows para la impresión. También puede tiene el identificador de marco de trabajo la impresión para la aplicación pero invalidar el cuadro de diálogo Imprimir común con su propio cuadro de diálogo de impresión. Para obtener más información sobre cómo usar el marco de trabajo para controlar las tareas de impresión, consulte el artículo [impresión](../../mfc/printing.md).

Si desea que la aplicación para controlar la impresión sin la participación de .NET framework, puede usar el `CPrintDialog` clase "tal cual" con el constructor proporcionado, o puede derivar su propia clase de cuadro de diálogo de `CPrintDialog` y escribir un constructor para satisfacer sus necesidades. En cualquier caso, estos cuadros de diálogo se comportarán como cuadros de diálogo MFC estándar, ya que se deriven de la clase `CCommonDialog`.

Para usar un `CPrintDialog` , primero cree el objeto con el `CPrintDialog` constructor. Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la [m_pd](#m_pd) estructura para inicializar los valores de los controles del cuadro de diálogo. El `m_pd` estructura es de tipo [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda). Para obtener más información sobre esta estructura, consulte el SDK de Windows.

Si no proporciona sus propios controladores en `m_pd` para el `hDevMode` y `hDevNames` miembros, no olvide llamar a la función de Windows `GlobalFree` para estos identificadores cuando haya terminado con el cuadro de diálogo. Cuando se usa la implementación de instalación de impresión del marco de trabajo proporcionada por `CWinApp::OnFilePrintSetup`, no es necesario que liberar estos identificadores. Los identificadores se mantienen por `CWinApp` y se liberan en `CWinApp`del destructor. Solo es necesario liberar estos identificadores cuando se usa `CPrintDialog` independiente.

Después de inicializar los controles de cuadro de diálogo, llame a la `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar las opciones de impresión. `DoModal` Devuelve si el usuario seleccionó el botón Aceptar (IDOK) o Cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede usar uno de `CPrintDialog`de las funciones miembro para recuperar la información de entrada por el usuario.

El `CPrintDialog::GetDefaults` función miembro es útil para recuperar los valores predeterminados de impresora actuales sin mostrar un cuadro de diálogo. Esta función miembro requiere ninguna interacción del usuario.

Puede usar el Windows `CommDlgExtendedError` función para determinar si se produjo un error durante la inicialización del cuadro de diálogo y para obtener más información sobre el error. Para obtener más información sobre esta función, consulte el SDK de Windows.

`CPrintDialog` se basa en el COMMDLG. Archivo DLL que se incluye con las versiones 3.1 y posteriores de Windows.

Para personalizar el cuadro de diálogo, derive una clase de `CPrintDialog`, proporcione una plantilla de cuadro de diálogo personalizado y agregar un mapa de mensajes para procesar los mensajes de notificación de los controles extendidos. Los mensajes no procesados se deben pasar a la clase base. Personalización de la función de enlace no es necesario.

Para procesar el mismo mensaje de manera diferente dependiendo de si el cuadro de diálogo es Print o instalación de impresión, debe derivar una clase para cada cuadro de diálogo. También debe reemplazar el Windows `AttachOnSetup` función, que controla la creación de un cuadro de diálogo cuando se selecciona el botón de instalación de impresión dentro de un cuadro de diálogo Imprimir.

Para obtener más información sobre el uso de `CPrintDialog`, consulte [clases de cuadro de diálogo comunes](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPrintDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="cprintdialog"></a>  CPrintDialog::CPrintDialog

Construye el objeto de cuadro de diálogo de impresión de Windows o el programa de instalación de impresión.

```
CPrintDialog(
    BOOL bPrintSetupOnly,
    DWORD dwFlags = PD_ALLPAGES | PD_USEDEVMODECOPIES | PD_NOPAGENUMS | PD_HIDEPRINTTOFILE | PD_NOSELECTION,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*bPrintSetupOnly*<br/>
Especifica si se muestra el cuadro de diálogo de impresión de Windows estándar o el cuadro de diálogo Configuración de impresión. Establezca este parámetro en True para mostrar el cuadro de diálogo de instalación de impresión de Windows estándar. Establézcalo en FALSE para mostrar el cuadro de diálogo de impresión de Windows. Si *bPrintSetupOnly* es FALSE, un botón de opción se sigue mostrando en el cuadro de diálogo Imprimir de instalación de impresión.

*dwFlags*<br/>
Uno o más marcadores que puede usar para personalizar la configuración del cuadro de diálogo combinada mediante el operador OR bit a bit. Por ejemplo, la marca PD_ALLPAGES establece el intervalo de impresión predeterminada para todas las páginas del documento. Consulte la [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) estructura en el SDK de Windows para obtener más información sobre estas marcas.

*pParentWnd*<br/>
Un puntero a la ventana de principal o propietaria del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Esta función miembro solo construye el objeto. Use el `DoModal` función miembro para mostrar el cuadro de diálogo.

Tenga en cuenta que cuando se llama al constructor con *bPrintSetupOnly* establecida en FALSE, se utiliza automáticamente la marca PD_RETURNDC. Después de llamar a `DoModal`, `GetDefaults`, o `GetPrinterDC`, se devolverá un DC de impresora en `m_pd.hDC`. Este controlador de dominio se debe liberar con una llamada a [DeleteObject](/windows/desktop/api/wingdi/nf-wingdi-deletedc) por el llamador de `CPrintDialog`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#174](../../mfc/codesnippet/cpp/cprintdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPrintDialog::CreatePrinterDC

Crea un contexto de dispositivo (DC) de impresora desde la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) y [DEVNAMES](/windows/desktop/api/commdlg/ns-commdlg-tagdevnames) estructuras.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto de dispositivo de impresora recién creado.

### <a name="remarks"></a>Comentarios

Este controlador de dominio se supone que el controlador de dominio de la impresora actual y cualquier otra impresora que se deben eliminar los controladores de dominio por el usuario ha obtenido anteriormente. Se puede llamar a esta función y utiliza el controlador de dominio resultante, sin mostrar el cuadro de diálogo Imprimir de alguna vez.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#106](../../mfc/codesnippet/cpp/cprintdialog-class_2.cpp)]

##  <a name="domodal"></a>  CPrintDialog::DoModal

Muestra el cuadro de diálogo de impresión común de Windows y permite al usuario seleccionar diversas opciones de impresión, como el número de copias, el intervalo de páginas, y si deben estar intercaladas copias.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) función para determinar si se produjo un error.

IDOK e IDCANCEL son las constantes que indican si el usuario seleccionó el botón Aceptar o Cancelar.

### <a name="remarks"></a>Comentarios

Si desea inicializar las distintas opciones de diálogo de impresión estableciendo los miembros de la `m_pd` estructura, debe hacerlo antes de llamar a `DoModal`, pero después de que se construye el objeto de cuadro de diálogo.

Después de llamar a `DoModal`, se puede llamar a otra funciones miembro para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.

Tenga en cuenta que cuando se llama al constructor con *bPrintSetupOnly* establecida en FALSE, se utiliza automáticamente la marca PD_RETURNDC. Después de llamar a `DoModal`, `GetDefaults`, o `GetPrinterDC`, se devolverá un DC de impresora en `m_pd.hDC`. Este controlador de dominio se debe liberar con una llamada a [DeleteObject](/windows/desktop/api/wingdi/nf-wingdi-deletedc) por el llamador de `CPrintDialog`.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::CreatePrinterDC](#createprinterdc).

##  <a name="getcopies"></a>  CPrintDialog::GetCopies

Recupera el número de copias solicitadas.

```
int GetCopies() const;
```

### <a name="return-value"></a>Valor devuelto

El número de copias que se solicita.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a `DoModal` para recuperar el número de copias que se solicita.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdefaults"></a>  CPrintDialog::GetDefaults

Recupera los valores predeterminados de dispositivo de la impresora predeterminada sin mostrar un cuadro de diálogo.

```
BOOL GetDefaults();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la función se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Los valores recuperados se colocan en el `m_pd` estructura.

En algunos casos, una llamada a esta función llamará el [constructor](#cprintdialog) para `CPrintDialog` con *bPrintSetupOnly* establecida en FALSE. En estos casos, un DC de impresora y `hDevNames` y `hDevMode` (dos puntos de control se encuentran en la `m_pd` miembro de datos) se asignan automáticamente.

If el constructor de `CPrintDialog` se llamó con *bPrintSetupOnly* establecida en FALSE, esta función no solo devolverá `hDevNames` y `hDevMode` ubicado en `m_pd.hDevNames` y `m_pd.hDevMode`) al llamador, pero también devolverá un DC de impresora en `m_pd.hDC`. Es responsabilidad del llamador para eliminar la impresora DC y llamar a la Windows [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree) función en los controladores cuando haya terminado con el `CPrintDialog` objeto.

### <a name="example"></a>Ejemplo

Este fragmento de código obtiene el contexto de dispositivo de la impresora predeterminada e informa al usuario la resolución de la impresora en puntos por pulgada. (Este atributo de capacidades de la impresora es a menudo sucesivo PPP.)

[!code-cpp[NVC_MFCDocView#107](../../mfc/codesnippet/cpp/cprintdialog-class_3.cpp)]

##  <a name="getdevicename"></a>  CPrintDialog::GetDeviceName

Recupera el nombre del dispositivo de impresora actualmente seleccionada.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de la impresora seleccionada actualmente.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a [DoModal](#domodal) para recuperar el nombre de la impresora seleccionada, o después de llamar a [GetDefaults](#getdefaults) para recuperar los valores predeterminados del dispositivo actual de la impresora predeterminada. Utilice un puntero a la `CString` objeto devuelto por `GetDeviceName` como el valor de `lpszDeviceName` en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Ejemplo

Este fragmento de código muestra el nombre de la impresora predeterminada del usuario y el puerto que está conectado, junto con el nombre de cola de impresión que usa la impresora. El código podría mostrar un cuadro de mensaje que dice: "la impresora predeterminada es HP LaserJet IIIP en \\\server\share mediante winspool.", por ejemplo.

[!code-cpp[NVC_MFCDocView#108](../../mfc/codesnippet/cpp/cprintdialog-class_4.cpp)]

##  <a name="getdevmode"></a>  CPrintDialog::GetDevMode

Recupera el `DEVMODE` estructura.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

El [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) estructuras de datos que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria usada por esta estructura con el Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) función, como se describe en el SDK de Windows.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar información sobre el dispositivo de impresión.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::PrintCollate](#printcollate).

##  <a name="getdrivername"></a>  CPrintDialog::GetDriverName

Recupera el nombre del controlador de impresora seleccionada actualmente.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Un `CString` especificando el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del controlador del dispositivo de impresora definido por el sistema. Utilice un puntero a la `CString` objeto devuelto por `GetDriverName` como el valor de `lpszDriverName` en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getfrompage"></a>  CPrintDialog::GetFromPage

Recupera la página de inicio del intervalo de impresión.

```
int GetFromPage() const;
```

### <a name="return-value"></a>Valor devuelto

Número de página inicial del intervalo de páginas que se van a imprimir.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a `DoModal` para recuperar el número de página inicial del intervalo de páginas que se van a imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

##  <a name="getportname"></a>  CPrintDialog::GetPortName

Recupera el nombre del puerto de impresora actualmente seleccionada.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del puerto de impresora actualmente seleccionada.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a [DoModal](#domodal) o [GetDefaults](#getdefaults) para recuperar el nombre del puerto de impresora actualmente seleccionada.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::GetDeviceName](#getdevicename).

##  <a name="getprinterdc"></a>  CPrintDialog::GetPrinterDC

Recupera un identificador para el contexto de dispositivo de impresora.

```
HDC GetPrinterDC() const;
```

### <a name="return-value"></a>Valor devuelto

Un identificador para el contexto de dispositivo de impresora si es correcto; en caso contrario, es NULL.

### <a name="remarks"></a>Comentarios

Si el *bPrintSetupOnly* parámetro de la `CPrintDialog` constructor era falso (indica que se muestra el cuadro de diálogo de impresión), a continuación, `GetPrinterDC` devuelve un identificador para el contexto de dispositivo de impresora. Debe llamar a la Windows [DeleteObject](/windows/desktop/api/wingdi/nf-wingdi-deletedc) función para eliminar el contexto de dispositivo cuando haya terminado con él.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#109](../../mfc/codesnippet/cpp/cprintdialog-class_5.cpp)]

##  <a name="gettopage"></a>  CPrintDialog::GetToPage

Recupera la página final del intervalo de impresión.

```
int GetToPage() const;
```

### <a name="return-value"></a>Valor devuelto

Número de página final del intervalo de páginas que se van a imprimir.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a `DoModal` para recuperar el número de página final del intervalo de páginas que se van a imprimir.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

##  <a name="m_pd"></a>  CPrintDialog::m_pd

Una estructura cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PRINTDLG& m_pd;
```

### <a name="remarks"></a>Comentarios

Después de crear un `CPrintDialog` objeto, puede usar `m_pd` para establecer varios aspectos del cuadro de diálogo antes de llamar a la [DoModal](#domodal) función miembro. Para obtener más información sobre la `m_pd` estructura, vea [PRINTDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpda) en el SDK de Windows.

Si modifica el `m_pd` miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#111](../../mfc/codesnippet/cpp/cprintdialog-class_6.cpp)]

##  <a name="printall"></a>  CPrintDialog::PrintAll

Determina si se va a imprimir todas las páginas del documento.

```
BOOL PrintAll() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si están todas las páginas del documento que se imprimen; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a `DoModal` para determinar si se va a imprimir todas las páginas del documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

##  <a name="printcollate"></a>  CPrintDialog::PrintCollate

Determina si se intercalan copias se solicitan.

```
BOOL PrintCollate() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario selecciona la casilla Intercalar el cuadro de diálogo. en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a `DoModal` para determinar si la impresora debe intercalar todas las copias del documento.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#110](../../mfc/codesnippet/cpp/cprintdialog-class_7.cpp)]

##  <a name="printrange"></a>  CPrintDialog::PrintRange

Determina si se imprime sólo un intervalo de páginas especificado.

```
BOOL PrintRange() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si solo un intervalo de páginas en el documento se imprimirá; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a `DoModal` para determinar si se debe imprimir sólo un intervalo de páginas del documento.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

##  <a name="printselection"></a>  CPrintDialog::PrintSelection

Determina si se imprime sólo los elementos seleccionados actualmente.

```
BOOL PrintSelection() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si solo los elementos seleccionados se imprimirá; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llame a esta función después de llamar a `DoModal` para determinar si se debe imprimir sólo los elementos seleccionados actualmente.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPrintDialog::m_pd](#m_pd).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC DIBLOOK](../../visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPrintInfo (estructura)](../../mfc/reference/cprintinfo-structure.md)
