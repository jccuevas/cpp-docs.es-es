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
ms.openlocfilehash: 0e5194a356684f2ff86d74a0ed1f37f332bcffeb
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58781658"
---
# <a name="cpropertysheet-class"></a>CPropertySheet (clase)

Representa hojas de propiedades, también conocidas como cuadros de diálogo de pestaña.

## <a name="syntax"></a>Sintaxis

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Construye un objeto `CPropertySheet`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Agrega una página a la hoja de propiedades.|
|[CPropertySheet::Construct](#construct)|Construye un objeto `CPropertySheet`.|
|[CPropertySheet::Create](#create)|Muestra una hoja de propiedades no modal.|
|[CPropertySheet::DoModal](#domodal)|Muestra una hoja de propiedades modal.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Indica si la hoja de propiedades usa pestañas apiladas o desplazamiento.|
|[CPropertySheet::EndDialog](#enddialog)|Finaliza la hoja de propiedades.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Recupera el índice de la página activa de la hoja de propiedades.|
|[CPropertySheet::GetActivePage](#getactivepage)|Devuelve el objeto de la página activa.|
|[CPropertySheet::GetPage](#getpage)|Recupera un puntero a la página especificada.|
|[CPropertySheet::GetPageCount](#getpagecount)|Recupera el número de páginas en la hoja de propiedades.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Recupera el índice de la página especificada de la hoja de propiedades.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Recupera un puntero a un control de ficha.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de la pantalla.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Invalidar para aumentar la inicialización de la hoja de propiedades.|
|[CPropertySheet::PressButton](#pressbutton)|Simula la elección del botón especificado en una hoja de propiedades.|
|[CPropertySheet::RemovePage](#removepage)|Quita una página de la hoja de propiedades.|
|[CPropertySheet::SetActivePage](#setactivepage)|Se establece mediante programación el objeto de la página activa.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Establece el texto para el botón Finalizar.|
|[CPropertySheet::SetTitle](#settitle)|Establece el título de la hoja de propiedades.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Permite que los botones del asistente.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Habilita el modo de asistente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|El Windows [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) estructura. Proporciona acceso a los parámetros de la hoja de propiedades básicas.|

## <a name="remarks"></a>Comentarios

Consta de una hoja de propiedades de un `CPropertySheet` objeto y uno o más [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objetos. El marco de trabajo muestra una hoja de propiedades como una ventana con un conjunto de índices de pestaña y un área que contiene la página seleccionada actualmente. El usuario navega a una página específica mediante el uso de la pestaña correspondiente.

`CPropertySheet` proporciona compatibilidad para el modo expandido [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2) estructura que se presentó en Windows 98 y 2000 de Windows NT. La estructura contiene marcas adicionales y los miembros que admiten el uso de un mapa de bits de fondo "marca de agua".

Para mostrar estas nuevas imágenes automáticamente en su objeto de hoja de propiedades, pasar los valores válidos para las imágenes de mapa de bits y paleta en la llamada a [CPropertySheet::Construct](#construct) o [CPropertySheet::CPropertySheet](#cpropertysheet).

Aunque `CPropertySheet` no se deriva [CDialog](../../mfc/reference/cdialog-class.md), administrar un `CPropertySheet` objeto es similar a administrar un `CDialog` objeto. Por ejemplo, la creación de una hoja de propiedades requiere la construcción de dos partes: llame al constructor y, a continuación, llame a [DoModal](#domodal) para una hoja de propiedades modal o [crear](#create) para una hoja de propiedades no modal. `CPropertySheet` tiene dos tipos de constructores: [CPropertySheet::Construct](#construct) y [CPropertySheet::CPropertySheet](#cpropertysheet).

Cuando se construye un `CPropertySheet` objeto, algunas [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) puede provocar una excepción de primera oportunidad para que se produzca. Esto da como resultado desde el sistema intenta cambiar el estilo de la hoja de propiedades antes de crea la hoja. Para evitar esta excepción, asegúrese de establecer los estilos siguientes al crear su `CPropertySheet`:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Los estilos siguientes son opcionales y no provocará la excepción de primera oportunidad:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Cualquier otro `Window Styles` están prohibidos y no se debe habilitar.

Intercambiar datos entre un `CPropertySheet` objeto y un objeto externo es similar a intercambiar datos con un `CDialog` objeto. La diferencia más importante es que la configuración de una hoja de propiedades normalmente es variables de miembro de la `CPropertyPage` objetos en lugar de la `CPropertySheet` propio objeto.

Puede crear un tipo de ficha del cuadro de diálogo llama a un asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades que guían al usuario a través de los pasos necesarios para una operación, como la configuración de un dispositivo o la creación de un boletín. En un cuadro de diálogo de pestaña de tipo asistente las páginas de propiedades no tiene pestañas y solo una página de propiedades es visible a la vez. Además, en lugar de tener **Aceptar** y **aplicar ahora** botones, un cuadro de diálogo de pestaña de tipo asistente tiene una **Atrás** botón, un **siguiente** o  **Finalizar** botón, un **cancelar** botón y un **ayuda** botón.

Para crear un cuadro de diálogo de tipo asistente, siga los mismos pasos que debe seguir para crear una hoja de propiedades estándar, pero llama a [SetWizardMode](#setwizardmode) antes de llamar a [DoModal](#domodal). Para habilitar los botones del asistente, llame a [SetWizardButtons](#setwizardbuttons), uso de marcas para personalizar sus funciones y apariencia. Para habilitar el **finalizar** botón, llame a [SetFinishText](#setfinishtext) después de que el usuario ha tomado ninguna acción en la última página del asistente.

Para obtener más información sobre cómo usar `CPropertySheet` objetos, consulte el artículo [hojas de propiedades y páginas de propiedades](../../mfc/property-sheets-and-property-pages-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

##  <a name="addpage"></a>  CPropertySheet::AddPage

Agrega la página proporcionada con la pestaña situada en la hoja de propiedades.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Hace referencia a la página que se agregarán a la hoja de propiedades. No puede ser nulo.

### <a name="remarks"></a>Comentarios

Agregar páginas a la hoja de propiedades en el orden de izquierda a derecha que desee que aparezcan.

`AddPage` Agrega el [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) de objeto para el `CPropertySheet` objeto de la lista de páginas, pero realmente no crea la ventana de la página. El marco de trabajo pospone la creación de la ventana de la página hasta que el usuario selecciona esa página.

Al agregar una página de propiedad mediante `AddPage`, `CPropertySheet` es el elemento primario de la `CPropertyPage`. Para obtener acceso a la hoja de propiedades de la página de propiedades, llamar a [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

No es necesario esperar a la creación de la ventana de la hoja de propiedades para llamar a `AddPage`. Normalmente, se llama `AddPage` antes de llamar a [DoModal](#domodal) o [crear](#create).

Si se llama a `AddPage` después de mostrar la página de propiedades, la fila de pestañas reflejará la página recién agregada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

##  <a name="construct"></a>  CPropertySheet::Construct

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
Id. de la leyenda que se usará para la hoja de propiedades.

*pParentWnd*<br/>
Puntero a la ventana primaria de la hoja de propiedades. Si es NULL, la ventana primaria será la ventana principal de la aplicación.

*iSelectPage*<br/>
El índice de la página que será inicialmente en la parte superior. Valor predeterminado es la primera página que se agrega a la hoja.

*pszCaption*<br/>
Puntero a una cadena que contiene el título que se usará para la hoja de propiedades. No puede ser nulo.

*hbmWatermark*<br/>
Identificador de mapa de bits de marca de agua de la página de propiedades.

*hpalWatermark*<br/>
Identificador de la paleta del mapa de bits de marca de agua o mapa de bits del encabezado.

*hbmHeader*<br/>
Identificador del mapa de bits del encabezado de la página de propiedades.

### <a name="remarks"></a>Comentarios

Llame a esta función miembro si uno de los constructores de clase ya no se ha llamado. Por ejemplo, llamar a `Construct` al declarar o asignar matrices de `CPropertySheet` objetos. En el caso de las matrices, debe llamar a `Construct` para cada miembro de la matriz.

Para mostrar la hoja de propiedades, llame a [DoModal](#domodal) o [crear](#create). La cadena contenida en el primer parámetro se colocarán en la barra de título de la hoja de propiedades.

Puede mostrar las imágenes de marca de agua o encabezado automáticamente si usa el tercer o cuarto prototipos de `Construct`, enumeradas anteriormente y pasar los valores válidos para el *hbmWatermark*, *hpalWatermark* , o *hbmHeader* parámetros.

### <a name="example"></a>Ejemplo

El ejemplo siguiente se muestra en qué circunstancias se llamaría a `Construct`.

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
Id. de la leyenda que se usará para la hoja de propiedades.

*pParentWnd*<br/>
Apunta a la ventana primaria de la hoja de propiedades. Si es NULL, la ventana primaria será la ventana principal de la aplicación.

*iSelectPage*<br/>
El índice de la página que será inicialmente en la parte superior. Valor predeterminado es la primera página que se agrega a la hoja.

*pszCaption*<br/>
Apunta a una cadena que contiene el título que se usará para la hoja de propiedades. No puede ser nulo.

*hbmWatermark*<br/>
Identificador de mapa de bits en segundo plano de la hoja de propiedades.

*hpalWatermark*<br/>
Identificador de la paleta del mapa de bits de marca de agua o mapa de bits del encabezado.

*hbmHeader*<br/>
Identificador del mapa de bits del encabezado de la página de propiedades.

### <a name="remarks"></a>Comentarios

Para mostrar la hoja de propiedades, llame a [DoModal](#domodal) o [crear](#create). La cadena contenida en el primer parámetro se colocarán en la barra de título de la hoja de propiedades.

Si tiene varios parámetros (por ejemplo, si está utilizando una matriz), use [construir](#construct) en lugar de `CPropertySheet`.

Puede mostrar las imágenes de marca de agua o encabezado automáticamente si usa el tercer o cuarto prototipos de `CPropertySheet`, anteriormente, y pase los valores válidos el *hbmWatermark*, *hpalWatermark*, y / o *hbmHeader* parámetros.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

##  <a name="create"></a>  CPropertySheet::Create

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
Estilos de ventana para la hoja de propiedades. Para obtener una lista completa de los estilos disponibles, consulte [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles).

*dwExStyle*<br/>
Estilos de ventana extendidos para la hoja de propiedades. Para obtener una lista completa de los estilos disponibles, consulte [estilos de ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se ha creado correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

La llamada a `Create` puede ser dentro del constructor, o puede llamar después de invoca el constructor.

El estilo predeterminado, expresado pasando -1 como *dwStyle*, es realmente WS_SYSMENU&#124;WS_POPUP&#124;WS_CAPTION&#124;DS_MODALFRAME&#124;DS_CONTEXTHELP&#124;WS_VISIBLE. El valor predeterminado extendido de estilo de ventana, expresada, pase 0 como *dwExStyle*, es realmente WS_EX_DLGMODALFRAME.

El `Create` función miembro devuelve inmediatamente después de crear la hoja de propiedades. Para destruir la hoja de propiedades, llamar a [CWnd:: DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Hojas de propiedades no modal que se muestra con una llamada a `Create` no tiene los botones OK, Cancel, aplicar ahora y ayuda, igual que las hojas de propiedades modal. Por el usuario se deben crear botones deseados.

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

IDOK o IDCANCEL si la función se realizó correctamente; en caso contrario, 0 o -1. Si se ha establecido la hoja de propiedades como un asistente (consulte [SetWizardMode](#setwizardmode)), `DoModal` devuelve ID_WIZFINISH o IDCANCEL.

### <a name="remarks"></a>Comentarios

El valor devuelto corresponde al identificador del control que se cierra la hoja de propiedades. Después de esta función devuelve, habrá ha destruido el correspondiente a la hoja de propiedades y todas las páginas de windows. Se conservarán los propios objetos. Normalmente, se recuperará los datos desde el [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objetos después `DoModal` devuelve IDOK.

Para mostrar una hoja de propiedades no modal, llame a [crear](#create) en su lugar.

Cuando se crea una página de propiedades de su recurso de cuadro de diálogo correspondiente, que puede causar una excepción de primera oportunidad. Esto da como resultado de la página de propiedades, cambiar el estilo del recurso de cuadro de diálogo para el estilo requerido antes de crea la página. Dado que los recursos son normalmente de solo lectura, esto produce una excepción. El sistema controla la excepción y realiza una copia del recurso modificado. Por lo tanto, se pueden omitir las excepciones de primera oportunidad.

> [!NOTE]
>  Esta excepción debe controlarse mediante el sistema operativo si está compilando con el modelo de control de excepciones asincrónicas. Para obtener más información acerca de los modelos de control de excepciones, vea [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md). En este caso, no incluya llamadas a `CPropertySheet::DoModal` con un bloque try-catch de C++ en el que la instrucción catch controla todas las excepciones, por ejemplo, `catch (...)`. Este bloque controlaría la excepción destinada a del sistema operativo y causa un comportamiento impredecible. Sin embargo, puede utilizar C++ control de excepciones con tipos de excepción específico o control de excepciones estructurado donde se pasa la excepción de infracción de acceso al sistema operativo.

Para evitar generar esta excepción de primera oportunidad, puede garantizar manualmente que la hoja de propiedades tiene el valor correcto [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles). Deberá establecer los siguientes estilos de una hoja de propiedades:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Puede usar los siguientes estilos opcionales sin provocar una excepción de primera oportunidad:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Deshabilitar todos los demás estilos de Windows, ya que no son compatibles con las hojas de propiedades. Este Consejo no es aplicable a los estilos extendidos. Establecer estos estilos estándares adecuadamente garantizará que la hoja de propiedades no tiene que modificarse y evitará que se genera la excepción de primera oportunidad.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet:: AddPage](#addpage).

##  <a name="enablestackedtabs"></a>  CPropertySheet::EnableStackedTabs

Indica si las filas de pestañas en una hoja de propiedades de la pila.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parámetros

*bStacked*<br/>
Indica si se habilitan apiladas pestañas en la hoja de propiedades. Deshabilitar apiladas filas de etiquetas estableciendo *bStacked* en FALSE.

### <a name="remarks"></a>Comentarios

De forma predeterminada, si una hoja de propiedades tiene varias pestañas que caben en una sola fila en el ancho de la hoja de propiedades, las pestañas se apilarán en varias filas. Para utilizar las pestañas de desplazamiento en lugar de pestañas de apilamiento, llame a `EnableStackedTabs` con *bStacked* establecida en FALSE antes de llamar a [DoModal](#domodal) o [crear](#create).

Debe llamar a `EnableStackedTabs` cuando crea una hoja de propiedades no modal o modal. Para incorporar este estilo en un `CPropertySheet`-clase derivada, escribe un controlador de mensajes para WM_CREATE. En la versión invalidada de [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), llame a `EnableStackedTabs( FALSE )` antes de llamar a la implementación de la clase base.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

##  <a name="enddialog"></a>  CPropertySheet::EndDialog

Finaliza la hoja de propiedades.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parámetros

*nEndID*<br/>
Identificador que se usará como valor devuelto de la hoja de propiedades.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama el marco de trabajo cuando se presiona el correcto, cancelar o botón de cierre. Llamada a esta función miembro si produce un evento que debe cerrar la hoja de propiedades.

Esta función miembro solo se usa con un cuadro de diálogo modal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::PressButton](#pressbutton).

##  <a name="getactiveindex"></a>  CPropertySheet::GetActiveIndex

Obtiene el número de índice de la página activa de la ventana de hoja de propiedades y, a continuación, utiliza el número de índice devuelto como parámetro para `GetPage`.

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El número de índice de la página activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="getactivepage"></a>  CPropertySheet::GetActivePage

Recupera la página activa de la ventana de hoja de propiedades.

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
Índice de la página que desee, empezando por 0. Debe ser entre 0 y menor que el número de páginas en la hoja de propiedades, ambos inclusive.

### <a name="return-value"></a>Valor devuelto

El puntero a la página correspondiente a la *nPage* parámetro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpagecount"></a>  CPropertySheet::GetPageCount

Determina el número de páginas actualmente en la hoja de propiedades.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de páginas en la hoja de propiedades.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

##  <a name="getpageindex"></a>  CPropertySheet::GetPageIndex

Recupera el número de índice de la página especificada en la hoja de propiedades.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Apunta a la página con el índice que se va a calcular. No puede ser nulo.

### <a name="return-value"></a>Valor devuelto

El número de índice de una página.

### <a name="remarks"></a>Comentarios

Por ejemplo, podría usar `GetPageIndex` para obtener el índice de página para poder usar [SetActivePage](#setactivepage) o [GetPage](#getpage).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="gettabcontrol"></a>  CPropertySheet::GetTabControl

Recupera un puntero a un control de ficha para realizar algo específico para el control de ficha (es decir, para usar cualquiera de las API en [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un control de ficha.

### <a name="remarks"></a>Comentarios

Por ejemplo, llamar a esta función miembro si desea agregar mapas de bits a cada una de las pestañas durante la inicialización.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

##  <a name="m_psh"></a>  CPropertySheet::m_psh

Una estructura cuyos miembros almacenan las características de [PROPSHEETHEADER](/windows/desktop/api/prsht/ns-prsht-_propsheetheadera_v2).

### <a name="remarks"></a>Comentarios

Utilice esta estructura para inicializar la apariencia de la hoja de propiedades una vez que se construye pero antes de que se muestre con la [DoModal](#domodal) función miembro. Por ejemplo, establecer el *dwSize* miembro de `m_psh` al tamaño que desee tener la hoja de propiedades.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea PROPSHEETHEADER en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

##  <a name="mapdialogrect"></a>  CPropertySheet::MapDialogRect

Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de la pantalla.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a un [RECT](/previous-versions/dd162897\(v=vs.85\)) estructura o [CRect](../../atl-mfc-shared/reference/crect-class.md) coordina el objeto que contiene el cuadro de diálogo que para se va a convertir.

### <a name="remarks"></a>Comentarios

Unidades de cuadro de diálogo se indican en términos de la unidad de base de cuadro de diálogo actual derivada del ancho medio y alto de caracteres de la fuente utilizada para el texto del cuadro de diálogo. Una unidad horizontal es una cuarta parte de la unidad de base ancho del cuadro de diálogo y una unidad vertical es una octava parte de la unidad de alto de la base del cuadro de diálogo.

El [GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) función Windows devuelve información de tamaño de la fuente del sistema, pero puede especificar una fuente distinta para cada hoja de propiedades si usa el estilo DS_SETFONT en el archivo de definición de recursos. El [MapDialogRect](/windows/desktop/api/winuser/nf-winuser-mapdialogrect) función de Windows, se describe en el SDK de Windows, usa la fuente adecuada para este cuadro de diálogo.

El `MapDialogRect` función miembro reemplaza las unidades de cuadro de diálogo en *lpRect* con pantalla (píxeles) de las unidades para que el rectángulo se puede usar para crear un cuadro de diálogo o colocar un control dentro de un cuadro.

##  <a name="oninitdialog"></a>  CPropertySheet::OnInitDialog

Invalidaciones para aumentar la inicialización de la hoja de propiedades.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

Especifica si la aplicación ha establecido el foco de entrada en uno de los controles en la hoja de propiedades. Si `OnInitDialog` devuelve distinto de cero, Windows establece el foco de entrada en el primer control en la hoja de propiedades. La aplicación puede devolver 0 solo si se establece explícitamente el foco de entrada para uno de los controles en la hoja de propiedades.

### <a name="remarks"></a>Comentarios

Esta función miembro se llama en respuesta al mensaje WM_INITDIALOG. Este mensaje se envía a la hoja de propiedades durante el [crear](#create) o [DoModal](#domodal) llamadas, que se producen inmediatamente antes de que se muestre la hoja de propiedades.

Reemplace esta función miembro si tiene que realizar un procesamiento especial cuando se inicializa la hoja de propiedades. En la versión invalidada, llame primero a la clase base `OnInitDialog` pero pasar por alto el valor devuelto. Normalmente devolverá TRUE desde la función miembro reemplazado.

No es necesario una entrada de mapa de mensajes para esta función miembro.

##  <a name="pressbutton"></a>  CPropertySheet::PressButton

Simula la elección del botón especificado en una hoja de propiedades.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parámetros

*nButton*<br/>
nBotón: Identifica que se pulse el botón. Este parámetro puede ser uno de los siguientes valores:

- PSBTN_BACK elige el botón Atrás.

- PSBTN_NEXT elige el botón siguiente.

- PSBTN_FINISH elige el botón Finalizar.

- PSBTN_OK elige el botón Aceptar.

- PSBTN_APPLYNOW elige el botón Aplicar ahora.

- PSBTN_CANCEL elige el botón Cancelar.

- PSBTN_HELP elige el botón Ayuda.

### <a name="remarks"></a>Comentarios

Consulte [PSM_PRESSBUTTON](/windows/desktop/Controls/psm-pressbutton) para obtener más información sobre el mensaje Pressbutton del SDK de Windows.

Una llamada a `PressButton` no enviará el [PSN_APPLY](/windows/desktop/Controls/psn-apply) notificación de una página de propiedades para el marco de trabajo. Para enviar esta notificación, llame a [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

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
Índice de la página que se va a quitar. Debe ser entre 0 y menor que el número de páginas en la hoja de propiedades, ambos inclusive.

### <a name="remarks"></a>Comentarios

El [CPropertyPage](../../mfc/reference/cpropertypage-class.md) propio objeto no se destruye hasta que el propietario de la `CPropertySheet` se cierra la ventana.

##  <a name="setactivepage"></a>  CPropertySheet::SetActivePage

Cambia la página activa.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
Índice de la página para establecer. Debe ser entre 0 y menor que el número de páginas en la hoja de propiedades, ambos inclusive.

*pPage*<br/>
Hace referencia a la página para establecer en la hoja de propiedades. No puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se activa correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Por ejemplo, utilice `SetActivePage` si una acción del usuario en una sola página provocaría que otra página para convertirse en la página activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::GetActivePage](#getactivepage).

##  <a name="setfinishtext"></a>  CPropertySheet::SetFinishText

Establece el texto en el botón de comando de finalizar.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Señala el texto que se mostrará en el botón de comando de finalizar.

### <a name="remarks"></a>Comentarios

Llame a `SetFinishText` para mostrar el texto en el botón de comando finalizar y ocultar los botones Atrás y siguiente después de que el usuario complete la acción en la última página del asistente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="settitle"></a>  CPropertySheet::SetTitle

Especifica el título de la hoja de propiedades (es decir, el texto mostrado en la barra de título de una ventana de marco).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Especifica el estilo del título de la hoja de propiedades. El estilo debe especificarse en 0 o como PSH_PROPTITLE. Si se establece el estilo como PSH_PROPTITLE, aparece la palabra "Propiedades" después del texto especificado como el título. Por ejemplo, al llamar a `SetTitle`("Simple", PSH_PROPTITLE) dará como resultado un título de la hoja de propiedades de propiedades simples"."

*lpszText*<br/>
Señala el texto que se usará como el título en la barra de título de la hoja de propiedades.

### <a name="remarks"></a>Comentarios

De forma predeterminada, una hoja de propiedades usa el parámetro de la leyenda en el constructor de la hoja de propiedades.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

##  <a name="setwizardbuttons"></a>  CPropertySheet::SetWizardButtons

Habilita o deshabilita el botón Atrás, siguiente o finalizar en una hoja de propiedades del asistente.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Un conjunto de marcadores que personalizan la función y la apariencia de los botones del asistente. Este parámetro puede ser una combinación de los siguientes valores:

- Botón Atrás PSWIZB_BACK

- Botón PSWIZB_NEXT siguiente

- Botón Finalizar PSWIZB_FINISH

- Botón PSWIZB_DISABLEDFINISH deshabilitado finalizar

### <a name="remarks"></a>Comentarios

Llame a `SetWizardButtons` solo después de que el cuadro de diálogo está abierto; no se puede llamar a `SetWizardButtons` antes de llamar a [DoModal](#domodal). Normalmente, debe llamar a `SetWizardButtons` desde [notificaciones CPropertyPage:: OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Si desea cambiar el texto en el botón Finalizar u ocultar la próxima y Back botones una vez que el usuario se ha completado el asistente, llamada [SetFinishText](#setfinishtext). Tenga en cuenta que se comparte el mismo botón para finalizar y siguiente. Puede mostrar un acabado o un botón siguiente al mismo tiempo, pero no ambos.

### <a name="example"></a>Ejemplo

Un `CPropertySheet` tiene tres páginas de propiedades de asistente: `CStylePage`, `CColorPage`, y `CShapePage`.  El fragmento de código siguiente muestra cómo habilitar y deshabilitar el **Atrás** y **siguiente** botones en la página de propiedades del asistente.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

##  <a name="setwizardmode"></a>  CPropertySheet::SetWizardMode

Establece una página de propiedades como un asistente.

```
void SetWizardMode();
```

### <a name="remarks"></a>Comentarios

Una característica clave de una página de propiedades del asistente es que el usuario navega junto con o finalizar, realizar una copia y botones en lugar de pestañas para cancelar.

Llame a `SetWizardMode` antes de llamar a [DoModal](#domodal). Después de llamar a `SetWizardMode`, `DoModal` devolverá ID_WIZFINISH (si el usuario cierra con el botón Finalizar) o IDCANCEL.

`SetWizardMode` establece la marca PSH_WIZARD.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Vea también

[MFC Sample CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[MFC Sample CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo SNAPVW de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
