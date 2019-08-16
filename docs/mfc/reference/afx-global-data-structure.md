---
title: AFX_GLOBAL_DATA (estructura)
ms.date: 11/04/2016
f1_keywords:
- AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA
- AFXGLOBALS/AFX_GLOBAL_DATA::CleanUp
- AFXGLOBALS/AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawParentBackground
- AFXGLOBALS/AFX_GLOBAL_DATA::DrawTextOnGlass
- AFXGLOBALS/AFX_GLOBAL_DATA::ExcludeTag
- AFXGLOBALS/AFX_GLOBAL_DATA::GetColor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetDirect2dFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetHandCursor
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList
- AFXGLOBALS/AFX_GLOBAL_DATA::GetITaskbarList3
- AFXGLOBALS/AFX_GLOBAL_DATA::GetNonClientMetrics
- AFXGLOBALS/AFX_GLOBAL_DATA::GetShellAutohideBars
- AFXGLOBALS/AFX_GLOBAL_DATA::GetTextHeight
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWICFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::GetWriteFactory
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::Is32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::IsD2DInitialized
- AFXGLOBALS/AFX_GLOBAL_DATA::IsDwmCompositionEnabled
- AFXGLOBALS/AFX_GLOBAL_DATA::IsHighContrastMode
- AFXGLOBALS/AFX_GLOBAL_DATA::OnSettingChange
- AFXGLOBALS/AFX_GLOBAL_DATA::RegisterWindowClass
- AFXGLOBALS/AFX_GLOBAL_DATA::ReleaseTaskBarRefs
- AFXGLOBALS/AFX_GLOBAL_DATA::Resume
- AFXGLOBALS/AFX_GLOBAL_DATA::SetLayeredAttrib
- AFXGLOBALS/AFX_GLOBAL_DATA::SetMenuFont
- AFXGLOBALS/AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateFonts
- AFXGLOBALS/AFX_GLOBAL_DATA::UpdateSysColors
- AFXGLOBALS/AFX_GLOBAL_DATA::EnableAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsAccessibilitySupport
- AFXGLOBALS/AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
- AFXGLOBALS/AFX_GLOBAL_DATA::bIsWindows7
- AFXGLOBALS/AFX_GLOBAL_DATA::clrActiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::clrInactiveCaptionGradient
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
- AFXGLOBALS/AFX_GLOBAL_DATA::m_bUseSystemFont
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurHand
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretch
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hcurStretchVert
- AFXGLOBALS/AFX_GLOBAL_DATA::m_hiconTool
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessDock
- AFXGLOBALS/AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
ms.openlocfilehash: dda3056cbed18ef93e09b52cd9d0a6b00e1db177
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507752"
---
# <a name="afx_global_data-structure"></a>AFX_GLOBAL_DATA (estructura)

La estructura `AFX_GLOBAL_DATA` contiene los campos y métodos que se utilizan para administrar el marco o personalizar el aspecto y el comportamiento de la aplicación.

## <a name="syntax"></a>Sintaxis

```
struct AFX_GLOBAL_DATA
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Crea una estructura `AFX_GLOBAL_DATA` .|
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[AFX_GLOBAL_DATA::CleanUp](#cleanup)|Libera los recursos asignados por el marco, como pinceles, fuentes y archivos DLL.|
|[AFX_GLOBAL_DATA::D2D1MakeRotateMatrix](#d2d1makerotatematrix)|Crea una transformación de giro que gire según el ángulo especificado alrededor de un punto especificado.|
|[AFX_GLOBAL_DATA::DrawParentBackground](#drawparentbackground)|Dibuja el fondo del elemento primario de un control en el área especificada.|
|[AFX_GLOBAL_DATA::DrawTextOnGlass](#drawtextonglass)|Dibuja el texto especificado en el estilo visual del tema especificado.|
|[AFX_GLOBAL_DATA::ExcludeTag](#excludetag)|Quita el par especificado de etiquetas XML de un búfer especificado.|
|[AFX_GLOBAL_DATA::GetColor](#getcolor)|Recupera el color actual del elemento de la interfaz de usuario especificado.|
|[AFX_GLOBAL_DATA::GetDirect2dFactory](#getdirect2dfactory)|Devuelve un puntero a la interfaz `ID2D1Factory` que está almacenada en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.|
|[AFX_GLOBAL_DATA::GetHandCursor](#gethandcursor)|Recupera el cursor predefinido que se parece a una mano y cuyo identificador es `IDC_HAND`.|
|[AFX_GLOBAL_DATA::GetITaskbarList](#getitaskbarlist)|Crea y almacena en los datos globales un puntero a la interfaz ITaskBarList.|
|[AFX_GLOBAL_DATA::GetITaskbarList3](#getitaskbarlist3)|Crea y almacena en los datos globales un puntero a la interfaz ITaskBarList3.|
|[AFX_GLOBAL_DATA::GetNonClientMetrics](#getnonclientmetrics)|Recupera las métricas asociadas al área no cliente de las ventanas no minimizadas.|
|[AFX_GLOBAL_DATA::GetShellAutohideBars](#getshellautohidebars)|Determina las posiciones de las barras Ocultar automáticamente del Shell.|
|[AFX_GLOBAL_DATA::GetTextHeight](#gettextheight)|Recupera el alto de caracteres de texto en la fuente actual.|
|[AFX_GLOBAL_DATA::GetWICFactory](#getwicfactory)|Devuelve un puntero a la interfaz `IWICImagingFactory` que está almacenada en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.|
|[AFX_GLOBAL_DATA::GetWriteFactory](#getwritefactory)|Devuelve un puntero a la interfaz `IDWriteFactory` que está almacenada en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Inicializa los generadores `D2D`, `DirectWrite`y `WIC` . Llame a este método antes de que se inicialice la ventana principal.|
|[AFX_GLOBAL_DATA::Is32BitIcons](#is32biticons)|Indica si se admiten los iconos de 32 bits predefinidos.|
|[AFX_GLOBAL_DATA::IsD2DInitialized](#isd2dinitialized)|Determina si se inicializó `D2D` .|
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Proporciona una manera sencilla de llamar al método de Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) .|
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Indica si las imágenes se muestran actualmente en contraste alto.|
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Detecta el estado actual de las características del escritorio para la animación de menús y para ocultar automáticamente la barra de tareas.|
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Registra la clase de ventana MFC especificada.|
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Libera las interfaces obtenidas a través de los métodos GetITaskbarList y GetITaskbarList3.|
|[AFX_GLOBAL_DATA::Resume](#resume)|Reinicializa los punteros a función internos que tienen acceso a métodos compatibles con los [temas y estilos visuales](/windows/win32/Controls/visual-styles-overview)de Windows.|
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Proporciona una manera sencilla de llamar al método de Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) .|
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Crea la fuente lógica especificada.|
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Crea e inicializa un objeto de elemento del Shell a partir de un nombre de análisis.|
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reinicializa las fuentes lógicas utilizadas por el marco.|
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializa los colores, la profundidad de color, los pinceles, los lápices y las imágenes utilizadas por el marco.|

### <a name="protected-methods"></a>Métodos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Habilita o deshabilita la compatibilidad con Microsoft Active Accessibility. Active Accessibility proporciona métodos de confianza para exponer información sobre los elementos de la interfaz de usuario.|
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Indica si la compatibilidad con Microsoft Active Accessibility está habilitada.|
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Indica si el sistema operativo admite ventanas superpuestas.|

### <a name="data-members"></a>Miembros de datos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport](#bisosalphablendingsupport)|Indica si el sistema operativo actual admite la combinación alfa.|
|[AFX_GLOBAL_DATA::bIsWindows7](#biswindows7)|Indica si la aplicación se está ejecutando en el sistema operativo Windows 7 o posterior.|
|[AFX_GLOBAL_DATA::clrActiveCaptionGradient](#clractivecaptiongradient)|Especifica el degradado de color de la leyenda activa. Se suele utilizar para acoplar paneles.|
|[AFX_GLOBAL_DATA::clrInactiveCaptionGradient](#clrinactivecaptiongradient)|Especifica el degradado de color de la leyenda inactiva. Se suele utilizar para acoplar paneles.|
|[AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons](#m_busebuiltin32biticons)|Indica si el marco usa iconos de colores de 32 bits predefinidos o iconos de una resolución inferior.|
|[AFX_GLOBAL_DATA::m_bUseSystemFont](#m_busesystemfont)|Indica si se usa una fuente del sistema para los menús, las barras de herramientas y las cintas.|
|[AFX_GLOBAL_DATA::m_hcurHand](#m_hcurhand)|Almacena el identificador del cursor de mano.|
|[AFX_GLOBAL_DATA::m_hcurStretch](#m_hcurstretch)|Almacena el identificador del cursor de ajuste horizontal.|
|[AFX_GLOBAL_DATA::m_hcurStretchVert](#m_hcurstretchvert)|Almacena el identificador del cursor de ajuste vertical.|
|[AFX_GLOBAL_DATA::m_hiconTool](#m_hicontool)|Almacena el identificador para el icono de la herramienta.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin](#m_nautohidetoolbarmargin)|Especifica el desplazamiento de la barra de herramientas Ocultar automáticamente situada más a la izquierda en el lado izquierdo de la barra de acoplamiento.|
|[AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing](#m_nautohidetoolbarspacing)|Especifica la separación entre las barras de herramientas Ocultar automáticamente.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](#m_ndragframethicknessdock)|Especifica el grosor del marco de arrastrar que se usa para comunicar el estado acoplado.|
|[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](#m_ndragframethicknessfloat)|Especifica el grosor del marco de arrastrar que se usa para comunicar el estado flotante.|

### <a name="remarks"></a>Comentarios

La mayoría de los datos de la estructura `AFX_GLOBAL_DATA` se inicializan cuando se inicia la aplicación.

### <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`AFX_GLOBAL_DATA`

### <a name="requirements"></a>Requisitos

**Encabezado:** afxglobals.h

## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport

Indica si el sistema operativo admite la combinación alfa.

```
BOOL  bIsOSAlphaBlendingSupport;
```

### <a name="remarks"></a>Comentarios

TRUE indica que se admite la combinación alfa; en caso contrario, FALSE.

## <a name="cleanup"></a> AFX_GLOBAL_DATA::CleanUp

Libera los recursos asignados por el marco, como pinceles, fuentes y archivos DLL.

```
void CleanUp();
```

## <a name="d2d1makerotatematrix"></a> AFX_GLOBAL_DATA::D2D1MakeRotateMatrix

Crea una transformación de giro que gire según el ángulo especificado alrededor de un punto especificado.

```
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,
    D2D1_POINT_2F center,
    D2D1_MATRIX_3X2_F *matrix);
```

### <a name="parameters"></a>Parámetros

*angle*<br/>
Ángulo de rotación en el sentido de las agujas del reloj, en grados.

*center*<br/>
Punto sobre el que se va a girar.

*matrix*<br/>
Cuando este método finaliza, contiene la nueva transformación de giro. Debe asignar almacenamiento para este parámetro.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente, o un valor de error en caso contrario.

## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground

Dibuja el fondo del elemento primario de un control en el área especificada.

```
BOOL DrawParentBackground(
    CWnd* pWnd,
    CDC* pDC,
    LPRECT lpRect = NULL);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
de Puntero a la ventana de un control.

*pDC*<br/>
de Puntero a un contexto de dispositivo.

*lpRect*<br/>
de Puntero a un rectángulo que delimita el área que se va a dibujar. El valor predeterminado es NULL.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

## <a name="drawtextonglass"></a> AFX_GLOBAL_DATA::DrawTextOnGlass

Dibuja el texto especificado en el estilo visual del tema especificado.

```
BOOL DrawTextOnGlass(
    HTHEME hTheme,
    CDC* pDC,
    int iPartId,
    int iStateId,
    CString strText,
    CRect rect,
    DWORD dwFlags,
    int nGlowSize = 0,
    COLORREF clrText = (COLORREF)-1);
```

### <a name="parameters"></a>Parámetros

*hTheme*<br/>
de Identificador de los datos del tema de una ventana o NULL. El marco de trabajo usa el tema especificado para dibujar el texto si este parámetro no es NULL y se admiten temas. En caso contrario, el marco no usa un tema para dibujar el texto.

Use el método [OpenThemeData](/windows/win32/api/uxtheme/nf-uxtheme-openthemedata) para crear un HTHEME.

*pDC*<br/>
de Puntero a un contexto de dispositivo.

*iPartId*<br/>
de Parte del control que tiene la apariencia de texto deseada. Para obtener más información, vea la columna Parts (Elementos) de la tabla de [Parts and States](/windows/win32/controls/parts-and-states)(Estados y elementos). Si este valor es 0, el texto se dibuja en la fuente predeterminada o en una fuente seleccionada en el contexto del dispositivo.

*iStateId*<br/>
de Estado del control que tiene la apariencia de texto deseada. Para obtener más información, vea la columna States (Estados) de la tabla de [Parts and States](/windows/win32/controls/parts-and-states)(Estados y elementos).

*strText*<br/>
de Texto que se va a dibujar.

*rect*<br/>
de Límite del área en la que se dibuja el texto especificado.

*dwFlags*<br/>
de Combinación bit a bit (o) de marcas que especifican cómo se dibuja el texto especificado.

Si el parámetro *hTheme* es `NULL` o si los temas no se admiten y habilitan, el parámetro *nFormat* del método [CDC::D rawtext](../../mfc/reference/cdc-class.md#drawtext) describe las marcas válidas. Si se admiten los temas, el parámetro *dwFlags* del método [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) describe las marcas válidas.

*nGlowSize*<br/>
de Tamaño de un efecto de resplandor que se dibuja en el fondo antes de dibujar el texto especificado. El valor predeterminado es 0.

*clrText*<br/>
de Color en el que se dibuja el texto especificado. El valor predeterminado es el color predeterminado.

### <a name="return-value"></a>Valor devuelto

TRUE si se usa un tema para dibujar el texto especificado; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un tema define el estilo visual de una aplicación. No se usa un tema para dibujar el texto si el parámetro *hTheme* es null, o si no se admite el método [DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex) , o si la composición [Administrador de ventanas de escritorio](/windows/win32/dwm/dwm-overview) (DWM) está deshabilitada.

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport

Habilita o deshabilita la compatibilidad con Microsoft Active Accessibility.

```
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parámetros

*bEnable*<br/>
de TRUE para habilitar la compatibilidad con accesibilidad; FALSE para deshabilitar la compatibilidad con accesibilidad. El valor predeterminado es TRUE.

### <a name="remarks"></a>Comentarios

Active Accessibility es una tecnología basada en COM que mejora la forma en que los programas y el sistema operativo Windows funcionan conjuntamente con los productos de tecnología de asistencia. Proporciona métodos confiables para exponer información sobre los elementos de la interfaz de usuario. Sin embargo, ahora está disponible un modelo de accesibilidad más reciente denominado Microsoft UI Automation. Para obtener una comparación de las dos tecnologías, vea automatización de la [interfaz de usuario y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).

Use el método [AFX_GLOBAL_DATA:: IsAccessibilitySupport](#isaccessibilitysupport) para determinar si la compatibilidad con Microsoft Active Accessibility está habilitada.

## <a name="excludetag"></a> AFX_GLOBAL_DATA::ExcludeTag

Quita el par especificado de etiquetas XML de un búfer especificado.

```
BOOL ExcludeTag(
    CString& strBuffer,
    LPCTSTR lpszTag,
    CString& strTag,
    BOOL bIsCharsList = FALSE);
```

### <a name="parameters"></a>Parámetros

*strBuffer*<br/>
de Búfer de texto.

*lpszTag*<br/>
de Nombre de un par de etiquetas XML de apertura y cierre.

*strTag*<br/>
enuncia Cuando este método finaliza, el parámetro *strTag* contiene el texto que se encuentra entre las etiquetas XML de apertura y cierre que se denominan mediante el parámetro *lpszTag* . Los espacios en blanco iniciales o finales se recortan del resultado.

*bIsCharsList*<br/>
de TRUE para convertir los símbolos de los caracteres de escape del parámetro *strTag* en caracteres de escape reales; FALSE no para realizar la conversión. El valor predeterminado es FALSE. Para obtener más información, vea la sección Comentarios.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se realiza correctamente; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Un par de etiquetas XML consta de etiquetas de apertura y cierre con nombre que indican el principio y el final de una ejecución de texto en el búfer especificado. El parámetro *strBuffer* especifica el búfer y el parámetro *lpszTag* especifica el nombre de las etiquetas XML.

Use los símbolos de la tabla siguiente para codificar un conjunto de caracteres de escape en el búfer especificado. Especifique TRUE para que el parámetro *bIsCharsList* convierta los símbolos del parámetro *strTag* en caracteres de escape reales. En la tabla siguiente se usa la macro [_ t ()](../../c-runtime-library/data-type-mappings.md) para especificar las cadenas de caracteres de símbolo y de escape.

|Símbolo|Carácter de escape|
|------------|----------------------|
|_ T (\\"\t")|_ T ("\t")|
|_ T (\\"\n")|_ T ("\n")|
|_ T (\\"\r")|_ T ("\r")|
|_ T (\\"\b")|_ T ("\b")|
|_ T ("LT")|_ T (\<"")|
|_ T ("GT")|_ T (">")|
|_ T ("AMP")|_ T ("&")|

## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor

Recupera el color actual del elemento de la interfaz de usuario especificado.

```
COLORREF GetColor(int nColor);
```

### <a name="parameters"></a>Parámetros

*nColor*<br/>
de Valor que especifica un elemento de la interfaz de usuario cuyo color se recupera. Para obtener una lista de valores válidos, vea el parámetro *NINDEX* del método [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) .

### <a name="return-value"></a>Valor devuelto

Valor de color RGB del elemento de la interfaz de usuario especificado. Para obtener más información, vea la sección Comentarios.

### <a name="remarks"></a>Comentarios

Si el parámetro *nColor* está fuera del intervalo, el valor devuelto es cero. Dado que cero también es un valor RGB válido, no se puede utilizar este método para determinar si el sistema operativo actual admite un color del sistema. En su lugar, use el método [GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush) , que devuelve NULL si no se admite el color.

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory

Devuelve un puntero a la interfaz ID2D1Factory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.

```
ID2D1Factory* GetDirect2dFactory();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz ID2D1Factory si la creación de un generador se realiza correctamente, o NULL si se produce un error en la creación o si el sistema operativo actual no tiene compatibilidad con D2D.

## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor

Recupera el cursor predefinido que se parece a una mano y cuyo identificador es IDC_HAND.

```
HCURSOR GetHandCursor();
```

### <a name="return-value"></a>Valor devuelto

Identificador del cursor de mano.

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics

Recupera las métricas asociadas al área no cliente de las ventanas no minimizadas.

```
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```

### <a name="parameters"></a>Parámetros

*info*<br/>
[in, out] Una estructura [NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw) que contiene las métricas escalables asociadas al área no cliente de una ventana no minimizada.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se ejecuta correctamente; en caso contrario, FALSE.

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight

Recupera el alto de caracteres de texto en la fuente actual.

```
int GetTextHeight(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>Parámetros

*bHorz*<br/>
de TRUE para recuperar el alto de los caracteres cuando el texto se ejecuta horizontalmente; FALSE para recuperar el alto de los caracteres cuando el texto se ejecuta verticalmente. El valor predeterminado es TRUE.

### <a name="return-value"></a>Valor devuelto

Alto de la fuente actual, que se mide desde su ascendente a su descendiente.

## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory

Devuelve un puntero a la interfaz IWICImagingFactory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.

```
IWICImagingFactory* GetWICFactory();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz IWICImagingFactory si la creación de un generador se realiza correctamente, o NULL si se produce un error en la creación o si el sistema operativo actual no tiene compatibilidad con WIC.

## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory

Devuelve un puntero a la interfaz IDWriteFactory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.

```
IDWriteFactory* GetWriteFactory();
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la interfaz IDWriteFactory si la creación de un generador se realiza correctamente, o NULL si se produce un error en la creación o el sistema operativo actual no tiene compatibilidad con DirectWrite.

## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D

Inicializa los generadores D2D, DirectWrite y WIC. Llame a este método antes de que se inicialice la ventana principal.

```
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>Parámetros

*d2dFactoryType*<br/>
El modelo de subprocesos del generador D2D y los recursos que crea.

*writeFactoryType*<br/>
Valor que especifica si el objeto de generador de escritura se compartirá o se aislará.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si se intilalizrd los generadores; de lo contrario, FALSE.

## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons

Indica si se admiten los iconos de 32 bits predefinidos.

```
BOOL Is32BitIcons() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se admiten los iconos predefinidos de 32 bits; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método devuelve TRUE si el marco admite iconos integrados de 32 bits y si el sistema operativo admite 16 bits por píxel o más, y si las imágenes no se muestran en contraste alto.

## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport

Indica si la compatibilidad con Microsoft Active Accessibility está habilitada.

```
BOOL IsAccessibilitySupport() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si está habilitada la compatibilidad con accesibilidad; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Microsoft Active Accessibility era la solución anterior para permitir el acceso a las aplicaciones. La automatización de la interfaz de usuario de Microsoft es el nuevo modelo de accesibilidad para Microsoft Windows y está diseñado para satisfacer las necesidades de los productos de tecnología de asistencia y las herramientas de pruebas automatizadas.

Use el método [AFX_GLOBAL_DATA:: EnableAccessibilitySupport](#enableaccessibilitysupport) para habilitar o deshabilitar la compatibilidad con Active Accessibility.

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized

Determina si se inicializó D2D

```
BOOL IsD2DInitialized() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se inicializó D2D; en caso contrario, FALSE.

## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled

Proporciona una manera sencilla de llamar al método de Windows [DwmIsCompositionEnabled](/windows/win32/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) .

```
BOOL IsDwmCompositionEnabled();
```

### <a name="return-value"></a>Valor devuelto

TRUE si la composición de [Administrador de ventanas de escritorio](/windows/win32/dwm/dwm-overview) (DWM) está habilitada; en caso contrario, FALSE.

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode

Indica si las imágenes se muestran actualmente en contraste alto.
```
BOOL IsHighContrastMode() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si las imágenes se muestran actualmente en el modo de contraste alto en blanco o negro; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

En el modo de contraste alto de color negro, los bordes orientados a la luz son blancos y el fondo es negro. En el modo de contraste alto blanco, los bordes orientados a la luz son negros y el fondo es blanco.

## <a name="iswindowslayersupportavailable"></a> AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable

Indica si el sistema operativo admite ventanas superpuestas.

```
BOOL IsWindowsLayerSupportAvailable() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se admiten las ventanas superpuestas; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Si se admiten ventanas superpuestas, los marcadores de *acoplamiento inteligente* usan ventanas superpuestas.

## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons

Indica si el marco usa iconos de colores de 32 bits predefinidos o iconos de una resolución inferior.

```
BOOL  m_bUseBuiltIn32BitIcons;
```

### <a name="remarks"></a>Comentarios

TRUE especifica que el marco usa iconos de color de 32 bits; FALSE especifica iconos de resolución inferior. El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro como true.

Este miembro debe establecerse en el inicio de la aplicación.

## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont

Indica si se usa una fuente del sistema para los menús, las barras de herramientas y las cintas.

```
BOOL m_bUseSystemFont;
```

### <a name="remarks"></a>Comentarios

TRUE especifica que se debe usar una fuente del sistema. en caso contrario, FALSE. El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en false.

La prueba de este miembro no es la única manera de que el marco de trabajo determine la fuente que se va a usar. El `AFX_GLOBAL_DATA::UpdateFonts` método también prueba las fuentes predeterminadas y alternativas para determinar qué estilos visuales están disponibles para aplicarse a menús, barras de herramientas y cintas de opciones.

## <a name="m_hcurhand"></a> AFX_GLOBAL_DATA::m_hcurHand

Almacena el identificador del cursor de mano.

```
HCURSOR m_hcurHand;
```

## <a name="m_hcurstretch"></a> AFX_GLOBAL_DATA::m_hcurStretch

Almacena el identificador del cursor de ajuste horizontal.

```
HCURSOR m_hcurStretch;
```

## <a name="m_hcurstretchvert"></a> AFX_GLOBAL_DATA::m_hcurStretchVert

Almacena el identificador del cursor de ajuste vertical.

```
HCURSOR m_hcurStretchVert;
```

## <a name="m_hicontool"></a> AFX_GLOBAL_DATA::m_hiconTool

Almacena el identificador para el icono de la herramienta.

```
HICON m_hiconTool;
```

## <a name="m_nautohidetoolbarmargin"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin

Especifica el desplazamiento de la barra de herramientas ocultar automáticamente situada más a la izquierda en el lado izquierdo de la barra de acoplamiento.

```
int  m_nAutoHideToolBarMargin;
```

### <a name="remarks"></a>Comentarios

El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en 4 píxeles.

## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing

Especifica la separación entre las barras de herramientas Ocultar automáticamente.

```
int   m_nAutoHideToolBarSpacing;
```

### <a name="remarks"></a>Comentarios

El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en 14 píxeles.

## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Especifica el grosor del marco de arrastre que se usa para indicar el estado acoplado.

```
int  m_nDragFrameThicknessDock;
```

### <a name="remarks"></a>Comentarios

El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en 3 píxeles.

## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat

Especifica el grosor del marco de arrastre que se usa para indicar el estado flotante.

```
int  m_nDragFrameThicknessFloat;
```

### <a name="remarks"></a>Comentarios

El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en 4 píxeles.

## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange

Detecta el estado actual de las características del escritorio para la animación de menús y para ocultar automáticamente la barra de tareas.

```
void OnSettingChange();
```

### <a name="remarks"></a>Comentarios

Este método establece las variables de marco de trabajo en el estado de ciertos atributos del escritorio del usuario. Este método detecta el estado actual de las características de animación de menús, atenuación de menús y ocultación automática de la barra de tareas.

## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass

Registra la clase de ventana MFC especificada.

```
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```

### <a name="parameters"></a>Parámetros

*lpszClassNamePrefix*<br/>
de Nombre de la clase de ventana que se va a registrar.

### <a name="return-value"></a>Valor devuelto

Nombre completo de la clase registrada si este método se ejecuta correctamente; de lo contrario, una [excepción de recurso](exception-processing.md#afxthrowresourceexception).

### <a name="remarks"></a>Comentarios

El valor devuelto es una lista delimitada por signos de dos puntos de la cadena de parámetro *lpszClassNamePrefix* y las representaciones de texto hexadecimal de los identificadores de la instancia de aplicación actual. cursor de la aplicación, que es el cursor de flecha cuyo identificador es IDC_ARROW; y el pincel del fondo. Para obtener más información sobre el registro de clases de ventana de MFC, vea [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).

## <a name="resume"></a> AFX_GLOBAL_DATA::Resume

Reinicializa los punteros de función internos que tienen acceso a los métodos que admiten los temas de Windows y los estilos visuales.

```
BOOL Resume();
```

### <a name="return-value"></a>Valor devuelto

TRUE si este método se ejecuta correctamente; en caso contrario, FALSE. En el modo de depuración, este método valida si este método no se realiza correctamente.

### <a name="remarks"></a>Comentarios

Se llama a este método cuando el marco de trabajo recibe el mensaje [WM_POWERBROADCAST](/windows/win32/Power/wm-powerbroadcast) .

## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib

Proporciona una manera sencilla de llamar al método de Windows [SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes) .

```
BOOL SetLayeredAttrib(
    HWND hwnd,
    COLORREF crKey,
    BYTE bAlpha,
    DWORD dwFlags);
```

### <a name="parameters"></a>Parámetros

*hwnd*<br/>
de Identificador de la ventana superpuesta.

*crKey*<br/>
de La clave de color de transparencia que el [Administrador de ventanas de escritorio](/windows/win32/dwm/dwm-overview) utiliza para componer la ventana superpuesta.

*bAlpha*<br/>
de Valor alfa que se usa para describir la opacidad de la ventana superpuesta.

*dwFlags*<br/>
de Combinación bit a bit (o) de marcas que especifican los parámetros de método que se van a utilizar. Especifique LWA_COLORKEY para usar el parámetro *crKey* como color de transparencia. Especifique LWA_ALPHA para usar el parámetro *bAlpha* para determinar la opacidad de la ventana superpuesta.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se ejecuta correctamente; en caso contrario, FALSE.

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont

Crea la fuente lógica especificada.

```
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz);
```

### <a name="parameters"></a>Parámetros

*lpLogFont*<br/>
de Puntero a una estructura que contiene los atributos de una fuente.

*bHorz*<br/>
de TRUE para especificar que el texto se ejecuta horizontalmente; FALSE para especificar que el texto se ejecuta verticalmente.

### <a name="return-value"></a>Valor devuelto

TRUE si este método se ejecuta correctamente; en caso contrario, FALSE. En el modo de depuración, este método valida si este método no se realiza correctamente.

### <a name="remarks"></a>Comentarios

Este método crea una fuente normal horizontal, una fuente subrayada y una fuente en negrita que se utiliza en los elementos de menú predeterminados. Este método crea opcionalmente una fuente vertical normal. Para obtener más información sobre las fuentes lógicas, vea [Cfont (:: CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).

## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts

Reinicializa las fuentes lógicas utilizadas por el marco.

```
void UpdateFonts();
```

### <a name="remarks"></a>Comentarios

Para obtener más información acerca de las fuentes `CFont::CreateFontIndirect`lógicas, vea.

## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors

Inicializa los colores, la profundidad de color, los pinceles, los lápices y las imágenes utilizadas por el marco.

```
void UpdateSysColors();
```

## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7

Indica si la aplicación se ejecuta en Windows 7 o posterior.

```
BOOL bIsWindows7;
```

## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient

Especifica el color de degradado del título activo. Se suele utilizar para acoplar paneles.

```
COLORREF clrActiveCaptionGradient;
```

## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient

Especifica el color de degradado del título inactivo. Se suele utilizar para acoplar paneles.

```
COLORREF clrInactiveCaptionGradient;
```

## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList

Crea y almacena en los datos globales un puntero a la `ITaskBarList` interfaz.

```
ITaskbarList *GetITaskbarList();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz `ITaskbarList` si la creación de un objeto de lista de la barra de tareas se realiza correctamente; Es NULL si se produce un error en la creación o si el sistema operativo actual es inferior a Windows 7.

## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3

Crea y almacena en los datos globales un puntero a la `ITaskBarList3` interfaz.

```
ITaskbarList3 *GetITaskbarList3();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la interfaz `ITaskbarList3` si la creación de un objeto de lista de la barra de tareas se realiza correctamente; Es NULL si se produce un error en la creación o si el sistema operativo actual es inferior a Windows 7.

## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars

Determina las posiciones de las barras Ocultar automáticamente del Shell.

```
int GetShellAutohideBars();
```

### <a name="return-value"></a>Valor devuelto

Valor entero con marcas codificadas que especifican las posiciones de las barras de ocultación automática. Puede combinar los valores siguientes: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.

## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs

Libera las interfaces obtenidas `GetITaskbarList` a `GetITaskbarList3` través de los métodos y.

```
void ReleaseTaskBarRefs();
```

## <a name="shellcreateitemfromparsingname"></a> AFX_GLOBAL_DATA::ShellCreateItemFromParsingName

Crea e inicializa un objeto de elemento del Shell a partir de un nombre de análisis.

```
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,
    IBindCtx *pbc,
    REFIID riid,
    void **ppv);
```

### <a name="parameters"></a>Parámetros

*pszPath*<br/>
de Un puntero a un nombre para mostrar.

*pbc*<br/>
Un puntero a un contexto de enlace que controla la operación de análisis.

*riid*<br/>
Referencia a un identificador de interfaz.

*ppv*<br/>
enuncia Cuando esta función devuelve un, contiene el puntero de interfaz solicitado en *riid*. Normalmente `IShellItem` será o `IShellItem2`.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se realiza correctamente; un valor de error en caso contrario.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../hierarchy-chart.md)<br/>
[Estructuras, estilos, devoluciones de llamada y mapas de mensajes](structures-styles-callbacks-and-message-maps.md)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[Partes y Estados](/windows/win32/controls/parts-and-states)<br/>
[CDC::DrawText](cdc-class.md#drawtext)<br/>
[DrawThemeTextEx](/windows/win32/api/uxtheme/nf-uxtheme-drawthemetextex)<br/>
[Administrador de ventanas de escritorio](/windows/win32/dwm/dwm-overview)<br/>
[Habilitar y controlar la composición de DWM](/windows/win32/dwm/composition-ovw)<br/>
[Automatización de la interfaz de usuario y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)<br/>
[GetSysColor (función)](/windows/win32/api/winuser/nf-winuser-getsyscolor)<br/>
[GetSysColorBrush](/windows/win32/api/winuser/nf-winuser-getsyscolorbrush)<br/>
[Estructura NONCLIENTMETRICS](/windows/win32/api/winuser/ns-winuser-nonclientmetricsw)<br/>
[AfxRegisterClass](application-information-and-management.md#afxregisterclass)<br/>
[AfxThrowResourceException](exception-processing.md#afxthrowresourceexception)<br/>
[SetLayeredWindowAttributes](/windows/win32/api/winuser/nf-winuser-setlayeredwindowattributes)
