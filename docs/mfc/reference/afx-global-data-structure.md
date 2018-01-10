---
title: AFX_GLOBAL_DATA (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AFX_GLOBAL_DATA
dev_langs: C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
caps.latest.revision: "30"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 68b4a5ba27d4fcb6fcaac7c80662d778c7cbbca7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="afxglobaldata-structure"></a>AFX_GLOBAL_DATA (estructura)
La estructura `AFX_GLOBAL_DATA` contiene los campos y métodos que se utilizan para administrar el marco o personalizar el aspecto y el comportamiento de la aplicación.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
struct AFX_GLOBAL_DATA  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`AFX_GLOBAL_DATA::AFX_GLOBAL_DATA`|Crea una estructura `AFX_GLOBAL_DATA` .|  
|`AFX_GLOBAL_DATA::~AFX_GLOBAL_DATA`|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
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
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Proporciona una manera sencilla de llamar al método de Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) .|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Indica si las imágenes se muestran actualmente en contraste alto.|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Detecta el estado actual de las características del escritorio para la animación de menús y para ocultar automáticamente la barra de tareas.|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Registra la clase de ventana MFC especificada.|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Libera las interfaces obtenidas a través de los métodos GetITaskbarList y GetITaskbarList3.|  
|[AFX_GLOBAL_DATA::resume](#resume)|Reinicializa los punteros a función internos que tienen acceso a métodos compatibles con los [temas y estilos visuales](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx)de Windows.|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Proporciona una manera sencilla de llamar al método de Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) .|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Crea la fuente lógica especificada.|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Crea e inicializa un objeto de elemento del Shell a partir de un nombre de análisis.|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reinicializa las fuentes lógicas utilizadas por el marco.|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializa los colores, la profundidad de color, los pinceles, los lápices y las imágenes utilizadas por el marco.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Habilita o deshabilita la compatibilidad con Microsoft Active Accessibility. Active Accessibility proporciona métodos de confianza para exponer información sobre los elementos de la interfaz de usuario.|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Indica si la compatibilidad con Microsoft Active Accessibility está habilitada.|  
|[AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable](#iswindowslayersupportavailable)|Indica si el sistema operativo admite ventanas superpuestas.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|nombre|Descripción|  
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
  
### <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)


## <a name="bisosalphablendingsupport"></a>AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
Indica si el sistema operativo admite la combinación alfa.  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`indica que se admite la combinación alfa; en caso contrario, `FALSE`.  
  

## <a name="cleanup"></a>AFX_GLOBAL_DATA::CleanUp
Libera los recursos asignados por el marco, como pinceles, fuentes y archivos DLL.  
  
  
```  
void CleanUp();
```  
## <a name="d2d1makerotatematrix"></a>AFX_GLOBAL_DATA::D2D1MakeRotateMatrix
Crea una transformación de giro que gire según el ángulo especificado alrededor de un punto especificado.  
  
  
```  
HRESULT D2D1MakeRotateMatrix(
    FLOAT angle,  
    D2D1_POINT_2F center,  
    D2D1_MATRIX_3X2_F *matrix);
```  
  
### <a name="parameters"></a>Parámetros   
 `angle`  
 El ángulo de giro hacia la derecha, en grados.  
  
 `center`  
 El punto en que se va a girar.  
  
 `matrix`  
 Cuando este método vuelve, contiene la nueva transformación de rotación. Debe asignar almacenamiento para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Lo contrario, devuelve S_OK si se realiza correctamente, o un valor de error.  
  
## <a name="drawparentbackground"></a>AFX_GLOBAL_DATA::DrawParentBackground
Dibuja el fondo del elemento primario de un control en el área especificada.  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `pWnd`  
 Puntero a la ventana del control.  
  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `lpRect`  
 Puntero a un rectángulo que delimita el área para dibujar. El valor predeterminado es `NULL`.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
## <a name="drawtextonglass"></a>AFX_GLOBAL_DATA::DrawTextOnGlass
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
 [in] `hTheme`  
 Identificador de los datos del tema de una ventana, o `NULL`. El marco usa el tema especificado para dibujar el texto si este parámetro no es `NULL` y se admiten temas. En caso contrario, el marco no usa un tema para dibujar el texto.  
  
 Use el método [OpenThemeData](http://msdn.microsoft.com/library/windows/desktop/bb759821) para crear un objeto `HTHEME`.  
  
 [in] `pDC`  
 Puntero a un contexto de dispositivo.  
  
 [in] `iPartId`  
 Elemento del control que tiene la apariencia del texto deseado. Para obtener más información, vea la columna Parts (Elementos) de la tabla de [Parts and States](http://msdn.microsoft.com/library/windows/desktop/bb773210)(Estados y elementos). Si este valor es 0, el texto se dibuja en la fuente predeterminada o en una fuente seleccionada en el contexto del dispositivo.  
  
 [in] `iStateId`  
 Estado del control que tiene la apariencia del texto deseado. Para obtener más información, vea la columna States (Estados) de la tabla de [Parts and States](http://msdn.microsoft.com/library/windows/desktop/bb773210)(Estados y elementos).  
  
 [in] `strText`  
 Texto que se va a trazar.  
  
 [in] `rect`  
 Límite del área en la que se dibuja el texto especificado.  
  
 [in] `dwFlags`  
 Combinación bit a bit (OR) de marcas que especifican cómo se dibuja el texto especificado.  
  
 Si el `hTheme` parámetro es `NULL` o si los temas no están admitidos y habilitados, el `nFormat` parámetro de la [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext) método describe las marcas válidas. Si se admiten temas, el parámetro `dwFlags` del método [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) describe las marcas válidas.  
  
 [in] `nGlowSize`  
 Tamaño de un efecto de iluminado que se dibuja en el fondo antes de dibujar el texto especificado. El valor predeterminado es 0.  
  
 [in] `clrText`  
 Color en el que se dibuja el texto especificado. El valor predeterminado es el color predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se utiliza un tema para dibujar el texto especificado; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Un tema define el estilo visual de una aplicación. Un tema no se usa para dibujar el texto si el parámetro `hTheme` es `NULL`, si no se admite el método [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317) o si la composición del [Administrador de ventanas de escritorio](http://msdn.microsoft.com/library/windows/desktop/aa969540) (DWM) está deshabilitada.  
  
### <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [Estados y elementos](http://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](http://msdn.microsoft.com/library/windows/desktop/bb773317)   
 [Administrador de ventanas de escritorio](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Habilitar y controlar la composición de DWM](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="enableaccessibilitysupport"></a>AFX_GLOBAL_DATA::EnableAccessibilitySupport
Habilita o deshabilita la compatibilidad con Microsoft Active Accessibility.  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `bEnable`  
 `TRUE`Para habilitar la compatibilidad de accesibilidad; `FALSE` para deshabilitar la compatibilidad de accesibilidad. El valor predeterminado es `TRUE`.  
  
### <a name="remarks"></a>Comentarios  
 Active Accessibility es una tecnología basada en COM que mejora el funcionamiento de los programas y el trabajo del sistema operativo de Windows junto con los productos de tecnología. Proporciona métodos confiables para exponer información sobre los elementos de la interfaz de usuario. Sin embargo, ahora está disponible un nuevo modelo de accesibilidad denominado automatización de interfaz de usuario de Microsoft. Para obtener una comparación de las dos tecnologías, consulte [UI Automation y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).  
  
 Use la [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) método para determinar si está habilitada la compatibilidad con Microsoft Active Accessibility.  
  
 
### <a name="see-also"></a>Vea también  
 [UI Automation y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

## <a name="excludetag"></a>AFX_GLOBAL_DATA::ExcludeTag
Quita el par especificado de etiquetas XML de un búfer especificado.  
  
  
```  
BOOL ExcludeTag(
    CString& strBuffer,  
    LPCTSTR lpszTag,  
    CString& strTag,  
    BOOL bIsCharsList = FALSE);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `strBuffer`  
 Un búfer de texto.  
  
 [in] `lpszTag`  
 El nombre de un par de apertura y cierre de etiquetas XML.  
  
 [out] `strTag`  
 Cuando este método finaliza, el `strTag` parámetro contiene el texto que se encuentra entre la apertura y cierre XML etiquetas designadas por los `lpszTag` parámetro. Ningún espacio en blanco inicial o final se recorta del resultado.  
  
 [in] `bIsCharsList`  
 `TRUE`para convertir los símbolos para los caracteres de escape en el `strTag` parámetro en caracteres de escape real; `FALSE` no debe realizar la conversión. El valor predeterminado es `FALSE`. Para obtener más información, vea la sección Comentarios.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Un par de etiquetas XML consta de con el nombre de apertura y cierre de las etiquetas que indican el inicio y final de una ejecución de texto en el búfer especificado. El `strBuffer` parámetro especifica el búfer y el `lpszTag` parámetro especifica el nombre de las etiquetas XML.  
  
 Utilice los símbolos en la tabla siguiente para codificar un juego de caracteres de escape en el búfer especificado. Especifique `TRUE` para el `bIsCharsList` parámetro para convertir los símbolos en el `strTag` parámetro en caracteres de escape real. La tabla siguiente se usa el [_T ()](../../c-runtime-library/data-type-mappings.md) macro para especificar los símbolos y cadenas de caracteres de escape.  
  
|Símbolo|Carácter de escape|  
|------------|----------------------|  
|_T ("\\\t")|_T("\t")|  
|_T ("\\\n")|_T("\n")|  
|_T ("\\\r")|_T("\r")|  
|_T ("\\\b")|_T("\b")|  
|_T("LT")|_T ("\<")|  
|_T("GT")|_T(">")|  
|_T("AMP")|_T("&")|  
  
## <a name="getcolor"></a>AFX_GLOBAL_DATA::GetColor
Recupera el color actual del elemento de la interfaz de usuario especificado.  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `nColor`  
 Un valor que especifica un elemento de la interfaz de usuario cuyo color se recupera. Para obtener una lista de valores válidos, consulte el `nIndex` parámetro de la [GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371) método.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de color RGB del elemento de interfaz de usuario especificado. Para obtener más información, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Si el `nColor` parámetro está fuera del intervalo, el valor devuelto es cero. Dado que cero también es un valor RGB válido, no puede usar este método para determinar si un color del sistema es compatible con el sistema operativo actual. En su lugar, use la [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927) método, que devuelve `NULL` si no se admite el color.  
  
### <a name="see-also"></a>Vea también  

 [Función GetSysColor](http://msdn.microsoft.com/library/windows/desktop/ms724371)   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [GetSysColorBrush](http://msdn.microsoft.com/library/windows/desktop/dd144927)

## <a name="getdirect2dfactory"></a>AFX_GLOBAL_DATA::GetDirect2dFactory
 Devuelve un puntero a la interfaz ID2D1Factory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a interfaz de ID2D1Factory si la creación de un generador se realiza correctamente, o NULL si no se puede crear o sistema operativo actual no tiene compatibilidad D2D.  
  
## <a name="gethandcursor"></a>AFX_GLOBAL_DATA::GetHandCursor
Recupera el cursor predefinido que se parece a una mano y cuyo identificador es `IDC_HAND`.  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del cursor de mano.  

## <a name="getnonclientmetrics"></a>AFX_GLOBAL_DATA::GetNonClientMetrics
Recupera las métricas asociadas al área no cliente de las ventanas no minimizadas.  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>Parámetros   
 [in, out] `info`  
 A [NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175) estructura que contiene las métricas escalables asociadas con el área no cliente de una ventana no minimizada.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.  
 
  
### <a name="see-also"></a>Vea también   
 [Estructura NONCLIENTMETRICS](http://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a>AFX_GLOBAL_DATA::GetTextHeight
 Recupera el alto de caracteres de texto en la fuente actual.  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `bHorz`  
 `TRUE`para recuperar el alto de caracteres cuando el texto se extiende horizontalmente; `FALSE` para recuperar el alto de caracteres cuando ejecuciones de texto verticalmente. El valor predeterminado es `TRUE`.  
  
### <a name="return-value"></a>Valor devuelto  
 El alto de la fuente actual, que se mide desde su ascender hasta su trazo descendente.  
  
## <a name="getwicfactory"></a>AFX_GLOBAL_DATA::GetWICFactory
Devuelve un puntero a la interfaz IWICImagingFactory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a interfaz de IWICImagingFactory si la creación de un generador se realiza correctamente, o NULL si no se puede crear o sistema operativo actual no tiene compatibilidad con WIC.  
  
## <a name="getwritefactory"></a>AFX_GLOBAL_DATA::GetWriteFactory
Devuelve un puntero a la interfaz IDWriteFactory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a interfaz de IDWriteFactory si la creación de un generador se realiza correctamente, o NULL si no se puede crear o sistema operativo actual no tiene compatibilidad con DirectWrite.  
 
## <a name="initd2d"></a>AFX_GLOBAL_DATA::InitD2D
Inicializa los generadores de D2D y DirectWrite, WIC. Llame a este método antes de que se inicialice la ventana principal.  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parámetros   
 `d2dFactoryType`  
 El modelo de subprocesos de la fábrica de D2D y los recursos crea.  
  
 `writeFactoryType`  
 Un valor que especifica si el objeto de generador de escritura se comparten o aislado  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si los generadores se han resuelto intilalizrd, FALSE: en caso contrario  
  
## <a name="is32biticons"></a>AFX_GLOBAL_DATA::Is32BitIcons
Indica si se admiten los iconos de 32 bits predefinidos.  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se admiten los iconos de 32 bits predefinidos; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve `TRUE` si el marco de trabajo admite iconos integrados de 32 bits y si el sistema operativo admite 16 bits por píxel o más, y no se muestran imágenes en contraste alto.  
  
## <a name="isaccessibilitysupport"></a>AFX_GLOBAL_DATA::IsAccessibilitySupport
Indica si la compatibilidad con Microsoft Active Accessibility está habilitada.  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se habilita la compatibilidad de accesibilidad; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Microsoft Active Accessibility fue la solución anterior para hacer que las aplicaciones accesibles. Automatización de la interfaz de usuario de Microsoft es el nuevo modelo de accesibilidad de Microsoft Windows y está pensado para abordar las necesidades de los productos de tecnología y herramientas de prueba automatizadas.   
  
 Use la [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) método para habilitar o deshabilitar la compatibilidad con Active Accessibility.  
  

### <a name="see-also"></a>Vea también  
 [Automatización de la interfaz de usuario y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a>AFX_GLOBAL_DATA::IsD2DInitialized
 Determina si se ha inicializado el D2D  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se inicializó D2D; en caso contrario, FALSE.  
  
## <a name="isdwmcompositionenabled"></a>AFX_GLOBAL_DATA::IsDwmCompositionEnabled
Proporciona una manera sencilla de llamar al método de Windows [DwmIsCompositionEnabled](http://msdn.microsoft.com/library/windows/desktop/aa969518) .  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si [Administrador de ventanas de escritorio](http://msdn.microsoft.com/library/windows/desktop/aa969540) composición (DWM) está habilitado; en caso contrario, `FALSE`.  
  
### <a name="see-also"></a>Vea también    
 [Administrador de ventanas de escritorio](http://msdn.microsoft.com/library/windows/desktop/aa969540)   
 [Habilitar y controlar la composición de DWM](http://msdn.microsoft.com/library/windows/desktop/aa969538)

## <a name="ishighcontrastmode"></a>AFX_GLOBAL_DATA::IsHighContrastMode
 Indica si las imágenes se muestran actualmente en contraste alto.    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si las imágenes se muestran actualmente en modo de blanco y negro de contraste alto; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de contraste alto negro, bordes orientada hacia la luz son blancos y el fondo es negro. En el modo de contraste alto blanca, bordes orientada hacia la luz son negros y el fondo es blanco.  
  
## <a name="iswindowslayersupportavailable"></a>AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable
Indica si el sistema operativo admite ventanas superpuestas.  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si se admiten las ventanas superpuestas; en caso contrario, `FALSE`.  
  
### <a name="remarks"></a>Comentarios  
 Si se admiten las ventanas superpuestas, *acoplamiento inteligente* marcadores usar ventanas superpuestas.  
  
## <a name="m_busebuiltin32biticons"></a>AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
Indica si el marco usa iconos de colores de 32 bits predefinidos o iconos de una resolución inferior.  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`Especifica que el marco usa iconos de colores de 32 bits; `FALSE` especifica iconos de resolución inferior. El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro por `TRUE`.  
  
 Este miembro debe establecerse al iniciar la aplicación.  
  
## <a name="m_busesystemfont"></a>AFX_GLOBAL_DATA::m_bUseSystemFont
Indica si se usa una fuente del sistema para los menús, las barras de herramientas y las cintas.  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>Comentarios  
 `TRUE`Especifica que se use una fuente del sistema; en caso contrario, `FALSE`. El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro por `FALSE`.  
  
 Pruebas de este miembro no es la única manera para el marco de trabajo determinar la fuente a utilizar. El `AFX_GLOBAL_DATA::UpdateFonts` método también comprueba las fuentes predeterminadas y alternativas para determinar qué estilos visuales están disponibles para aplicarse a los menús, barras de herramientas y las cintas.  
  
## <a name="m_hcurhand"></a>AFX_GLOBAL_DATA::m_hcurHand
Almacena el identificador del cursor de mano.  
  
  
```  
HCURSOR m_hcurHand;  
```  
  
## <a name="m_hcurstretch"></a>AFX_GLOBAL_DATA::m_hcurStretch
Almacena el identificador del cursor de ajuste horizontal.  
  
  
```  
HCURSOR m_hcurStretch;  
```  

## <a name="m_hcurstretchvert"></a>AFX_GLOBAL_DATA::m_hcurStretchVert
Almacena el identificador del cursor de ajuste vertical.  
  
  
```  
HCURSOR m_hcurStretchVert;  
```  
  
## <a name="m_hicontool"></a>AFX_GLOBAL_DATA::m_hiconTool
Almacena el identificador para el icono de la herramienta.  
  
  
```  
HICON m_hiconTool;  
```  
## <a name="m_nautohidetoolbarmargin"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarMargin
Especifica el desplazamiento de la barra de herramientas Ocultar automáticamente situada más a la izquierda de la barra de acoplamiento.  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro por 4 píxeles.  
  
## <a name="m_nautohidetoolbarspacing"></a>AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
Especifica la separación entre las barras de herramientas Ocultar automáticamente.  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro a 14 píxeles.  
  
## <a name="m_ndragframethicknessdock"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Especifica el grosor del marco de arrastrar que se utiliza para indicar el estado acoplado.  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro por 3 píxeles.  
  
## <a name="m_ndragframethicknessfloat"></a>AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
Especifica el grosor del marco de arrastrar que se usa para indicar el estado flotante.  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro por 4 píxeles.  
  
## <a name="onsettingchange"></a>AFX_GLOBAL_DATA::OnSettingChange
Detecta el estado actual de las características del escritorio para la animación de menús y para ocultar automáticamente la barra de tareas.  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método establece las variables de marco de trabajo en el estado de algunos atributos de escritorio del usuario. Este método detecta el estado actual de la animación de menús, la atenuación de menús y la barra funciones de ocultación automática de tareas.  
  
## <a name="registerwindowclass"></a>AFX_GLOBAL_DATA::RegisterWindowClass
Registra la clase de ventana MFC especificada.  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `lpszClassNamePrefix`  
 El nombre de la clase de ventana para registrar.  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre completo de la clase registrada si este método se realiza correctamente; en caso contrario, un [excepción recursos](http://msdn.microsoft.com/library/ddd99292-819b-4fa4-8371-b1954ed5856d).  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto es una lista delimitada por dos puntos de la `lpszClassNamePrefix` la cadena de parámetros y las representaciones de texto hexadecimal de los identificadores de la actual instancia de la aplicación; el cursor de la aplicación, que es el cursor de flecha cuyo identificador es IDC_ARROW; y el pincel del fondo. Para obtener más información acerca del registro de clases de ventana MFC, vea [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
### <a name="see-also"></a>Vea también    
 [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [AfxThrowResourceException](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a>AFX_GLOBAL_DATA::resume
 Reinicializa los punteros a función internos que tienen acceso a los métodos que admiten estilos visuales y temas de Windows. 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`. En modo de depuración, este método valida si este método es incorrecto.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama cuando el marco de trabajo recibe el [WM_POWERBROADCAST](http://msdn.microsoft.com/library/windows/desktop/aa373247) mensaje.  
  
## <a name="setlayeredattrib"></a>AFX_GLOBAL_DATA::SetLayeredAttrib
Proporciona una manera sencilla de llamar al método de Windows [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540) .  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `hwnd`  
 Identificador de la ventana superpuesta.  
  
 [in] `crKey`  
 El color de transparencia de clave que el [Administrador de ventanas de escritorio](http://msdn.microsoft.com/library/windows/desktop/aa969540) se utiliza para crear la ventana superpuesta.  
  
 [in] `bAlpha`  
 El valor alfa que se usa para describir la opacidad de la ventana superpuesta.  
  
 [in] `dwFlags`  
 Una combinación bit a bit (OR) de marcas que especifican qué parámetros de método que se usarán. Especificar LWA_COLORKEY para usar el `crKey` parámetro como el color de transparencia. Especificar LWA_ALPHA para usar el `bAlpha` parámetro para determinar la opacidad de la ventana superpuesta.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`.   
 
### <a name="see-also"></a>Vea también   
 [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)   
 [SetLayeredWindowAttributes](http://msdn.microsoft.com/library/windows/desktop/ms633540)

## <a name="setmenufont"></a>AFX_GLOBAL_DATA::SetMenuFont
Crea la fuente lógica especificada.  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros   
 [in] `lpLogFont`  
 Puntero a una estructura que contiene los atributos de una fuente.  
  
 [in] `bHorz`  
 `TRUE`para especificar que el texto se ejecuta horizontalmente; `FALSE` para especificar que el texto está situado verticalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 `TRUE`Si este método se realiza correctamente; en caso contrario, `FALSE`. En modo de depuración, este método valida si este método es incorrecto.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea una fuente regular horizontal, una fuente subrayada, y una fuente en negrita que está en default usa elementos de menú. Opcionalmente, este método crea una fuente vertical normal. Para obtener más información sobre las fuentes lógicas, consulte [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).  
  
## <a name="updatefonts"></a>AFX_GLOBAL_DATA::UpdateFonts
Reinicializa las fuentes lógicas utilizadas por el marco.  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información sobre las fuentes lógicas, consulte `CFont::CreateFontIndirect`.  
  
## <a name="updatesyscolors"></a>AFX_GLOBAL_DATA::UpdateSysColors
Inicializa los colores, la profundidad de color, los pinceles, los lápices y las imágenes utilizadas por el marco.  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a>AFX_GLOBAL_DATA::bIsWindows7
Indica si la aplicación se está ejecutando en Windows 7 o posterior.  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a>AFX_GLOBAL_DATA::clrActiveCaptionGradient
Especifica el color del degradado de la leyenda activa. Se suele utilizar para acoplar paneles.  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a>AFX_GLOBAL_DATA::clrInactiveCaptionGradient
Especifica el color del degradado de la leyenda inactiva. Se suele utilizar para acoplar paneles.  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a>AFX_GLOBAL_DATA::GetITaskbarList
Crea y almacena en los datos globales un puntero a la `ITaskBarList` interfaz.  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `ITaskbarList` interfaz si se realiza correctamente la creación de una barra de objeto de lista de tareas; `NULL` si se produce un error en la creación o si el sistema operativo actual es menor que Windows 7.  
  
## <a name="getitaskbarlist3"></a>AFX_GLOBAL_DATA::GetITaskbarList3
Crea y almacena en los datos globales un puntero a la `ITaskBarList3` interfaz.  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `ITaskbarList3` interfaz si se realiza correctamente la creación de una barra de objeto de lista de tareas; `NULL` si se produce un error en la creación o si el sistema operativo actual es menor que Windows 7.  
  
## <a name="getshellautohidebars"></a>AFX_GLOBAL_DATA::GetShellAutohideBars
Determina las posiciones de las barras Ocultar automáticamente del Shell.  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor entero con codificado marcas que especifican las posiciones de "auto" ocultar barras. Pueden combinar los valores siguientes: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.  
  
## <a name="releasetaskbarrefs"></a>AFX_GLOBAL_DATA::ReleaseTaskBarRefs
Libera las interfaces obtenidas a través de la `GetITaskbarList` y `GetITaskbarList3` métodos.  
  
  
```  
void ReleaseTaskBarRefs();
```  
  
## <a name="shellcreateitemfromparsingname"></a>AFX_GLOBAL_DATA::ShellCreateItemFromParsingName
Crea e inicializa un objeto de elemento del Shell a partir de un nombre de análisis.  
  
  
```  
HRESULT ShellCreateItemFromParsingName(
    PCWSTR pszPath,  
    IBindCtx *pbc,  
    REFIID riid,  
    void **ppv);
```  
  
### <a name="parameters"></a>Parámetros   
 `pszPath`  
 [in] Un puntero a un nombre para mostrar.  
  
 `pbc`  
 Un puntero a un contexto de enlace que controla la operación de análisis.  
  
 `riid`  
 Una referencia a un identificador de interfaz.  
  
 `ppv`  
 [out] Cuando esta función devuelve, contiene el puntero de interfaz solicitado en `riid`. Normalmente será `IShellItem` o `IShellItem2`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se realiza correctamente; un valor de error en caso contrario.  

