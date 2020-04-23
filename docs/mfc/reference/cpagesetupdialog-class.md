---
title: Clase CPageSetupDialog
ms.date: 11/04/2016
f1_keywords:
- CPageSetupDialog
- AFXDLGS/CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CPageSetupDialog
- AFXDLGS/CPageSetupDialog::CreatePrinterDC
- AFXDLGS/CPageSetupDialog::DoModal
- AFXDLGS/CPageSetupDialog::GetDeviceName
- AFXDLGS/CPageSetupDialog::GetDevMode
- AFXDLGS/CPageSetupDialog::GetDriverName
- AFXDLGS/CPageSetupDialog::GetMargins
- AFXDLGS/CPageSetupDialog::GetPaperSize
- AFXDLGS/CPageSetupDialog::GetPortName
- AFXDLGS/CPageSetupDialog::OnDrawPage
- AFXDLGS/CPageSetupDialog::PreDrawPage
- AFXDLGS/CPageSetupDialog::m_psd
helpviewer_keywords:
- CPageSetupDialog [MFC], CPageSetupDialog
- CPageSetupDialog [MFC], CreatePrinterDC
- CPageSetupDialog [MFC], DoModal
- CPageSetupDialog [MFC], GetDeviceName
- CPageSetupDialog [MFC], GetDevMode
- CPageSetupDialog [MFC], GetDriverName
- CPageSetupDialog [MFC], GetMargins
- CPageSetupDialog [MFC], GetPaperSize
- CPageSetupDialog [MFC], GetPortName
- CPageSetupDialog [MFC], OnDrawPage
- CPageSetupDialog [MFC], PreDrawPage
- CPageSetupDialog [MFC], m_psd
ms.assetid: 049c0ac8-f254-4854-9414-7a8271d1447a
ms.openlocfilehash: 3664149ef0d7476b460ef06cddaf2b8145ade701
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753687"
---
# <a name="cpagesetupdialog-class"></a>Clase CPageSetupDialog

Encapsula los servicios proporcionados por el cuadro de diálogo Configurar página OLE común de Windows con compatibilidad adicional para configurar y modificar márgenes de impresión.

## <a name="syntax"></a>Sintaxis

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Construye un objeto `CPageSetupDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo para imprimir.|
|[CPageSetupDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite al usuario realizar una selección.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Devuelve el nombre del dispositivo de la impresora.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Devuelve el DEVMODE actual de la impresora.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Devuelve el controlador utilizado por la impresora.|
|[CPageSetupDialog::GetMargins](#getmargins)|Devuelve la configuración de margen actual de la impresora.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Devuelve el tamaño de papel de la impresora.|
|[CPageSetupDialog::GetPortName](#getportname)|Devuelve el nombre del puerto de salida.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Llamado por el marco de trabajo para representar una imagen de pantalla de una página impresa.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Llamado por el marco de trabajo antes de representar una imagen de pantalla de una página impresa.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Estructura utilizada para `CPageSetupDialog` personalizar un objeto.|

## <a name="remarks"></a>Observaciones

Esta clase está diseñada para tomar el lugar del cuadro de diálogo Configuración de impresión.

Para utilizar `CPageSetupDialog` un objeto, primero `CPageSetupDialog` cree el objeto mediante el constructor. Una vez construido el cuadro de diálogo, puede establecer `m_psd` o modificar cualquier valor en el miembro de datos para inicializar los valores de los controles del cuadro de diálogo. La estructura [m_psd](#m_psd) es de tipo PAGESETUPDLG.

Después de inicializar los controles `DoModal` del cuadro de diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar las opciones de impresión. `DoModal`devuelve si el usuario ha seleccionado el botón Aceptar (IDOK) o Cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede `CPageSetupDialog`usar varias de las `m_psd` funciones miembro de 's, o tener acceso al miembro de datos, para recuperar la información introducida por el usuario.

> [!NOTE]
> Después de descartar el cuadro de diálogo Configuración de página OLE común, el marco de trabajo no guardará los cambios realizados por el usuario. Depende de la propia aplicación guardar los valores de este cuadro de diálogo en una ubicación permanente, como el miembro del documento de la aplicación o la clase de aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="cpagesetupdialogcpagesetupdialog"></a><a name="cpagesetupdialog"></a>CPageSetupDialog::CPageSetupDialog

Llame a esta `CPageSetupDialog` función para construir un objeto.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Una o más marcas que puede utilizar para personalizar la configuración del cuadro de diálogo. Los valores se pueden combinar mediante el operador OR bit a bit. Estos valores tienen los significados siguientes:

- PSD_DEFAULTMINMARGINS Establece los anchos mínimos permitidos para que los márgenes de página sean los mismos que los mínimos de la impresora. Esta marca se omite si también se especifican las marcas PSD_MARGINS y PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE No implementado.

- PSD_MINMARGINS Hace que el sistema utilice `rtMinMargin` los valores especificados en el miembro como los anchos mínimos permitidos para los márgenes izquierdo, superior, derecho e inferior. El sistema impide que el usuario introduzca un ancho inferior al mínimo especificado. Si no se especifica PSD_MINMARGINS, el sistema establece los anchos mínimos permitidos a los permitidos por la impresora.

- PSD_MARGINS Activa el área de control de margen.

- PSD_INTHOUSANDTHSOFINCHES Hace que las unidades del cuadro de diálogo se midan en 1/1000 de pulgada.

- PSD_INHUNDREDTHSOFMILLIMETERS Hace que las unidades del cuadro de diálogo se midan en 1/100 de un milímetro.

- PSD_DISABLEMARGINS Deshabilita los controles del cuadro de diálogo de margen.

- PSD_DISABLEPRINTER Desactiva el botón Impresora.

- PSD_NOWARNING Impide que se muestre el mensaje de advertencia cuando no hay ninguna impresora predeterminada.

- PSD_DISABLEORIENTATION Deshabilita el control de cuadro de diálogo de orientación de página.

- PSD_RETURNDEFAULT `CPageSetupDialog` Hace que se devuelvan las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) que se inicializan para la impresora predeterminada del sistema sin mostrar un cuadro de diálogo. Se supone que `hDevNames` `hDevMode` ambos y son NULL; de lo contrario, la función devuelve un error. Si la impresora predeterminada del sistema es compatible con un controlador de `hDevNames` impresora antiguo (anterior a la versión 3.0 de Windows), solo se devuelve; `hDevMode` es NULL.

- PSD_DISABLEPAPER Desactiva el control de selección de papel.

- PSD_SHOWHELP Hace que el cuadro de diálogo muestre el botón Ayuda. El `hwndOwner` miembro no debe ser NULL si se especifica esta marca.

- PSD_ENABLEPAGESETUPHOOK Habilita la función `lpfnSetupHook`de enlace especificada en .

- PSD_ENABLEPAGESETUPTEMPLATE Hace que el sistema operativo cree el cuadro `hInstance` de `lpSetupTemplateName`diálogo mediante el cuadro de plantilla de cuadro de diálogo identificado por y .

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE Indica `hInstance` que identifica un bloque de datos que contiene una plantilla de cuadro de diálogo precargada. El sistema `lpSetupTemplateName` omite si se especifica este indicador.

- PSD_ENABLEPAGEPAINTHOOK Habilita la función `lpfnPagePaintHook`de enlace especificada en .

- PSD_DISABLEPAGEPAINTING Deshabilita el área de dibujo del cuadro de diálogo.

*pParentWnd*<br/>
Puntero al elemento primario o propietario del cuadro de diálogo.

### <a name="remarks"></a>Observaciones

Utilice la función [DoModal](../../mfc/reference/cdialog-class.md#domodal) para mostrar el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

## <a name="cpagesetupdialogcreateprinterdc"></a><a name="createprinterdc"></a>CPageSetupDialog::CreatePrinterDC

Crea un contexto de dispositivo de impresora a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES.](/windows/win32/api/commdlg/ns-commdlg-devnames)

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Manipule el contexto del dispositivo de impresora (DC) recién creado.

## <a name="cpagesetupdialogdomodal"></a><a name="domodal"></a>CPageSetupDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Configuración de página OLE común de Windows y permitir al usuario seleccionar varias opciones de configuración de impresión, como los márgenes de impresión, el tamaño y la orientación del papel y la impresora de destino.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK e IDCANCEL son constantes que indican si el usuario ha seleccionado el botón Aceptar o Cancelar.

### <a name="remarks"></a>Observaciones

Además, el usuario puede acceder a las opciones de configuración de la impresora, como la ubicación de red y las propiedades específicas de la impresora seleccionada.

Si desea inicializar las distintas opciones de cuadro `m_psd` de diálogo Configurar página `DoModal`estableciendo miembros de la estructura, debe hacerlo antes de llamar a , y después de que se construya el objeto de cuadro de diálogo. Después `DoModal`de llamar a , llame a otras funciones miembro para recuperar la configuración o la información introducida por el usuario en el cuadro de diálogo.

Si desea propagar la configuración actual introducida por el usuario, realice una llamada a [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Esta función toma `CPageSetupDialog` la información del objeto e inicializa y selecciona un nuevo controlador de dominio de impresora con los atributos adecuados.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialoggetdevicename"></a><a name="getdevicename"></a>CPageSetupDialog::GetDeviceName

Llame a `DoModal` esta función después de recuperar el nombre de la impresora seleccionada actualmente.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del `CPageSetupDialog` dispositivo utilizado por el objeto.

## <a name="cpagesetupdialoggetdevmode"></a><a name="getdevmode"></a>CPageSetupDialog::GetDevMode

Llame a esta `DoModal` función después de llamar `CPageSetupDialog` para recuperar información sobre el contexto del dispositivo de impresora del objeto.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

La estructura de datos [DEVMODE,](/windows/win32/api/wingdi/ns-wingdi-devmodea) que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria tomada por esta estructura con la función [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, que se describe en el Windows SDK.

## <a name="cpagesetupdialoggetdrivername"></a><a name="getdrivername"></a>CPageSetupDialog::GetDriverName

Llame a esta función después de llamar a [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) para recuperar el nombre del controlador de dispositivo de impresora definido por el sistema.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Especificando `CString` el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Observaciones

Utilice un puntero `CString` al `GetDriverName` objeto devuelto `lpszDriverName` como valor de en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

## <a name="cpagesetupdialoggetmargins"></a><a name="getmargins"></a>CPageSetupDialog::GetMargins

Llame a esta función después de una llamada para `DoModal` recuperar los márgenes del controlador del dispositivo de impresora.

```cpp
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parámetros

*lpRectMargins*<br/>
Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que describa (en 1/1000 pulgadas o 1/100 mm) los márgenes de impresión de la impresora seleccionada actualmente. Pase NULL para este parámetro, si no está interesado en este rectángulo.

*lpRectMinMargins*<br/>
Puntero a `RECT` una `CRect` estructura u objeto que describa (en 1/1000 pulgadas o 1/100 mm) los márgenes de impresión mínimos para la impresora seleccionada actualmente. Pase NULL para este parámetro, si no está interesado en este rectángulo.

## <a name="cpagesetupdialoggetpapersize"></a><a name="getpapersize"></a>CPageSetupDialog::GetPaperSize

Llame a esta función para recuperar el tamaño del papel seleccionado para la impresión.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valor devuelto

Objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) que contiene el tamaño del papel (en 1/1000 pulgadas o 1/100 mm) seleccionado para la impresión.

## <a name="cpagesetupdialoggetportname"></a><a name="getportname"></a>CPageSetupDialog::GetPortName

Llame a esta `DoModal` función después de llamar para recuperar el nombre del puerto de impresora seleccionado actualmente.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del puerto de impresora seleccionado actualmente.

## <a name="cpagesetupdialogm_psd"></a><a name="m_psd"></a>CPageSetupDialog::m_psd

Estructura de tipo PAGESETUPDLG, cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Observaciones

Después de `CPageSetupDialog` construir un `m_psd` objeto, puede usar para establecer varios `DoModal` aspectos del cuadro de diálogo antes de llamar a la función miembro.

Si modifica `m_psd` el miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

Para obtener más información sobre la estructura [PAGESETUPDLG,](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw) consulte el Windows SDK.

Vea el ejemplo de [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

## <a name="cpagesetupdialogondrawpage"></a><a name="ondrawpage"></a>CPageSetupDialog::OnDrawPage

Llamado por el marco de trabajo para dibujar una imagen de pantalla de una página impresa.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto del dispositivo de impresora.

*nMessage*<br/>
Especifica un mensaje que indica el área de la página que se está dibujando actualmente. Puede ser uno de los siguientes:

- WM_PSD_FULLPAGERECT El área de página completa.

- WM_PSD_MINMARGINRECT Márgenes mínimos actuales.

- WM_PSD_MARGINRECT Márgenes actuales.

- WM_PSD_GREEKTEXTRECT Contenido de la página.

- WM_PSD_ENVSTAMPRECT área reservada para una representación de sello postal.

- WM_PSD_YAFULLPAGERECT para una representación de dirección de devolución. Esta área se extiende a los bordes del área de página de muestra.

*lpRect*<br/>
Puntero a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene las coordenadas del área de dibujo.

### <a name="return-value"></a>Valor devuelto

Valor distinto de cero si se controla; de lo contrario 0.

### <a name="remarks"></a>Observaciones

A continuación, esta imagen se muestra como parte del cuadro de diálogo Configuración de página OLE común. La implementación predeterminada dibuja una imagen de una página de texto.

Reemplace esta función para personalizar el dibujo de un área específica de la imagen o de toda la imagen. Puede hacerlo mediante una instrucción **switch** con instrucciones **case** que comprueben el valor de *nMessage*. Por ejemplo, para personalizar la representación del contenido de la imagen de página, puede utilizar el siguiente código de ejemplo:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Tenga en cuenta que no es necesario controlar todos los casos de *nMessage*. Puede elegir manejar un componente de la imagen, varios componentes de la imagen o toda el área.

## <a name="cpagesetupdialogpredrawpage"></a><a name="predrawpage"></a>CPageSetupDialog::PreDrawPage

Llamado por el marco de trabajo antes de dibujar la imagen de pantalla de una página impresa.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parámetros

*wPaper*<br/>
Especifica un valor que indica el tamaño del papel. Este valor puede ser uno de los **valores de DMPAPER_** enumerados en la descripción de la estructura [DEVMODE.](/windows/win32/api/wingdi/ns-wingdi-devmodea)

*wFlags*<br/>
Indica la orientación del papel o sobre y si la impresora es una matriz de puntos o un dispositivo HPPCL (Hewlett Packard Printer Control Language). Este parámetro puede tener uno de los valores siguientes:

- 0x001 Papel en modo horizontal (matriz de puntos)

- 0x003 Papel en modo horizontal (HPPCL)

- 0x005 Papel en modo vertical (matriz de puntos)

- 0x007 Papel en modo vertical (HPPCL)

- 0x00b Sobre en modo horizontal (HPPCL)

- 0x00d Sobre en modo vertical (matriz de puntos)

- 0x019 Sobre en modo horizontal (matriz de puntos)

- 0x01f Sobre en modo vertical (matriz de puntos)

*Dpsp*<br/>
Puntero a una estructura `PAGESETUPDLG`. Para obtener más información sobre [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-pagesetupdlgw), consulte el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Valor distinto de cero si se controla; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Reemplace esta función para personalizar el dibujo de la imagen. Si invalida esta función y devuelve TRUE, debe dibujar toda la imagen. Si invalida esta función y devuelve FALSE, el marco de trabajo dibuja toda la imagen predeterminada.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[Clase CCommonDialog](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
