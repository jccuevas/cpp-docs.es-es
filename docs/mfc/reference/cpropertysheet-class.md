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
ms.openlocfilehash: 167c99f734e4538ff2704e032a6ca98fb1d82004
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363947"
---
# <a name="cpropertysheet-class"></a>CPropertySheet (clase)

Representa hojas de propiedades, también conocidas como cuadros de diálogo de pestaña.

## <a name="syntax"></a>Sintaxis

```
class CPropertySheet : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropertySheet::CPropertySheet](#cpropertysheet)|Construye un objeto `CPropertySheet`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropertySheet::AddPage](#addpage)|Agrega una página a la hoja de propiedades.|
|[CPropertySheet::Construct](#construct)|Construye un objeto `CPropertySheet`.|
|[CPropertySheet::Create](#create)|Muestra una hoja de propiedades no quede sin cambios.|
|[CPropertySheet::DoModal](#domodal)|Muestra una hoja de propiedades modal.|
|[CPropertySheet::EnableStackedTabs](#enablestackedtabs)|Indica si la hoja de propiedades utiliza pestañas apiladas o de desplazamiento.|
|[CPropertySheet::EndDialog](#enddialog)|Termina la hoja de propiedades.|
|[CPropertySheet::GetActiveIndex](#getactiveindex)|Recupera el índice de la página activa de la hoja de propiedades.|
|[CPropertySheet::GetActivePage](#getactivepage)|Devuelve el objeto de página activo.|
|[CPropertySheet::GetPage](#getpage)|Recupera un puntero a la página especificada.|
|[CPropertySheet::GetPageCount](#getpagecount)|Recupera el número de páginas de la hoja de propiedades.|
|[CPropertySheet::GetPageIndex](#getpageindex)|Recupera el índice de la página especificada de la hoja de propiedades.|
|[CPropertySheet::GetTabControl](#gettabcontrol)|Recupera un puntero a un control de ficha.|
|[CPropertySheet::MapDialogRect](#mapdialogrect)|Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.|
|[CPropertySheet::OnInitDialog](#oninitdialog)|Reemplazar para aumentar la inicialización de la hoja de propiedades.|
|[CPropertySheet::PressButton](#pressbutton)|Simula la elección del botón especificado en una hoja de propiedades.|
|[CPropertySheet::RemovePage](#removepage)|Quita una página de la hoja de propiedades.|
|[CPropertySheet::SetActivePage](#setactivepage)|Establece mediante programación el objeto de página activo.|
|[CPropertySheet::SetFinishText](#setfinishtext)|Establece el texto del botón Finalizar.|
|[CPropertySheet::SetTitle](#settitle)|Establece el título de la hoja de propiedades.|
|[CPropertySheet::SetWizardButtons](#setwizardbuttons)|Habilita los botones del asistente.|
|[CPropertySheet::SetWizardMode](#setwizardmode)|Habilita el modo asistente.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPropertySheet::m_psh](#m_psh)|La estructura [PROPSHEETHEADER de](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) Windows. Proporciona acceso a los parámetros básicos de la hoja de propiedades.|

## <a name="remarks"></a>Observaciones

Una hoja de `CPropertySheet` propiedades consta de un objeto y uno o varios [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objetos. El marco de trabajo muestra una hoja de propiedades como una ventana con un conjunto de índices de tabulación y un área que contiene la página seleccionada actualmente. El usuario navega a una página específica mediante la pestaña adecuada.

`CPropertySheet`proporciona compatibilidad con la estructura [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2) ampliada introducida en Windows 98 y Windows NT 2000. La estructura contiene indicadores y miembros adicionales que admiten el uso de un mapa de bits de fondo "marca de agua".

Para mostrar estas nuevas imágenes automáticamente en el objeto de hoja de propiedades, pase valores válidos para las imágenes de mapa de bits y paleta en la llamada a [CPropertySheet::Construct](#construct) o [CPropertySheet::CPropertySheet](#cpropertysheet).

Aunque `CPropertySheet` no se deriva de [CDialog](../../mfc/reference/cdialog-class.md), administrar un `CPropertySheet` objeto es como administrar un `CDialog` objeto. Por ejemplo, la creación de una hoja de propiedades requiere una construcción de dos partes: llame al constructor y, a continuación, llame a [DoModal](#domodal) para una hoja de propiedades modal o [Crear](#create) para una hoja de propiedades no modal. `CPropertySheet`tiene dos tipos de constructores: [CPropertySheet::Construct](#construct) y [CPropertySheet::CPropertySheet](#cpropertysheet).

Al construir `CPropertySheet` un objeto, algunos [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana pueden provocar una excepción de primera oportunidad. Esto resulta del sistema que intenta cambiar el estilo de la hoja de propiedades antes de crear la hoja. Para evitar esta excepción, asegúrese de establecer `CPropertySheet`los siguientes estilos al crear:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Los siguientes estilos son opcionales y no provocarán la excepción de primera oportunidad:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Cualquier `Window Styles` otro está prohibido y no debe habilitarlos.

El intercambio de `CPropertySheet` datos entre un objeto y un `CDialog` objeto externo es similar al intercambio de datos con un objeto. La diferencia importante es que la configuración de una hoja `CPropertyPage` de propiedades `CPropertySheet` suele ser variables miembro de los objetos en lugar del propio objeto.

Puede crear un tipo de cuadro de diálogo de ficha denominado asistente, que consta de una hoja de propiedades con una secuencia de páginas de propiedades que guían al usuario a través de los pasos de una operación, como la configuración de un dispositivo o la creación de un boletín informativo. En un cuadro de diálogo de ficha de tipo asistente, las páginas de propiedades no tienen pestañas y solo una página de propiedades está visible a la vez. Además, en lugar de tener los botones **Aceptar** y **Aplicar ahora,** un cuadro de diálogo de ficha de tipo asistente tiene un botón **Atrás,** un botón **Siguiente** o **Finalizar,** un botón **Cancelar** y un botón **Ayuda.**

Para crear un cuadro de diálogo de tipo asistente, siga los mismos pasos que seguiría para crear una hoja de propiedades estándar, pero llame a [SetWizardMode](#setwizardmode) antes de llamar a [DoModal](#domodal). Para habilitar los botones del asistente, llame a [SetWizardButtons](#setwizardbuttons), mediante indicadores para personalizar su función y apariencia. Para habilitar el botón **Finalizar,** llame a [SetFinishText](#setfinishtext) después de que el usuario haya realizado una acción en la última página del asistente.

Para obtener más información `CPropertySheet` acerca de cómo utilizar objetos, vea el artículo Hojas de propiedades [y páginas](../../mfc/property-sheets-and-property-pages-in-mfc.md)de propiedades .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPropertySheet`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdlgs.h

## <a name="cpropertysheetaddpage"></a><a name="addpage"></a>CPropertySheet::AddPage

Agrega la página proporcionada con la pestaña más a la derecha en la hoja de propiedades.

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Apunta a la página que se va a agregar a la hoja de propiedades. No puede ser NULL.

### <a name="remarks"></a>Observaciones

Agregue páginas a la hoja de propiedades en el orden de izquierda a derecha que desea que aparezcan.

`AddPage`agrega el [CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage) objeto `CPropertySheet` a la lista de páginas del objeto, pero en realidad no crea la ventana para la página. El marco de trabajo pospone la creación de la ventana de la página hasta que el usuario selecciona esa página.

Cuando se agrega una `AddPage`página `CPropertySheet` de propiedades `CPropertyPage`mediante , el es el elemento primario del archivo . Para obtener acceso a la hoja de propiedades desde la página de propiedades, llame a [CWnd::GetParent](../../mfc/reference/cwnd-class.md#getparent).

No es necesario esperar hasta la creación de `AddPage`la ventana de la hoja de propiedades para llamar a . Normalmente, llamará `AddPage` antes de llamar a [DoModal](#domodal) o [Create](#create).

Si llama `AddPage` después de mostrar la página de propiedades, la fila de pestaña reflejará la página recién agregada.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#129](../../mfc/codesnippet/cpp/cpropertysheet-class_1.cpp)]

## <a name="cpropertysheetconstruct"></a><a name="construct"></a>CPropertySheet::Construct

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
ID del título que se usará para la hoja de propiedades.

*pParentWnd*<br/>
Puntero a la ventana primaria de la hoja de propiedades. Si NULL, la ventana primaria será la ventana principal de la aplicación.

*iSelectPage*<br/>
El índice de la página que estará inicialmente en la parte superior. El valor predeterminado es la primera página agregada a la hoja.

*pszCaption*<br/>
Puntero a una cadena que contiene el título que se usará para la hoja de propiedades. No puede ser NULL.

*hbmWatermark*<br/>
Controle el mapa de bits de marca de agua de la página de propiedades.

*hpalWatermark*<br/>
Controle la paleta del mapa de bits de marca de agua y/o el mapa de bits de encabezado.

*hbmHeader*<br/>
Controlar el mapa de bits de encabezado de la página de propiedades.

### <a name="remarks"></a>Observaciones

Llame a esta función miembro si uno de los constructores de clase aún no se ha llamado. Por ejemplo, `Construct` llame al declarar o `CPropertySheet` asignar matrices de objetos. En el caso de matrices, debe llamar `Construct` a cada miembro de la matriz.

Para mostrar la hoja de propiedades, llame a [DoModal](#domodal) o [Create](#create). La cadena contenida en el primer parámetro se colocará en la barra de título de la hoja de propiedades.

Puede mostrar imágenes de marca de agua y/o `Construct`encabezado automáticamente si utiliza los prototipos tercero o cuarto de , enumerados anteriormente, y pasa valores válidos para los parámetros *hbmWatermark*, *hpalWatermark*y/o *hbmHeader.*

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `Construct`en qué circunstancias se llamaría .

[!code-cpp[NVC_MFCDocView#130](../../mfc/codesnippet/cpp/cpropertysheet-class_2.cpp)]

## <a name="cpropertysheetcpropertysheet"></a><a name="cpropertysheet"></a>CPropertySheet::CPropertySheet

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
ID del título que se usará para la hoja de propiedades.

*pParentWnd*<br/>
Apunta a la ventana principal de la hoja de propiedades. Si NULL, la ventana primaria será la ventana principal de la aplicación.

*iSelectPage*<br/>
El índice de la página que estará inicialmente en la parte superior. El valor predeterminado es la primera página agregada a la hoja.

*pszCaption*<br/>
Apunta a una cadena que contiene el título que se usará para la hoja de propiedades. No puede ser NULL.

*hbmWatermark*<br/>
Identificador del mapa de bits de fondo de la hoja de propiedades.

*hpalWatermark*<br/>
Identificador de la paleta del mapa de bits de marca de agua y/o mapa de bits de encabezado.

*hbmHeader*<br/>
Identificador del mapa de bits de encabezado de la página de propiedades.

### <a name="remarks"></a>Observaciones

Para mostrar la hoja de propiedades, llame a [DoModal](#domodal) o [Create](#create). La cadena contenida en el primer parámetro se colocará en la barra de título de la hoja de propiedades.

Si tiene varios parámetros (por ejemplo, si [Construct](#construct) utiliza una `CPropertySheet`matriz), utilice Construct en lugar de .

Puede mostrar imágenes de marca de agua y/o `CPropertySheet`encabezado automáticamente si utiliza los prototipos tercero o cuarto de , arriba, y pasa valores válidos para los parámetros *hbmWatermark*, *hpalWatermark*y/o *hbmHeader.*

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#131](../../mfc/codesnippet/cpp/cpropertysheet-class_3.cpp)]

## <a name="cpropertysheetcreate"></a><a name="create"></a>CPropertySheet::Create

Muestra una hoja de propiedades no quede sin cambios.

```
virtual BOOL Create(CWnd* pParentWnd = NULL,
    DWORD dwStyle = (DWORD)-1,
    DWORD dwExStyle = 0);
```

### <a name="parameters"></a>Parámetros

*pParentWnd*<br/>
Apunta a la ventana principal. Si NULL, el elemento primario es el escritorio.

*dwStyle*<br/>
Estilos de ventana para hoja de propiedades. Para obtener una lista completa de los estilos disponibles, consulte [Estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles)de ventana .

*dwExStyle*<br/>
Estilos de ventana extendidos para la hoja de propiedades. Para obtener una lista completa de los estilos disponibles, consulte Estilos de [ventana extendidos](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

La llamada `Create` a puede estar dentro del constructor, o puede llamarlo después de invocar el constructor.

El estilo predeterminado, expresado pasando -1 como *dwStyle*, es en realidad WS_SYSMENU&#124;WS_POPUP&#124;&#124;WS_CAPTION&#124;&#124;DS_MODALFRAME DS_MODALFRAME WS_VISIBLE DS_CONTEXTHELP&#124;. El estilo de ventana extendida predeterminado, expresado pasando 0 como *dwExStyle*, es realmente WS_EX_DLGMODALFRAME.

La `Create` función miembro devuelve inmediatamente después de crear la hoja de propiedades. Para destruir la hoja de propiedades, llame a [CWnd::DestroyWindow](../../mfc/reference/cwnd-class.md#destroywindow).

Las hojas de propiedades no modales que se muestran con una llamada para `Create` no tener los botones Aceptar, Cancelar, Aplicar ahora y Ayuda como lo hacen las hojas de propiedades modales. Los botones deseados deben ser creados por el usuario.

Para mostrar una hoja de propiedades modal, llame a [DoModal](#domodal) en su lugar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#132](../../mfc/codesnippet/cpp/cpropertysheet-class_4.cpp)]

[!code-cpp[NVC_MFCDocView#133](../../mfc/codesnippet/cpp/cpropertysheet-class_5.cpp)]

## <a name="cpropertysheetdomodal"></a><a name="domodal"></a>CPropertySheet::DoModal

Muestra una hoja de propiedades modal.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Valor devuelto

IDOK o IDCANCEL si la función se realizó correctamente; de lo contrario 0 o -1. Si la hoja de propiedades se ha establecido `DoModal` como asistente (consulte [SetWizardMode](#setwizardmode)), devuelve ID_WIZFINISH o IDCANCEL.

### <a name="remarks"></a>Observaciones

El valor devuelto corresponde al identificador del control que cerró la hoja de propiedades. Después de que esta función vuelve, las ventanas correspondientes a la hoja de propiedades y todas las páginas se habrán destruido. Los objetos en sí seguirán existiendo. Normalmente, recuperará datos de la [CPropertyPage](../../mfc/reference/cpropertypage-class.md) objetos después `DoModal` de devuelve IDOK.

Para mostrar una hoja de propiedades no quede sin cambios, llame a [Crear](#create) en su lugar.

Cuando se crea una página de propiedades a partir de su recurso de cuadro de diálogo correspondiente, puede provocar una excepción de primera oportunidad. Esto resulta de la página de propiedades cambiando el estilo del recurso de cuadro de diálogo al estilo necesario antes de crear la página. Dado que los recursos suelen ser de solo lectura, esto provoca una excepción. El sistema controla la excepción y realiza una copia del recurso modificado. Por lo tanto, se puede omitir la excepción de primera oportunidad.

> [!NOTE]
> Esta excepción debe ser controlada por el sistema operativo si está compilando con el modelo de control de excepciones asincrónico. Para obtener más información acerca de los modelos de control de excepciones, vea [/EH (modelo](../../build/reference/eh-exception-handling-model.md)de control de excepciones) . En este caso, no `CPropertySheet::DoModal` ajuste las llamadas con un bloque try-catch de C++ en el que catch controle todas las excepciones, por ejemplo, `catch (...)`. Este bloque controlaría la excepción destinada al sistema operativo y provocaría un comportamiento impredecible. Sin embargo, puede usar de forma segura el control de excepciones de C++ con tipos de excepción específicos o el control de excepciones estructurado donde la excepción de infracción de acceso se pasa al sistema operativo.

Para evitar generar esta excepción de primera oportunidad, puede garantizar manualmente que la hoja de propiedades tiene los estilos de [ventana correctos.](../../mfc/reference/styles-used-by-mfc.md#window-styles) Debe establecer los siguientes estilos para una hoja de propiedades:

- DS_3DLOOK

- DS_CONTROL

- WS_CHILD

- WS_TABSTOP

Puede utilizar los siguientes estilos opcionales sin provocar una excepción de primera oportunidad:

- DS_SHELLFONT

- DS_LOCALEDIT

- WS_CLIPCHILDREN

Deshabilite todos los demás estilos de Windows porque no son compatibles con las hojas de propiedades. Este consejo no se aplica a los estilos extendidos. Establecer estos estilos estándar de forma adecuada garantizará que la hoja de propiedades no tiene que modificarse y evitará generar la excepción de primera oportunidad.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::AddPage](#addpage).

## <a name="cpropertysheetenablestackedtabs"></a><a name="enablestackedtabs"></a>CPropertySheet::EnableStackedTabs

Indica si se deben apilar filas de pestañas en una hoja de propiedades.

```
void EnableStackedTabs(BOOL bStacked);
```

### <a name="parameters"></a>Parámetros

*bStacked*<br/>
Indica si las pestañas apiladas están habilitadas en la hoja de propiedades. Deshabilite las filas apiladas de etiquetas estableciendo *bStacked en* FALSE.

### <a name="remarks"></a>Observaciones

De forma predeterminada, si una hoja de propiedades tiene más pestañas de las que caben en una sola fila en el ancho de la hoja de propiedades, las pestañas se apilarán en varias filas. Para usar pestañas de desplazamiento en lugar `EnableStackedTabs` de pestañas de apilamiento, llame con *bStacked* establecido en FALSE antes de llamar a [DoModal](#domodal) o [Create](#create).

Debe llamar `EnableStackedTabs` al crear una hoja de propiedades modal o no modal. Para incorporar este `CPropertySheet`estilo en una clase derivada, escriba un controlador de mensajes para WM_CREATE. En la versión invalidada de [CWnd::OnCreate](../../mfc/reference/cwnd-class.md#oncreate), llame `EnableStackedTabs( FALSE )` antes de llamar a la implementación de la clase base.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#134](../../mfc/codesnippet/cpp/cpropertysheet-class_6.cpp)]

## <a name="cpropertysheetenddialog"></a><a name="enddialog"></a>CPropertySheet::EndDialog

Termina la hoja de propiedades.

```
void EndDialog(int nEndID);
```

### <a name="parameters"></a>Parámetros

*nEndID*<br/>
Identificador que se utilizará como valor devuelto de la hoja de propiedades.

### <a name="remarks"></a>Observaciones

El marco de trabajo llama a esta función miembro cuando se presiona el botón Aceptar, Cancelar o Cerrar. Llame a esta función miembro si se produce un evento que debe cerrar la hoja de propiedades.

Esta función miembro solo se utiliza con un cuadro de diálogo modal.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::PressButton](#pressbutton).

## <a name="cpropertysheetgetactiveindex"></a><a name="getactiveindex"></a>CPropertySheet::GetActiveIndex

Obtiene el número de índice de la página activa de la ventana de `GetPage`la hoja de propiedades y, a continuación, utiliza el número de índice devuelto como parámetro para .

```
int GetActiveIndex() const;
```

### <a name="return-value"></a>Valor devuelto

El número de índice de la página activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgetactivepage"></a><a name="getactivepage"></a>CPropertySheet::GetActivePage

Recupera la página activa de la ventana de la hoja de propiedades.

```
CPropertyPage* GetActivePage() const;
```

### <a name="return-value"></a>Valor devuelto

El puntero a la página activa.

### <a name="remarks"></a>Observaciones

Utilice esta función miembro para realizar alguna acción en la página activa.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#135](../../mfc/codesnippet/cpp/cpropertysheet-class_7.cpp)]

## <a name="cpropertysheetgetpage"></a><a name="getpage"></a>CPropertySheet::GetPage

Devuelve un puntero a la página especificada en esta hoja de propiedades.

```
CPropertyPage* GetPage(int nPage) const;
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
Indice de la página deseada, a partir de 0. Debe estar entre 0 y uno menos que el número de páginas de la hoja de propiedades, ambos inclusive.

### <a name="return-value"></a>Valor devuelto

El puntero a la página correspondiente a la *nPage* parámetro.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpagecount"></a><a name="getpagecount"></a>CPropertySheet::GetPageCount

Determina el número de páginas actualmente en la hoja de propiedades.

```
int GetPageCount() const;
```

### <a name="return-value"></a>Valor devuelto

El número de páginas de la hoja de propiedades.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertyPage::OnWizardFinish](../../mfc/reference/cpropertypage-class.md#onwizardfinish).

## <a name="cpropertysheetgetpageindex"></a><a name="getpageindex"></a>CPropertySheet::GetPageIndex

Recupera el número de índice de la página especificada en la hoja de propiedades.

```
int GetPageIndex(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Apunta a la página con el índice que se va a encontrar. No puede ser NULL.

### <a name="return-value"></a>Valor devuelto

El número de índice de una página.

### <a name="remarks"></a>Observaciones

Por ejemplo, usaría `GetPageIndex` para obtener el índice de página con el fin de utilizar [SetActivePage](#setactivepage) o [GetPage](#getpage).

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetgettabcontrol"></a><a name="gettabcontrol"></a>CPropertySheet::GetTabControl

Recupera un puntero a un control de ficha para hacer algo específico del control de ficha (es decir, para usar cualquiera de las API en [CTabCtrl](../../mfc/reference/ctabctrl-class.md)).

```
CTabCtrl* GetTabControl() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a un control de ficha.

### <a name="remarks"></a>Observaciones

Por ejemplo, llame a esta función miembro si desea agregar mapas de bits a cada una de las fichas durante la inicialización.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#136](../../mfc/codesnippet/cpp/cpropertysheet-class_8.cpp)]

## <a name="cpropertysheetm_psh"></a><a name="m_psh"></a>CPropertySheet::m_psh

Estructura cuyos miembros almacenan las características de [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2).

### <a name="remarks"></a>Observaciones

Utilice esta estructura para inicializar la apariencia de la hoja de propiedades después de que se construye, pero antes de que se muestra con el [DoModal](#domodal) función miembro. Por ejemplo, establezca el `m_psh` miembro *dwSize* en el tamaño que desea que tenga la hoja de propiedades.

Para obtener más información sobre esta estructura, incluida una lista de sus miembros, vea PROPSHEETHEADER en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#143](../../mfc/codesnippet/cpp/cpropertysheet-class_9.cpp)]

## <a name="cpropertysheetmapdialogrect"></a><a name="mapdialogrect"></a>CPropertySheet::MapDialogRect

Convierte las unidades de cuadro de diálogo de un rectángulo en unidades de pantalla.

```
void MapDialogRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) que contiene las coordenadas del cuadro de diálogo que se van a convertir.

### <a name="remarks"></a>Observaciones

Las unidades de cuadro de diálogo se indican en términos de la unidad base del cuadro de diálogo actual derivada de la anchura y la altura medias de los caracteres de la fuente utilizada para el texto del cuadro de diálogo. Una unidad horizontal es una cuarta parte de la unidad de ancho base del cuadro de diálogo y una unidad vertical es una octava parte de la unidad de altura base del cuadro de diálogo.

La función de Windows [GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) devuelve información de tamaño para la fuente del sistema, pero puede especificar una fuente diferente para cada hoja de propiedades si usa el estilo DS_SETFONT en el archivo de definición de recursos. La función [MapDialogRect](/windows/win32/api/winuser/nf-winuser-mapdialogrect) de Windows, que se describe en el Windows SDK, usa la fuente adecuada para este cuadro de diálogo.

La `MapDialogRect` función miembro reemplaza las unidades de cuadro de diálogo en *lpRect* con unidades de pantalla (píxeles) para que el rectángulo se puede utilizar para crear un cuadro de diálogo o colocar un control dentro de un cuadro.

## <a name="cpropertysheetoninitdialog"></a><a name="oninitdialog"></a>CPropertySheet::OnInitDialog

Reemplazaciones para aumentar la inicialización de la hoja de propiedades.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Valor devuelto

Especifica si la aplicación ha establecido el foco de entrada en uno de los controles de la hoja de propiedades. Si `OnInitDialog` devuelve distinto de cero, Windows establece el foco de entrada en el primer control de la hoja de propiedades. La aplicación solo puede devolver 0 si ha establecido explícitamente el foco de entrada en uno de los controles de la hoja de propiedades.

### <a name="remarks"></a>Observaciones

Esta función miembro se llama en respuesta al mensaje de WM_INITDIALOG. Este mensaje se envía a la hoja de propiedades durante el [Create](#create) o [DoModal](#domodal) llamadas, que se producen inmediatamente antes de que se muestre la hoja de propiedades.

Invalide esta función miembro si necesita realizar un procesamiento especial cuando se inicializa la hoja de propiedades. En la versión reemplazada, primero `OnInitDialog` llame a la clase base pero ignore su valor devuelto. Normalmente devolverá TRUE desde la función miembro invalidada.

No necesita una entrada de mapa de mensajes para esta función miembro.

## <a name="cpropertysheetpressbutton"></a><a name="pressbutton"></a>CPropertySheet::PressButton

Simula la elección del botón especificado en una hoja de propiedades.

```
void PressButton(int nButton);
```

### <a name="parameters"></a>Parámetros

*nButton*<br/>
nButton : Identifica el botón que se va a pulsar. Este parámetro puede ser uno de los siguientes valores:

- PSBTN_BACK Selecciona el botón Atrás.

- PSBTN_NEXT Selecciona el botón Siguiente.

- PSBTN_FINISH Selecciona el botón Finalizar.

- PSBTN_OK Selecciona el botón Aceptar.

- PSBTN_APPLYNOW Selecciona el botón Aplicar ahora.

- PSBTN_CANCEL Selecciona el botón Cancelar.

- PSBTN_HELP Selecciona el botón Ayuda.

### <a name="remarks"></a>Observaciones

Consulte [PSM_PRESSBUTTON](/windows/win32/Controls/psm-pressbutton) para obtener más información sobre el mensaje de botón de presión de Windows SDK.

Una llamada `PressButton` a no enviará la notificación [PSN_APPLY](/windows/win32/Controls/psn-apply) de una página de propiedades al marco de trabajo. Para enviar esta notificación, llame a [CPropertyPage::OnOK](../../mfc/reference/cpropertypage-class.md#onok).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#137](../../mfc/codesnippet/cpp/cpropertysheet-class_10.cpp)]

## <a name="cpropertysheetremovepage"></a><a name="removepage"></a>CPropertySheet::RemovePage

Quita una página de la hoja de propiedades y destruye la ventana asociada.

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>Parámetros

*pPage*<br/>
Apunta a la página que se va a quitar de la hoja de propiedades. No puede ser NULL.

*nPage*<br/>
El índice de la página que se va a quitar. Debe estar entre 0 y uno menos que el número de páginas de la hoja de propiedades, ambos inclusive.

### <a name="remarks"></a>Observaciones

El [CPropertyPage](../../mfc/reference/cpropertypage-class.md) propio objeto no se destruye `CPropertySheet` hasta que se cierra el propietario de la ventana.

## <a name="cpropertysheetsetactivepage"></a><a name="setactivepage"></a>CPropertySheet::SetActivePage

Cambia la página activa.

```
BOOL SetActivePage(int nPage);
BOOL SetActivePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>Parámetros

*nPage*<br/>
Indice de la página que se ha establecido. Debe estar entre 0 y uno menos que el número de páginas de la hoja de propiedades, ambos inclusive.

*pPage*<br/>
Apunta a la página que se establecerá en la hoja de propiedades. No puede ser NULL.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la hoja de propiedades se activa correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Por ejemplo, `SetActivePage` use si la acción de un usuario en una página debe hacer que otra página se convierta en la página activa.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CPropertySheet::GetActivePage](#getactivepage).

## <a name="cpropertysheetsetfinishtext"></a><a name="setfinishtext"></a>CPropertySheet::SetFinishText

Establece el texto en el botón de comando Finalizar.

```
void SetFinishText(LPCTSTR lpszText);
```

### <a name="parameters"></a>Parámetros

*lpszText*<br/>
Señala el texto que se mostrará en el botón de comando Finalizar.

### <a name="remarks"></a>Observaciones

Llame `SetFinishText` para mostrar el texto en el botón de comando Finalizar y ocultar los botones Siguiente y Atrás después de que el usuario complete la acción en la última página del asistente.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsettitle"></a><a name="settitle"></a>CPropertySheet::SetTitle

Especifica el título de la hoja de propiedades (el texto que se muestra en la barra de título de una ventana de marco).

```
void SetTitle(
    LPCTSTR lpszText,
    UINT nStyle = 0);
```

### <a name="parameters"></a>Parámetros

*nStyle*<br/>
Especifica el estilo del título de la hoja de propiedades. El estilo debe especificarse en 0 o como PSH_PROPTITLE. Si el estilo se establece como PSH_PROPTITLE, la palabra "Propiedades" aparece después del texto especificado como título. Por ejemplo, `SetTitle`al llamar a ("Simple", PSH_PROPTITLE) dará como resultado un título de hoja de propiedades de "Propiedades simples."

*lpszText*<br/>
Apunta al texto que se utilizará como título en la barra de título de la hoja de propiedades.

### <a name="remarks"></a>Observaciones

De forma predeterminada, una hoja de propiedades utiliza el parámetro caption en el constructor de la hoja de propiedades.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#139](../../mfc/codesnippet/cpp/cpropertysheet-class_12.cpp)]

## <a name="cpropertysheetsetwizardbuttons"></a><a name="setwizardbuttons"></a>CPropertySheet::SetWizardButtons

Habilita o deshabilita el botón Atrás, Siguiente o Finalizar en una hoja de propiedades del asistente.

```
void SetWizardButtons(DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Conjunto de indicadores que personalizan la función y la apariencia de los botones del asistente. Este parámetro puede ser una combinación de los siguientes valores:

- botón PSWIZB_BACK Atrás

- botón PSWIZB_NEXT Siguiente

- botón PSWIZB_FINISH Finalizar

- PSWIZB_DISABLEDFINISH botón Finalizar deshabilitado

### <a name="remarks"></a>Observaciones

Llame `SetWizardButtons` sólo después de que el cuadro de diálogo esté abierto; no se puede `SetWizardButtons` llamar antes de llamar a [DoModal](#domodal). Normalmente, debe `SetWizardButtons` llamar desde [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).

Si desea cambiar el texto en el botón Finalizar u ocultar los botones Siguiente y Atrás una vez que el usuario haya completado el asistente, llame a [SetFinishText](#setfinishtext). Tenga en cuenta que el mismo botón se comparte para Finalizar y Siguiente. Puede mostrar un botón Finalizar o Siguiente a la vez, pero no ambos.

### <a name="example"></a>Ejemplo

A `CPropertySheet` tiene tres páginas `CColorPage`de `CShapePage`propiedades del asistente: `CStylePage`, , y .  El fragmento de código siguiente muestra cómo habilitar y deshabilitar los botones **Atrás** y **Siguiente** en la página de propiedades del asistente.

[!code-cpp[NVC_MFCDocView#140](../../mfc/codesnippet/cpp/cpropertysheet-class_13.cpp)]

[!code-cpp[NVC_MFCDocView#141](../../mfc/codesnippet/cpp/cpropertysheet-class_14.cpp)]

[!code-cpp[NVC_MFCDocView#138](../../mfc/codesnippet/cpp/cpropertysheet-class_11.cpp)]

## <a name="cpropertysheetsetwizardmode"></a><a name="setwizardmode"></a>CPropertySheet::SetWizardMode

Establece una página de propiedades como asistente.

```
void SetWizardMode();
```

### <a name="remarks"></a>Observaciones

Una característica clave de una página de propiedades del asistente es que el usuario navega con los botones Siguiente o Finalizar, Atrás y Cancelar en lugar de pestañas.

Llame `SetWizardMode` antes de llamar a [DoModal](#domodal). Después `SetWizardMode`de `DoModal` llamar , devolverá ID_WIZFINISH (si el usuario cierra con el botón Finalizar) o IDCANCEL.

`SetWizardMode`establece la marca PSH_WIZARD.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#142](../../mfc/codesnippet/cpp/cpropertysheet-class_15.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC CMNCTRL1](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo cmNCTRL2 de MFC](../../overview/visual-cpp-samples.md)<br/>
[Ejemplo de MFC PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[EJEMPLO de MFC SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
