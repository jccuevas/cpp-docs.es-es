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
ms.openlocfilehash: 18b17d0f40aaab6ba2a018a568950549eda23016
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503013"
---
# <a name="cpagesetupdialog-class"></a>Clase CPageSetupDialog

Encapsula los servicios proporcionados por el cuadro de diálogo Configurar página OLE común de Windows con compatibilidad adicional para configurar y modificar márgenes de impresión.

## <a name="syntax"></a>Sintaxis

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Construye un objeto `CPageSetupDialog`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo para imprimir.|
|[CPageSetupDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite que el usuario realice una selección.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Devuelve el nombre del dispositivo de la impresora.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Devuelve el DEVMODE actual de la impresora.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Devuelve el controlador usado por la impresora.|
|[CPageSetupDialog::GetMargins](#getmargins)|Devuelve los valores de margen actuales de la impresora.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Devuelve el tamaño de papel de la impresora.|
|[CPageSetupDialog::GetPortName](#getportname)|Devuelve el nombre del puerto de salida.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Lo llama el marco de trabajo para representar una imagen en pantalla de una página impresa.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Lo llama el marco de trabajo antes de representar una imagen en pantalla de una página impresa.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Estructura utilizada para personalizar un `CPageSetupDialog` objeto.|

## <a name="remarks"></a>Comentarios

Esta clase está diseñada para que ocupe el lugar del cuadro de diálogo de configuración de impresión.

Para usar un `CPageSetupDialog` objeto, primero cree el objeto mediante el `CPageSetupDialog` constructor. Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores `m_psd` del miembro de datos para inicializar los valores de los controles del cuadro de diálogo. La estructura [m_psd](#m_psd) es de tipo PAGESETUPDLG.

Después de inicializar los controles de cuadro de `DoModal` diálogo, llame a la función miembro para mostrar el cuadro de diálogo y permitir que el usuario seleccione las opciones de impresión. `DoModal`Devuelve si el usuario seleccionó el botón Aceptar (IDOK) o cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, puede usar varias funciones miembro `CPageSetupDialog`de, o tener acceso al `m_psd` miembro de datos, para recuperar información introducida por el usuario.

> [!NOTE]
>  Una vez descartado el cuadro de diálogo Configuración de página OLE común, el marco de trabajo no guardará los cambios realizados por el usuario. Depende de la propia aplicación guardar los valores de este cuadro de diálogo en una ubicación permanente, como un miembro de la clase de documento o aplicación de la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs. h

##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog

Llame a esta función para construir `CPageSetupDialog` un objeto.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Una o varias marcas que puede usar para personalizar la configuración del cuadro de diálogo. Los valores se pueden combinar mediante el operador OR bit a bit. Estos valores tienen los significados siguientes:

- PSD_DEFAULTMINMARGINS establece el ancho mínimo permitido para que los márgenes de página sean los mismos que los mínimos de la impresora. Esta marca se omite si también se especifican las marcas PSD_MARGINS y PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE no implementado.

- PSD_MINMARGINS hace que el sistema use los valores especificados en `rtMinMargin` el miembro como el ancho mínimo permitido para los márgenes izquierdo, superior, derecho e inferior. El sistema impide que el usuario escriba un ancho menor que el mínimo especificado. Si no se especifica PSD_MINMARGINS, el sistema establece los anchos mínimos permitidos en los permitidos por la impresora.

- PSD_MARGINS activa el área de control margin.

- PSD_INTHOUSANDTHSOFINCHES hace que las unidades del cuadro de diálogo se midan en 1/1000 de pulgada.

- PSD_INHUNDREDTHSOFMILLIMETERS hace que las unidades del cuadro de diálogo se midan en 1/100 de milímetro.

- PSD_DISABLEMARGINS deshabilita los controles del cuadro de diálogo margen.

- PSD_DISABLEPRINTER deshabilita el botón impresora.

- PSD_NOWARNING evita que se muestre el mensaje de advertencia cuando no hay ninguna impresora predeterminada.

- PSD_DISABLEORIENTATION deshabilita el control de cuadro de diálogo de orientación de página.

- PSD_RETURNDEFAULT hace `CPageSetupDialog` que devuelva las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) inicializadas para la impresora predeterminada del sistema sin mostrar un cuadro de diálogo. Se supone que `hDevNames` y `hDevMode` son NULL; de lo contrario, la función devuelve un error. Si la impresora predeterminada del sistema es compatible con un controlador de impresora anterior (anterior a la versión 3,0 de `hDevNames` Windows), solo se devuelve; `hDevMode` es NULL.

- PSD_DISABLEPAPER deshabilita el control de selección de papel.

- PSD_SHOWHELP hace que el cuadro de diálogo muestre el botón ayuda. El `hwndOwner` miembro no debe ser null si se especifica esta marca.

- PSD_ENABLEPAGESETUPHOOK habilita la función de enlace especificada `lpfnSetupHook`en.

- PSD_ENABLEPAGESETUPTEMPLATE hace que el sistema operativo cree el cuadro de diálogo mediante el cuadro de plantilla de cuadro `hInstance` de `lpSetupTemplateName`diálogo identificado por y.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE indica que `hInstance` identifica un bloque de datos que contiene una plantilla de cuadro de diálogo cargada previamente. El sistema omite `lpSetupTemplateName` si se especifica esta marca.

- PSD_ENABLEPAGEPAINTHOOK habilita la función de enlace especificada `lpfnPagePaintHook`en.

- PSD_DISABLEPAGEPAINTING deshabilita el área de dibujo del cuadro de diálogo.

*pParentWnd*<br/>
Puntero al elemento primario o propietario del cuadro de diálogo.

### <a name="remarks"></a>Comentarios

Utilice la función [DoModal](../../mfc/reference/cdialog-class.md#domodal) para mostrar el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

Crea un contexto de dispositivo de impresora a partir de las estructuras [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) y [DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames) .

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Identificador del contexto de dispositivo de impresora (DC) que se acaba de crear.

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Configuración de página OLE común de Windows y permitir al usuario seleccionar varias opciones de configuración de impresión, como los márgenes de impresión, el tamaño y la orientación del papel, y la impresora de destino.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la función [CommDlgExtendedError](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) de Windows para determinar si se ha producido un error.

IDOK y IDCANCEL son constantes que indican si el usuario seleccionó el botón Aceptar o cancelar.

### <a name="remarks"></a>Comentarios

Además, el usuario puede tener acceso a las opciones de configuración de la impresora, como la ubicación de red y las propiedades específicas de la impresora seleccionada.

Si desea inicializar las diversas opciones del cuadro de diálogo de configuración de página mediante `m_psd` el establecimiento de miembros de la estructura, `DoModal`debe hacerlo antes de llamar a y después de que se construya el objeto de cuadro de diálogo. Después de `DoModal`llamar a, llame a otras funciones miembro para recuperar la información de configuración o la entrada del usuario en el cuadro de diálogo.

Si desea propagar la configuración actual introducida por el usuario, realice una llamada a [CWinApp:: SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Esta función toma la información del `CPageSetupDialog` objeto e inicializa y selecciona un nuevo controlador de dominio de impresora con los atributos adecuados.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog).

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

Llame a esta función `DoModal` después de para recuperar el nombre de la impresora seleccionada actualmente.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del dispositivo que usa el `CPageSetupDialog` objeto.

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

Llame a esta función después `DoModal` `CPageSetupDialog` de llamar a para recuperar información sobre el contexto de dispositivo de impresora del objeto.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

La estructura de datos [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) , que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria tomada por esta estructura con la función [GlobalUnlock](/windows/win32/api/winbase/nf-winbase-globalunlock) de Windows, que se describe en el Windows SDK.

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

Llame a esta función después de llamar a [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) para recuperar el nombre del controlador de dispositivo de impresora definido por el sistema.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Que `CString` especifica el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Comentarios

`CString` Use un puntero al objeto devuelto por `GetDriverName` como el valor de `lpszDriverName` en una llamada a [CDC:: CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

Llame a esta función después de una `DoModal` llamada a para recuperar los márgenes del controlador de dispositivo de impresora.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parámetros

*lpRectMargins*<br/>
Puntero a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que describe (en 1/1000 pulgadas o 1/100 mm) los márgenes de impresión de la impresora seleccionada actualmente. Pase NULL para este parámetro si no está interesado en este rectángulo.

*lpRectMinMargins*<br/>
Puntero a una `RECT` estructura u `CRect` objeto que describe (en 1/1000 pulgadas o 1/100 mm) el mínimo de márgenes de impresión de la impresora seleccionada actualmente. Pase NULL para este parámetro si no está interesado en este rectángulo.

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

Llame a esta función para recuperar el tamaño del papel seleccionado para imprimir.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valor devuelto

Un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) que contiene el tamaño del papel (en 1/1000 pulgadas o 1/100 mm) seleccionado para imprimir.

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

Llame a esta función después `DoModal` de llamar a para recuperar el nombre del puerto de impresora seleccionado actualmente.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

Nombre del puerto de impresora seleccionado actualmente.

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

Estructura de tipo PAGESETUPDLG, cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Comentarios

Después de construir un `CPageSetupDialog` objeto, puede utilizar `m_psd` para establecer diversos aspectos del cuadro de diálogo antes de llamar a `DoModal` la función miembro.

Si modifica el miembro `m_psd` de datos directamente, invalidará el comportamiento predeterminado.

Para obtener más información sobre la estructura [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw) , vea el Windows SDK.

Vea el ejemplo de [CPageSetupDialog:: CPageSetupDialog](#cpagesetupdialog).

##  <a name="ondrawpage"></a>  CPageSetupDialog::OnDrawPage

Lo llama el marco de trabajo para dibujar una imagen de pantalla de una página impresa.

```
virtual UINT OnDrawPage(
    CDC* pDC,
    UINT nMessage,
    LPRECT lpRect);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero en el contexto del dispositivo de impresora.

*nMessage*<br/>
Especifica un mensaje que indica el área de la página que se está dibujando actualmente. Puede ser uno de los siguientes:

- WM_PSD_FULLPAGERECT todo el área de la página.

- WM_PSD_MINMARGINRECT los márgenes mínimos actuales.

- WM_PSD_MARGINRECT los márgenes actuales.

- WM_PSD_GREEKTEXTRECT contenido de la página.

- Área de WM_PSD_ENVSTAMPRECT reservada para una representación de sello de franqueo.

- Área WM_PSD_YAFULLPAGERECT para una representación de dirección devuelta. Esta área se extiende hasta los bordes del área de la página de ejemplo.

*lpRect*<br/>
Puntero a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o [Rect](/windows/win32/api/windef/ns-windef-rect) que contiene las coordenadas del área de dibujo.

### <a name="return-value"></a>Valor devuelto

Valor distinto de cero si se controla; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

A continuación, esta imagen se muestra como parte del cuadro de diálogo Configuración de página OLE común. La implementación predeterminada dibuja una imagen de una página de texto.

Invalide esta función para personalizar el dibujo de un área específica de la imagen, o toda la imagen. Para ello, puede usar una instrucción **Switch** con instrucciones **Case** comprobando el valor de *nmensaje*. Por ejemplo, para personalizar la representación del contenido de la imagen de página, puede usar el siguiente código de ejemplo:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Tenga en cuenta que no necesita controlar cada caso de *nmensaje*. Puede optar por controlar un componente de la imagen, varios componentes de la imagen o todo el área.

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

Lo llama el marco de trabajo antes de dibujar la imagen de pantalla de una página impresa.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parámetros

*wPaper*<br/>
Especifica un valor que indica el tamaño del papel. Este valor puede ser uno de los valores de **DMPAPER_** enumerados en la descripción de la estructura [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) .

*wFlags*<br/>
Indica la orientación del papel o sobre, y si la impresora es un dispositivo de matriz de puntos o HPPCL (lenguaje de control de impresora de Hewlett Packard). Este parámetro puede tener uno de los valores siguientes:

- Papel 0x001 en modo horizontal (matriz de puntos)

- Papel 0x003 en modo horizontal (HPPCL)

- Papel 0x005 en modo vertical (matriz de puntos)

- Papel 0x007 en modo vertical (HPPCL)

- Sobre 0x00b en modo horizontal (HPPCL)

- Sobre 0x00d en modo vertical (matriz de puntos)

- Sobre 0x019 en modo horizontal (matriz de puntos)

- Sobre 0x01f en modo vertical (matriz de puntos)

*pPSD*<br/>
Puntero a una estructura `PAGESETUPDLG`. Para obtener más información sobre [PAGESETUPDLG](/windows/win32/api/commdlg/ns-commdlg-psdw), vea el Windows SDK.

### <a name="return-value"></a>Valor devuelto

Valor distinto de cero si se controla; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Invalide esta función para personalizar el dibujo de la imagen. Si invalida esta función y devuelve TRUE, debe dibujar toda la imagen. Si invalida esta función y devuelve FALSE, el marco de trabajo dibuja toda la imagen predeterminada.

## <a name="see-also"></a>Vea también

[WORDPAD de ejemplo de MFC](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
