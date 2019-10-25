---
title: CPropertySheet (clase)
ms.date: 11/04/2016
f1_keywords:
- CPropertySheet
- AFXDLGS/CPropertySheet
- AFXDLGS/CPropertySheet::CPropertySheet
- AFXDLGS/CPropertySheet::AddPage
- AFXDLGS/CPropertySheet::Construct
- AFXDLGS/CPropertySheet::Create
- AFXDLGS/CPropertySheet::DoModal
- AFXDLGS/CPropertySheet::EnableStackedTabs
- AFXDLGS/CPropertySheet::EndDialog
- AFXDLGS/CPropertySheet::GetActiveIndex
- AFXDLGS/CPropertySheet::GetActivePage
- AFXDLGS/CPropertySheet::GetPage
- AFXDLGS/CPropertySheet::GetPageCount
- AFXDLGS/CPropertySheet::GetPageIndex
- AFXDLGS/CPropertySheet::GetTabControl
- AFXDLGS/CPropertySheet::MapDialogRect
- AFXDLGS/CPropertySheet::OnInitDialog
- AFXDLGS/CPropertySheet::PressButton
- AFXDLGS/CPropertySheet::RemovePage
- AFXDLGS/CPropertySheet::SetActivePage
- AFXDLGS/CPropertySheet::SetFinishText
- AFXDLGS/CPropertySheet::SetTitle
- AFXDLGS/CPropertySheet::SetWizardButtons
- AFXDLGS/CPropertySheet::SetWizardMode
- AFXDLGS/CPropertySheet::m_psh
helpviewer_keywords:
- CPropertySheet [MFC], CPropertySheet
- CPropertySheet [MFC], AddPage
- CPropertySheet [MFC], Construct
- CPropertySheet [MFC], Create
- CPropertySheet [MFC], DoModal
- CPropertySheet [MFC], EnableStackedTabs
- CPropertySheet [MFC], EndDialog
- CPropertySheet [MFC], GetActiveIndex
- CPropertySheet [MFC], GetActivePage
- CPropertySheet [MFC], GetPage
- CPropertySheet [MFC], GetPageCount
- CPropertySheet [MFC], GetPageIndex
- CPropertySheet [MFC], GetTabControl
- CPropertySheet [MFC], MapDialogRect
- CPropertySheet [MFC], OnInitDialog
- CPropertySheet [MFC], PressButton
- CPropertySheet [MFC], RemovePage
- CPropertySheet [MFC], SetActivePage
- CPropertySheet [MFC], SetFinishText
- CPropertySheet [MFC], SetTitle
- CPropertySheet [MFC], SetWizardButtons
- CPropertySheet [MFC], SetWizardMode
- CPropertySheet [MFC], m_psh
ms.assetid: 8461ccff-d14f-46e0-a746-42ad642ef94e
ms.openlocfilehash: 23d17aee2aacbc1484c0f3e181bc824546ab49a2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502823"
---
# <a name="cpropertysheet-class"></a>CPropertySheet (clase)

Representa hojas de propiedades, también conocidas como cuadros de diálogo de pestaña.

## <a name="syntax"></a>Sintaxis

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Construye un objeto `CPropertySheet`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Agrega una página a la hoja de propiedades.|
|[CPropertySheet::Construct](#construct)|Construye un objeto `CPropertySheet`.|
|[CPropertySheet::Create](#create)|Muestra una hoja de propiedades no modal.|
|[CPropertySheet::DoModal](#domodal)|Muestra una hoja de propiedades modal.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Indica si la hoja de propiedades utiliza pestañas apiladas o de desplazamiento.|
|[CPropertySheet::EndDialog](#enddialog)|Finaliza la hoja de propiedades.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Recupera el índice de la página activa de la hoja de propiedades.|
|[CPropertySheet::GetActivePage](#getactivepage)|Devuelve el objeto de página activo.|
|[CPropertySheet::GetPage](#getpage)|Recupera un puntero a la página especificada.|
|[CPropertySheet::GetPageCount](#getpagecount)|Recupera el número de páginas de la hoja de propiedades.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Recupera el índice de la página especificada de la hoja de propiedades.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Recupera un puntero a un control de ficha.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Invalide para aumentar la inicialización de la hoja de propiedades.|
|[CPropertySheet::PressButton](#pressbutton)|Simula la elección del botón especificado en una hoja de propiedades.|
|[CPropertySheet::RemovePage](#removepage)|Quita una página de la hoja de propiedades.|
|[CPropertySheet::SetActivePage](#setactivepage)|Establece mediante programación el objeto de página activo.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Establece el texto para el botón Finalizar.|
|[CPropertySheet::SetTitle](#settitle)|Establece el título de la hoja de propiedades.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Habilita los botones del asistente.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Habilita el modo del asistente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|Estructura [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) de Windows. Proporciona acceso a los parámetros básicos de la hoja de propiedades.|

## <a name="remarks"></a>Comentarios

Una hoja de propiedades consta de `CPropertySheet` un objeto y uno o varios objetos [CPropertyPage](../../mfc/reference/cpropertypage-class.md) . El marco de trabajo muestra una hoja de propiedades como una ventana con un conjunto de índices de pestaña y un área que contiene la página seleccionada actualmente. El usuario navega a una página específica mediante la ficha adecuada.

`CPropertySheet`proporciona compatibilidad con la estructura [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) expandida introducida en Windows 98 y windows NT 2000. La estructura contiene marcadores y miembros adicionales que admiten el uso de un mapa de bits de fondo de "marca de agua".

Para mostrar estas nuevas imágenes automáticamente en el objeto de hoja de propiedades, pase los valores válidos para las imágenes de mapa de bits y de paleta en la llamada a [CPropertySheet:: Construct](#construct) o [CPropertySheet:: CPropertySheet](#cpropertysheet).

Aunque `CPropertySheet` no se deriva de [CDialog](../../mfc/reference/cdialog-class.md), la administración de un objeto `CPropertySheet` es como la administración de un objeto `CDialog`. Por ejemplo, la creación de una hoja de propiedades requiere la construcción en dos partes: llamar al constructor y, a continuación, llamar a [DoModal](#domodal) para una hoja de propiedades modal o [crear](#create) para una hoja de propiedades no modal. `CPropertySheet`tiene dos tipos de constructores: [CPropertySheet:: Construct](#construct) y [CPropertySheet:: CPropertySheet](#cpropertysheet).

Cuando se construye un `CPropertySheet` objeto, algunos [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) pueden hacer que se produzca una excepción de primera oportunidad. Esto se debe a que el sistema intenta cambiar el estilo de la hoja de propiedades antes de crear la hoja. Para evitar esta excepción, asegúrese de establecer los siguientes estilos al crear el `CPropertySheet`:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Los estilos siguientes son opcionales y no provocarán la primera excepción:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Cualquier otro `Window Styles` está prohibido y no debe habilitarlos.

El intercambio de datos entre `CPropertySheet` un objeto y un objeto externo es similar al intercambio de datos con `CDialog` un objeto. La diferencia importante es que los valores de una hoja de propiedades suelen ser variables de miembro `CPropertyPage` de los objetos en lugar `CPropertySheet` del propio objeto.

Puede crear un tipo de cuadro de diálogo de pestaña denominado asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades que guía al usuario a través de los pasos de una operación, como la configuración de un dispositivo o la creación de un boletín. En un cuadro de diálogo de ficha tipo de asistente, las páginas de propiedades no tienen pestañas y solo se puede ver una página de propiedades a la vez. Además, en lugar de tener botones **Aceptar** y **aplicar ahora** , un cuadro de diálogo de la pestaña tipo asistente tiene un botón **atrás** , un botón **siguiente** o **Finalizar** , un botón **Cancelar** y un botón **ayuda** .

Para crear un cuadro de diálogo de tipo asistente, siga los mismos pasos que seguiría para crear una hoja de propiedades estándar, pero llame a [SetWizardMode](#setwizardmode) antes de llamar a [DoModal](#domodal). Para habilitar los botones del asistente, llame a [SetWizardButtons](#setwizardbuttons), usando marcas para personalizar su función y apariencia. Para habilitar el botón **Finalizar** , llame a [SetFinishText](#setfinishtext) después de que el usuario haya realizado la acción en la última página del asistente.

Para obtener más información sobre cómo usar `CPropertySheet` objetos, vea el artículo [hojas de propiedades y páginas de propiedades](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs. h

##  <a name="addpage"></a>  CPropertySheet::AddPage

Agrega la página proporcionada con la ficha situada más a la derecha en la hoja de propiedades.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Apunta a la página que se va a agregar a la hoja de propiedades. No puede ser nulo.

### <a name="remarks"></a>Comentarios

Agregue páginas a la hoja de propiedades en el orden de izquierda a derecha que desee que aparezcan.

`AddPage`agrega el objeto [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) a la `CPropertySheet` lista de páginas del objeto, pero no crea realmente la ventana de la página. El marco pospone la creación de la ventana de la página hasta que el usuario seleccione esa página.

Cuando se agrega una página de propiedades `AddPage`mediante `CPropertySheet` , `CPropertyPage`es el elemento primario de. Para obtener acceso a la hoja de propiedades desde la página de propiedades, llame a [CWnd:: GetParent](../../mfc/reference/cwnd-class.md#getparent).

No es necesario esperar hasta que se cree la ventana de la hoja de propiedades `AddPage`para llamar a. Normalmente, se llamará `AddPage` a antes de llamar a [DoModal](#domodal) o [Create](#create).

Si llama a `AddPage` después de mostrar la página de propiedades, la fila de pestañas reflejará la página recién agregada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>CPropertySheet:: Construct

Construye un objeto `CPropertySheet`.

```
void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

void Construct(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

void Construct(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>Parámetros

*nIDCaption*<br/>
IDENTIFICADOR del título que se va a utilizar para la hoja de propiedades.

*pParentWnd*<br/>
Puntero a la ventana primaria de la hoja de propiedades. Si es NULL, la ventana primaria será la ventana principal de la aplicación.

*iSelectPage*<br/>
Índice de la página que estará inicialmente en la parte superior. El valor predeterminado es la primera página agregada a la hoja.

*pszCaption*<br/>
Puntero a una cadena que contiene el título que se va a utilizar para la hoja de propiedades. No puede ser nulo.

*hbmWatermark*<br/>
Identificador del mapa de bits de la marca de agua de la página de propiedades.

*hpalWatermark*<br/>
Identificador de la paleta del mapa de bits de marca de agua y/o mapa de bits del encabezado.

*hbmHeader*<br/>
Identificador del mapa de bits del encabezado de la página de propiedades.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro si aún no se ha llamado a uno de los constructores de clase. Por ejemplo, llame `Construct` a cuando declare o asigne matrices de `CPropertySheet` objetos. En el caso de las matrices, debe llamar `Construct` a para cada miembro de la matriz.

Para mostrar la hoja de propiedades, llame a [DoModal](#domodal) o a [Create](#create). La cadena contenida en el primer parámetro se colocará en la barra de título de la hoja de propiedades.

Puede mostrar la marca de agua o las imágenes de encabezado automáticamente si usa el tercer o cuarto prototipo de `Construct`, enumerados anteriormente, y pasa valores válidos para los parámetros *hbmWatermark*, *hpalWatermark*y *hbmHeader* .

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra en qué circunstancias se `Construct`llamaría.

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

##  <a name="cpropertysheet"></a>  CPropertySheet::CPropertySheet

Construye un objeto `CPropertySheet`.

```
CPropertySheet();

explicit CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

explicit CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd = NULL,
    UINT iSelectPage = 0);

CPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);

CPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd,
    UINT iSelectPage,
    HBITMAP hbmWatermark,
    HPALETTE hpalWatermark = NULL,
    HBITMAP hbmHeader = NULL);
```

### <a name="parameters"></a>Parámetros

*nIDCaption*<br/>
IDENTIFICADOR del título que se va a utilizar para la hoja de propiedades.

*pParentWnd*<br/>
Apunta a la ventana primaria de la hoja de propiedades. Si es NULL, la ventana primaria será la ventana principal de la aplicación.

*iSelectPage*<br/>
Índice de la página que estará inicialmente en la parte superior. El valor predeterminado es la primera página agregada a la hoja.

*pszCaption*<br/>
Apunta a una cadena que contiene el título que se va a utilizar para la hoja de propiedades. No puede ser nulo.

*hbmWatermark*<br/>
Identificador del mapa de bits de fondo de la hoja de propiedades.

*hpalWatermark*<br/>
Identificador de la paleta del mapa de bits de la marca de agua o del encabezado de mapa de bits.

*hbmHeader*<br/>
Identificador del mapa de bits del encabezado de la página de propiedades.

### <a name="remarks"></a>Comentarios

Para mostrar la hoja de propiedades, llame a [DoModal](#domodal) o a [Create](#create). La cadena contenida en el primer parámetro se colocará en la barra de título de la hoja de propiedades.

Si tiene varios parámetros (por ejemplo, si usa una matriz), use la [construcción](#construct) en lugar de `CPropertySheet`.

Puede mostrar la marca de agua y/o las imágenes de encabezado automáticamente si usa los prototipos tercero `CPropertySheet`o cuarto de, anteriores, y pasa valores válidos para los parámetros *hbmWatermark*, *hpalWatermark*y *hbmHeader* .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>CPropertySheet:: Create

Muestra una hoja de propiedades no modal.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Apunta a la ventana primaria. Si es NULL, el elemento primario es el escritorio.

*dwStyle*<br/>
Estilos de ventana para la hoja de propiedades. Para obtener una lista completa de los estilos disponibles, vea [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Estilos de ventana extendidos para la hoja de propiedades. Para obtener una lista completa de los estilos disponibles, consulte [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se crea correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

La llamada a `Create` puede estar dentro del constructor o se puede llamar después de invocar el constructor.

El estilo predeterminado, expresado mediante Pass-1 como *dwStyle*, es realmente WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;&#124;DS_CONTEXTHELP WS_VISIBLE. El estilo de ventana extendido predeterminado, expresado al pasar 0 como *dwExStyle*, realmente es WS_EX_DLGMODALFRAME.

La `Create` función miembro devuelve inmediatamente después de crear la hoja de propiedades. Para destruir la hoja de propiedades, llame a [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow).

Las hojas de propiedades no modales mostradas `Create` con una llamada a no tienen los botones aceptar, cancelar, aplicar ahora y ayuda como las hojas de propiedades modales. El usuario debe crear los botones deseados.

Para mostrar una hoja de propiedades modal, llame a [DoModal](#domodal) en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

##  <a name="domodal"></a>  CPropertySheet::DoModal

Muestra una hoja de propiedades modal.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL si la función se realizó correctamente; de lo contrario, 0 o-1. Si la hoja de propiedades se ha establecido como un asistente (vea [SetWizardMode](#setwizardmode)) `DoModal` , devuelve ID_WIZFINISH o IDCANCEL.

### <a name="remarks"></a>Comentarios

El valor devuelto corresponde al identificador del control que cerró la hoja de propiedades. Después de que se devuelva esta función, se destruirán las ventanas correspondientes a la hoja de propiedades y todas las páginas. Los propios objetos seguirán existiendo. Normalmente, recuperará los datos de los objetos [CPropertyPage](../../mfc/reference/cpropertypage-class.md) después `DoModal` de que devuelva IDOK.

Para mostrar una hoja de propiedades no modal, llame a [Create](#create) en su lugar.

Cuando se crea una página de propiedades a partir de su recurso de cuadro de diálogo correspondiente, puede producirse una excepción de primera oportunidad. Esto se debe a que la página de propiedades cambia el estilo del recurso de cuadro de diálogo al estilo requerido antes de que se cree la página. Dado que los recursos suelen ser de solo lectura, esto produce una excepción. El sistema controla la excepción y realiza una copia del recurso modificado. Por tanto, se puede omitir la primera excepción.

> [!NOTE]
>  El sistema operativo debe controlar esta excepción si está compilando con el modelo de control de excepciones asincrónico. Para obtener más información sobre los modelos de control de excepciones, vea [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md). En este caso, no ajuste las llamadas a `CPropertySheet::DoModal` con un C++ bloque try-catch en el que la instrucción Catch controle todas las excepciones `catch (...)`, por ejemplo,. Este bloque controlaría la excepción prevista para el sistema operativo y produciría un comportamiento imprevisible. Sin embargo, puede utilizar C++ de forma segura el control de excepciones con tipos de excepción específicos o el control de excepciones estructurado, donde la excepción de infracción de acceso se pasa a través del sistema operativo.

Para evitar que se genere esta excepción de primera oportunidad, puede garantizar manualmente que la hoja de propiedades tenga los [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles)correctos. Debe establecer los siguientes estilos para una hoja de propiedades:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Puede usar los siguientes estilos opcionales sin producir una excepción de primera oportunidad:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Deshabilite todos los demás estilos de Windows porque no son compatibles con las hojas de propiedades. Este Consejo no se aplica a los estilos extendidos. Establecer los estilos estándar de forma adecuada garantizará que la hoja de propiedades no tiene que modificarse y evitará la generación de la primera excepción.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet:: AddPage](#addpage).

##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs

Indica si se van a apilar filas de pestañas en una hoja de propiedades.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parámetros

*bStacked*<br/>
Indica si las pestañas apiladas están habilitadas en la hoja de propiedades. Deshabilite las filas apiladas de etiquetas estableciendo *bStacked* en false.

### <a name="remarks"></a>Comentarios

De forma predeterminada, si una hoja de propiedades tiene más pestañas de las que caben en una sola fila en el ancho de la hoja de propiedades, las pestañas se apilarán en varias filas. Para usar las pestañas de desplazamiento en lugar de las pestañas `EnableStackedTabs` de apilamiento, llame a con *bStacked* establecido en false antes de llamar a [DoModal](#domodal) o [Create](#create).

Debe llamar al `EnableStackedTabs` método cuando cree una hoja de propiedades modal o no modal. Para incorporar este estilo en una `CPropertySheet`clase derivada de, escriba un controlador de mensajes para WM_CREATE. En la versión invalidada de [CWnd::](../../mfc/reference/cwnd-class.md#oncreate)alcreate `EnableStackedTabs( FALSE )` , llame a antes de llamar a la implementación de la clase base.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>CPropertySheet:: EndDialog

Finaliza la hoja de propiedades.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parámetros

*nEndID*<br/>
Identificador que se va a usar como valor devuelto de la hoja de propiedades.

### <a name="remarks"></a>Comentarios

El marco de trabajo llama a esta función miembro cuando se presiona el botón Aceptar, cancelar o cerrar. Llame a esta función miembro si se produce un evento que debería cerrar la hoja de propiedades.

Esta función miembro solo se usa con un cuadro de diálogo modal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::P ressbutton](#pressbutton).

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

Obtiene el número de índice de la página activa de la ventana de la hoja de propiedades y, a continuación, usa `GetPage`el número de índice devuelto como parámetro para.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Valor devuelto

Número de índice de la página activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage

Recupera la página activa de la ventana de la hoja de propiedades.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la página activa.

### <a name="remarks"></a>Comentarios

Utilice esta función miembro para realizar alguna acción en la página activa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

##  <a name="getpage"></a>  CPropertySheet::GetPage

Devuelve un puntero a la página especificada en esta hoja de propiedades.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
Índice de la página deseada, empezando por 0. Debe estar entre 0 y uno menos que el número de páginas de la hoja de propiedades, ambos inclusive.

### <a name="return-value"></a>Valor devuelto

El puntero a la página correspondiente al parámetro *nPage* .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount

Determina el número de páginas actualmente en la hoja de propiedades.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Valor devuelto

Número de páginas de la hoja de propiedades.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertyPage:: OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex

Recupera el número de índice de la página especificada en la hoja de propiedades.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Apunta a la página con el índice que se va a buscar. No puede ser nulo.

### <a name="return-value"></a>Valor devuelto

El número de índice de una página.

### <a name="remarks"></a>Comentarios

Por ejemplo, se usaría `GetPageIndex` para obtener el índice de la página con el fin de usar [SetActivePage](#setactivepage) o [GetPage](#getpage).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

Recupera un puntero a un control de ficha para realizar una acción específica del control de ficha (es decir, para usar cualquiera de las API en [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un control de ficha.

### <a name="remarks"></a>Comentarios

Por ejemplo, llame a esta función miembro si desea agregar mapas de bits a cada una de las pestañas durante la inicialización.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

Estructura cuyos miembros almacenan las características de [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Comentarios

Use esta estructura para inicializar la apariencia de la hoja de propiedades después de construirla, pero antes de que se muestre con la función miembro [DoModal](#domodal) . Por ejemplo, establezca el miembro *dwSize* de `m_psh` en el tamaño que desee que tenga la hoja de propiedades.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea PROPSHEETHEADER en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene las coordenadas del cuadro de diálogo que se van a convertir.

### <a name="remarks"></a>Comentarios

Las unidades de cuadro de diálogo se indican en términos de la unidad base de cuadro de diálogo actual derivada del ancho y alto promedio de los caracteres de la fuente utilizada para el texto del cuadro de diálogo. Una unidad horizontal es una cuarta parte de la unidad de ancho base del cuadro de diálogo y una unidad vertical es una octava parte de la unidad de alto base del cuadro de diálogo.

La función [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) de Windows devuelve información de tamaño para la fuente del sistema, pero puede especificar una fuente diferente para cada hoja de propiedades si usa el estilo DS_SETFONT en el archivo de definición de recursos. La función de Windows [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) , que se describe en el Windows SDK, usa la fuente adecuada para este cuadro de diálogo.

La `MapDialogRect` función miembro reemplaza las unidades de cuadro de diálogo de *lpRect* por unidades de pantalla (píxeles) para que el rectángulo pueda usarse para crear un cuadro de diálogo o para colocar un control dentro de un cuadro.

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

Invalida para aumentar la inicialización de la hoja de propiedades.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

Especifica si la aplicación ha establecido el foco de entrada en uno de los controles de la hoja de propiedades. Si `OnInitDialog` devuelve un valor distinto de cero, Windows establece el foco de entrada en el primer control de la hoja de propiedades. La aplicación solo puede devolver 0 si ha establecido explícitamente el foco de entrada en uno de los controles de la hoja de propiedades.

### <a name="remarks"></a>Comentarios

Se llama a esta función miembro como respuesta al mensaje WM_INITDIALOG. Este mensaje se envía a la hoja de propiedades durante las llamadas a [Create](#create) o [DoModal](#domodal) , que se producen inmediatamente antes de que se muestre la hoja de propiedades.

Invalide esta función miembro si necesita realizar un procesamiento especial cuando se inicializa la hoja de propiedades. En la versión invalidada, llame primero a la `OnInitDialog` clase base pero omita el valor devuelto. Normalmente, devolverá TRUE desde la función miembro invalidada.

No necesita una entrada de mapa de mensajes para esta función miembro.

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

Simula la elección del botón especificado en una hoja de propiedades.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parámetros

*nButton*<br/>
Nbotón Identifica el botón que se va a presionar. Este parámetro puede ser uno de los siguientes valores:

- PSBTN_BACK elige el botón atrás.

- PSBTN_NEXT elige el botón siguiente.

- PSBTN_FINISH elige el botón Finalizar.

- PSBTN_OK elige el botón Aceptar.

- PSBTN_APPLYNOW elige el botón aplicar ahora.

- PSBTN_CANCEL elige el botón Cancelar.

- PSBTN_HELP elige el botón ayuda.

### <a name="remarks"></a>Comentarios

Consulte [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) para obtener más información sobre el mensaje de PRESSBUTTON de Windows SDK.

Una llamada a `PressButton` no enviará la notificación [PSN_APPLY](/windows/win32/Controls/psn-apply) desde una página de propiedades al marco. Para enviar esta notificación, llame a [CPropertyPage:: onok](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

##  <a name="removepage"></a>  CPropertySheet::RemovePage

Quita una página de la hoja de propiedades y destruye la ventana asociada.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Apunta a la página que se va a quitar de la hoja de propiedades. No puede ser nulo.

*nPage*<br/>
Índice de la página que se va a quitar. Debe estar entre 0 y uno menos que el número de páginas de la hoja de propiedades, ambos inclusive.

### <a name="remarks"></a>Comentarios

El objeto [CPropertyPage](../../mfc/reference/cpropertypage-class.md) en sí no se destruye hasta que se cierra `CPropertySheet` el propietario de la ventana.

##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage

Cambia la página activa.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
Índice de la página que se va a establecer. Debe estar entre 0 y uno menos que el número de páginas de la hoja de propiedades, ambos inclusive.

*pPage*<br/>
Apunta a la página que se va a establecer en la hoja de propiedades. No puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se activa correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Por ejemplo, use `SetActivePage` si la acción de un usuario en una página debe hacer que otra página se convierta en la página activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet:: GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText

Establece el texto del botón de comando finalizar.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Señala el texto que se va a mostrar en el botón de comando finalizar.

### <a name="remarks"></a>Comentarios

Llame `SetFinishText` a para mostrar el texto del botón de comando finalizar y ocultar los botones siguiente y atrás después de que el usuario complete la acción en la última página del asistente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>  CPropertySheet::SetTitle

Especifica el título de la hoja de propiedades (el texto que se muestra en la barra de título de una ventana de marco).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Especifica el estilo del título de la hoja de propiedades. El estilo debe especificarse en 0 o como PSH_PROPTITLE. Si el estilo se establece como PSH_PROPTITLE, la palabra "propiedades" aparece después del texto especificado como título. Por ejemplo, llamar `SetTitle`a ("simple", PSH_PROPTITLE) dará como resultado un título de la hoja de propiedades de "propiedades simples".

*lpszText*<br/>
Señala el texto que se va a usar como título en la barra de título de la hoja de propiedades.

### <a name="remarks"></a>Comentarios

De forma predeterminada, una hoja de propiedades utiliza el parámetro Caption en el constructor de la hoja de propiedades.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>CPropertySheet:: SetWizardButtons

Habilita o deshabilita el botón atrás, siguiente o finalizar en una hoja de propiedades del asistente.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Un conjunto de marcas que personalizan la función y la apariencia de los botones del asistente. Este parámetro puede ser una combinación de los siguientes valores:

- PSWIZB_BACK botón atrás

- PSWIZB_NEXT botón siguiente

- PSWIZB_FINISH botón Finalizar

- PSWIZB_DISABLEDFINISH botón Finalizar deshabilitado

### <a name="remarks"></a>Comentarios

Llamar `SetWizardButtons` solo después de que el cuadro de diálogo esté abierto `SetWizardButtons` ; no se puede llamar a antes de llamar a [DoModal](#domodal). Normalmente, debe llamar a `SetWizardButtons` desde [CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Si desea cambiar el texto del botón Finalizar u ocultar los botones siguiente y atrás una vez que el usuario haya completado el asistente, llame a [SetFinishText](#setfinishtext). Tenga en cuenta que el mismo botón se comparte para finalizar y siguiente. Puede mostrar un botón Finalizar o siguiente al mismo tiempo, pero no ambos.

### <a name="example"></a>Ejemplo

Un `CPropertySheet` tiene tres páginas de propiedades del `CStylePage`asistente `CColorPage`:, `CShapePage`y.  En el fragmento de código siguiente se muestra cómo habilitar y deshabilitar los botones **atrás** y **siguiente** en la página de propiedades del asistente.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>  CPropertySheet::SetWizardMode

Establece una página de propiedades como un asistente.

```
void SetWizardMode();
```

### <a name="remarks"></a>Comentarios

Una característica clave de una página de propiedades del asistente es que el usuario navega con los botones siguiente, finalizar, atrás y cancelar en lugar de pestañas.

Llame `SetWizardMode` a antes de llamar a [DoModal](#domodal). Después de llamar `SetWizardMode`a `DoModal` , devolverá ID_WIZFINISH (si el usuario se cierra con el botón Finalizar) o IDCANCEL.

`SetWizardMode`establece la marca PSH_WIZARD.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
