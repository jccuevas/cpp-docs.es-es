---
title: CPageSetupDialog (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 721dd285760027c35ae93d89ec5bb3fde6e9ba11
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413456"
---
# <a name="cpagesetupdialog-class"></a>CPageSetupDialog (clase)

Encapsula los servicios proporcionados por el cuadro de diálogo Configurar página OLE común de Windows con compatibilidad adicional para configurar y modificar márgenes de impresión.

## <a name="syntax"></a>Sintaxis

```
class CPageSetupDialog : public CCommonDialog
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog)|Construye un objeto `CPageSetupDialog`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPageSetupDialog::CreatePrinterDC](#createprinterdc)|Crea un contexto de dispositivo de impresión.|
|[CPageSetupDialog::DoModal](#domodal)|Muestra el cuadro de diálogo y permite tomar una selección.|
|[CPageSetupDialog::GetDeviceName](#getdevicename)|Devuelve el nombre del dispositivo de la impresora.|
|[CPageSetupDialog::GetDevMode](#getdevmode)|Devuelve la estructura DEVMODE actual de la impresora.|
|[CPageSetupDialog::GetDriverName](#getdrivername)|Devuelve el controlador utilizado por la impresora.|
|[CPageSetupDialog::GetMargins](#getmargins)|Devuelve la configuración actual de margen de la impresora.|
|[CPageSetupDialog::GetPaperSize](#getpapersize)|Devuelve el tamaño del papel de la impresora.|
|[CPageSetupDialog::GetPortName](#getportname)|Devuelve el nombre del puerto de salida.|
|[CPageSetupDialog::OnDrawPage](#ondrawpage)|Lo llama el marco de trabajo para representar una imagen de pantalla de una página impresa.|
|[CPageSetupDialog::PreDrawPage](#predrawpage)|Lo llama el marco de trabajo antes de representar una imagen de pantalla de una página impresa.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPageSetupDialog::m_psd](#m_psd)|Una estructura utilizada para personalizar un `CPageSetupDialog` objeto.|

## <a name="remarks"></a>Comentarios

Esta clase está diseñada para ocupar el lugar del cuadro de diálogo Configuración de impresión.

Para usar un `CPageSetupDialog` , primero cree el objeto con el `CPageSetupDialog` constructor. Una vez que se ha construido el cuadro de diálogo, puede establecer o modificar los valores de la `m_psd` miembro de datos para inicializar los valores de los controles del cuadro de diálogo. El [m_psd](#m_psd) estructura es de tipo PAGESETUPDLG.

Después de inicializar los controles de cuadro de diálogo, llame a la `DoModal` la función miembro para mostrar el cuadro de diálogo y permitir al usuario seleccionar las opciones de impresión. `DoModal` Devuelve si el usuario seleccionó el botón Aceptar (IDOK) o Cancelar (IDCANCEL).

Si `DoModal` devuelve IDOK, se pueden usar varios de `CPageSetupDialog`del acceso o funciones miembro de la `m_psd` miembro de datos, para recuperar la entrada de información por el usuario.

> [!NOTE]
>  Una vez se cierra el cuadro de diálogo Configurar página OLE común, no se guardarán los cambios realizados por el usuario mediante el marco de trabajo. Es responsabilidad de la aplicación para guardar los valores de este cuadro de diálogo a una ubicación permanente, como miembro de clase de aplicación o documento de la aplicación.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CPageSetupDialog`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="cpagesetupdialog"></a>  CPageSetupDialog::CPageSetupDialog

Llame a esta función para construir un `CPageSetupDialog` objeto.

```
CPageSetupDialog(
    DWORD dwFlags = PSD_MARGINS | PSD_INWININIINTLMEASURE,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Uno o más marcadores que puede usar para personalizar la configuración del cuadro de diálogo. Los valores se pueden combinar mediante el operador OR bit a bit. Estos valores tienen los significados siguientes:

- PSD_DEFAULTMINMARGINS establece el ancho mínimo permitido para los márgenes de página ser el mismo que las cantidades mínimas de la impresora. Esta marca se omite si también se especifican los indicadores PSD_MARGINS y PSD_MINMARGINS.

- PSD_INWININIINTLMEASURE no implementado.

- PSD_MINMARGINS hace que el sistema usar los valores especificados en el `rtMinMargin` miembro como los anchos mínimos permitidos para la izquierda, superior, derecha y los márgenes de la parte inferior. El sistema evita que el usuario escriba un ancho menor que el mínimo especificado. Si no se especifica PSD_MINMARGINS, el sistema establece el ancho mínimo permitido para las que permite la impresora.

- PSD_MARGINS activa el margen del control.

- PSD_INTHOUSANDTHSOFINCHES hace que las unidades del cuadro de diálogo que se medirá en 1/1000 de pulgada.

- PSD_INHUNDREDTHSOFMILLIMETERS hace que las unidades del cuadro de diálogo que se medirá en 1/100 de milímetro.

- PSD_DISABLEMARGINS deshabilita los controles de cuadro de diálogo de margen.

- PSD_DISABLEPRINTER deshabilita el botón impresora.

- PSD_NOWARNING impide que el mensaje de advertencia que se muestra cuando no hay ninguna impresora predeterminada.

- PSD_DISABLEORIENTATION deshabilita el control de cuadro de diálogo de orientación de página.

- Hace que PSD_RETURNDEFAULT `CPageSetupDialog` para devolver [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) y [DEVNAMES](../../mfc/reference/devnames-structure.md) estructuras que se inicializaron para la impresora predeterminada del sistema sin mostrar un cuadro de diálogo. Se supone que ambos `hDevNames` y `hDevMode` son NULL; en caso contrario, la función devuelve un error. Si la impresora predeterminada del sistema es compatible con un anterior controlador de impresora (anterior a Windows versión 3.0), sólo `hDevNames` se devuelve; `hDevMode` es NULL.

- PSD_DISABLEPAPER deshabilita el control de selección de papel.

- PSD_SHOWHELP hace que el cuadro de diálogo Mostrar el botón de ayuda. El `hwndOwner` miembro no debe ser NULL si no se especifica esta marca.

- PSD_ENABLEPAGESETUPHOOK habilita la función de enlace especificada en `lpfnSetupHook`.

- PSD_ENABLEPAGESETUPTEMPLATE hace que el sistema operativo crear el cuadro de diálogo mediante el cuadro de diálogo plantilla identificado por `hInstance` y `lpSetupTemplateName`.

- PSD_ENABLEPAGESETUPTEMPLATEHANDLE indica que `hInstance` identifica un bloque de datos que contiene una plantilla de cuadro de diálogo cargados previamente. El sistema ignora `lpSetupTemplateName` si se especifica este marcador.

- PSD_ENABLEPAGEPAINTHOOK habilita la función de enlace especificada en `lpfnPagePaintHook`.

- PSD_DISABLEPAGEPAINTING deshabilita el área de dibujo del cuadro de diálogo.

*pParentWnd*<br/>
Puntero en el cuadro de diálogo principal o propietaria.

### <a name="remarks"></a>Comentarios

Use la [DoModal](../../mfc/reference/cdialog-class.md#domodal) función para mostrar el cuadro de diálogo.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#94](../../mfc/codesnippet/cpp/cpagesetupdialog-class_1.cpp)]

##  <a name="createprinterdc"></a>  CPageSetupDialog::CreatePrinterDC

Crea un contexto de dispositivo de impresora desde la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) y [DEVNAMES](../../mfc/reference/devnames-structure.md) estructuras.

```
HDC CreatePrinterDC();
```

### <a name="return-value"></a>Valor devuelto

Controlar el contexto de dispositivo de impresora recién creada (DC).

##  <a name="domodal"></a>  CPageSetupDialog::DoModal

Llame a esta función para mostrar el cuadro de diálogo Configurar página OLE común de Windows y permitir al usuario seleccionar distintas opciones de configuración de impresión, como los márgenes de impresión, el tamaño y la orientación del papel y la impresora de destino.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL. Si se devuelve IDCANCEL, llame a la Windows [CommDlgExtendedError](/windows/desktop/api/commdlg/nf-commdlg-commdlgextendederror) función para determinar si se produjo un error.

IDOK e IDCANCEL son las constantes que indican si el usuario seleccionó el botón Aceptar o Cancelar.

### <a name="remarks"></a>Comentarios

Además, el usuario puede tener acceso a las opciones de configuración de impresora como ubicación de red y las propiedades específicas de la impresora seleccionada.

Si desea inicializar las distintas opciones del cuadro de diálogo Configurar página estableciendo los miembros de la `m_psd` estructura, debe hacerlo antes de llamar a `DoModal`, y después de que se construye el objeto de cuadro de diálogo. Después de llamar a `DoModal`, llamar a otros miembros de funciones para recuperar la configuración o la entrada de información por el usuario en el cuadro de diálogo.

Si desea propagar la configuración actual especificada por el usuario, realice una llamada a [CWinApp::SelectPrinter](../../mfc/reference/cwinapp-class.md#selectprinter). Esta función toma la información de la `CPageSetupDialog` objeto inicializa y selecciona una nueva impresora de controlador de dominio con los atributos adecuados.

[!code-cpp[NVC_MFCDocView#95](../../mfc/codesnippet/cpp/cpagesetupdialog-class_2.cpp)]

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

##  <a name="getdevicename"></a>  CPageSetupDialog::GetDeviceName

Llame a esta función después de `DoModal` para recuperar el nombre de la impresora seleccionada actualmente.

```
CString GetDeviceName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre de dispositivo usado por el `CPageSetupDialog` objeto.

##  <a name="getdevmode"></a>  CPageSetupDialog::GetDevMode

Llame a esta función después de llamar a `DoModal` para recuperar información sobre el contexto de dispositivo de impresora de la `CPageSetupDialog` objeto.

```
LPDEVMODE GetDevMode() const;
```

### <a name="return-value"></a>Valor devuelto

El [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) estructuras de datos que contiene información sobre la inicialización del dispositivo y el entorno de un controlador de impresión. Debe desbloquear la memoria usada por esta estructura con el Windows [GlobalUnlock](/windows/desktop/api/winbase/nf-winbase-globalunlock) función, como se describe en el SDK de Windows.

##  <a name="getdrivername"></a>  CPageSetupDialog::GetDriverName

Llame a esta función después de llamar a [DoModal](../../mfc/reference/cprintdialog-class.md#domodal) para recuperar el nombre del controlador del dispositivo de impresora definido por el sistema.

```
CString GetDriverName() const;
```

### <a name="return-value"></a>Valor devuelto

Un `CString` especificando el nombre del controlador definido por el sistema.

### <a name="remarks"></a>Comentarios

Utilice un puntero a la `CString` objeto devuelto por `GetDriverName` como el valor de `lpszDriverName` en una llamada a [CDC::CreateDC](../../mfc/reference/cdc-class.md#createdc).

##  <a name="getmargins"></a>  CPageSetupDialog::GetMargins

Llame a esta función después de llamar a `DoModal` para recuperar los márgenes del controlador del dispositivo de impresora.

```
void GetMargins(
    LPRECT lpRectMargins,
    LPRECT lpRectMinMargins) const;
```

### <a name="parameters"></a>Parámetros

*lpRectMargins*<br/>
Puntero a un [RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto que describe (en pulgadas de 1/1000 o 1/100 mm) a los márgenes de impresión para la impresora seleccionada actualmente. Pasar NULL para este parámetro, si no está interesado en este rectángulo.

*lpRectMinMargins*<br/>
Puntero a un `RECT` estructura o `CRect` objeto que describe (en pulgadas de 1/1000 o 1/100 mm) a los márgenes de impresión mínimos para la impresora seleccionada actualmente. Pasar NULL para este parámetro, si no está interesado en este rectángulo.

##  <a name="getpapersize"></a>  CPageSetupDialog::GetPaperSize

Llame a esta función para recuperar el tamaño del papel seleccionado para la impresión.

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>Valor devuelto

Un [CSize](../../atl-mfc-shared/reference/csize-class.md) objeto que contiene el tamaño del papel (en pulgadas de 1/1000 o 1/100 mm) seleccionado para imprimir.

##  <a name="getportname"></a>  CPageSetupDialog::GetPortName

Llame a esta función después de llamar a `DoModal` para recuperar el nombre del puerto de impresora actualmente seleccionada.

```
CString GetPortName() const;
```

### <a name="return-value"></a>Valor devuelto

El nombre del puerto de impresora actualmente seleccionada.

##  <a name="m_psd"></a>  CPageSetupDialog::m_psd

Una estructura de tipo PAGESETUPDLG, cuyos miembros almacenan las características del objeto de cuadro de diálogo.

```
PAGESETUPDLG m_psd;
```

### <a name="remarks"></a>Comentarios

Después de crear un `CPageSetupDialog` objeto, puede usar `m_psd` para establecer varios aspectos del cuadro de diálogo antes de llamar a la `DoModal` función miembro.

Si modifica el `m_psd` miembro de datos directamente, invalidará cualquier comportamiento predeterminado.

Para obtener más información sobre la [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda) estructura, vea el SDK de Windows.

Vea el ejemplo de [CPageSetupDialog::CPageSetupDialog](#cpagesetupdialog).

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
Puntero al contexto de dispositivo de impresora.

*nha*<br/>
Especifica un mensaje, que indica el área de la página que se está dibujando actualmente. Puede ser uno de los siguientes:

- WM_PSD_FULLPAGERECT el área de página completa.

- Márgenes mínimos WM_PSD_MINMARGINRECT actual.

- Márgenes WM_PSD_MARGINRECT actual.

- WM_PSD_GREEKTEXTRECT el contenido de la página.

- WM_PSD_ENVSTAMPRECT área reservada para una representación de sello.

- Área WM_PSD_YAFULLPAGERECT para obtener una representación de la dirección de devolución. Esta área se extiende a los bordes del área de la página de ejemplo.

*lpRect*<br/>
Puntero a un [CRect](../../atl-mfc-shared/reference/crect-class.md) o [RECT](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/18113766-3975-4369-bc07-92e34cba712e/locales/en-us) objeto que contiene las coordenadas del área de dibujo.

### <a name="return-value"></a>Valor devuelto

Valor distinto de cero si se controló; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta imagen, a continuación, se muestra como parte del cuadro de diálogo Configurar página OLE común. La implementación predeterminada dibuja una imagen de una página de texto.

Reemplace esta función para personalizar el dibujo de un área específica de la imagen o toda la imagen. Puede hacerlo mediante el uso de un **cambiar** instrucción con **caso** instrucciones comprobando el valor de *nmensaje*. Por ejemplo, para personalizar la representación del contenido de la imagen de página, podría usar el código de ejemplo siguiente:

[!code-cpp[NVC_MFCDocView#96](../../mfc/codesnippet/cpp/cpagesetupdialog-class_3.cpp)]

Tenga en cuenta que no es necesario controlar todos los casos de *nmensaje*. Puede controlar un componente de la imagen, varios componentes de la imagen o el área completa.

##  <a name="predrawpage"></a>  CPageSetupDialog::PreDrawPage

Lo llama el marco de trabajo antes de dibujar la imagen en pantalla de una página impresa.

```
virtual UINT PreDrawPage(
    WORD wPaper,
    WORD wFlags,
    LPPAGESETUPDLG pPSD);
```

### <a name="parameters"></a>Parámetros

*wPaper*<br/>
Especifica un valor que indica el tamaño del papel. Este valor puede ser uno de los **DMPAPER_** valores aparecen en la descripción de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) estructura.

*wFlags*<br/>
Indica la orientación del papel o sobre, y si la impresora es una matriz de puntos o el dispositivo HPPCL (lenguaje de Control de impresora de Hewlett Packard). Este parámetro puede tener uno de los valores siguientes:

- 0 x 001 de papel en modo horizontal (matricial)

- 0 x 003 de papel en modo horizontal (HPPCL)

- 0x005 de papel en modo vertical (matricial)

- 0x007 de papel en modo vertical (HPPCL)

- 0x00b sobre en modo horizontal (HPPCL)

- 0x00d sobre en modo vertical (matricial)

- 0x019 sobre en modo horizontal (matricial)

- 0x01f sobre en modo vertical (matricial)

*PSD*<br/>
Puntero a una estructura `PAGESETUPDLG`. Para obtener más información sobre [PAGESETUPDLG](/windows/desktop/api/commdlg/ns-commdlg-tagpsda), consulte el SDK de Windows.

### <a name="return-value"></a>Valor devuelto

Valor distinto de cero si se controló; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Reemplace esta función para personalizar el dibujo de la imagen. Si reemplaza esta función y devuelve TRUE, se debe dibujar toda la imagen. Si reemplazar esta función y devuelve FALSE, se dibuja la imagen predeterminada todo el marco de trabajo.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC WORDPAD](../../visual-cpp-samples.md)<br/>
[CCommonDialog (clase)](../../mfc/reference/ccommondialog-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)



