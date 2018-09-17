---
title: AFX_GLOBAL_DATA (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- AFX_GLOBAL_DATA structure [MFC]
- AFX_GLOBAL_DATA constructor
ms.assetid: c7abf2fb-ad5e-4336-a01d-260c29ed53a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0f5297b6764ba29805b842329403557ad2aa4c3b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701927"
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
|[AFX_GLOBAL_DATA::IsDwmCompositionEnabled](#isdwmcompositionenabled)|Proporciona una manera sencilla para llamar a la Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) método.|  
|[AFX_GLOBAL_DATA::IsHighContrastMode](#ishighcontrastmode)|Indica si las imágenes se muestran actualmente en contraste alto.|  
|[AFX_GLOBAL_DATA::OnSettingChange](#onsettingchange)|Detecta el estado actual de las características del escritorio para la animación de menús y para ocultar automáticamente la barra de tareas.|  
|[AFX_GLOBAL_DATA::RegisterWindowClass](#registerwindowclass)|Registra la clase de ventana MFC especificada.|  
|[AFX_GLOBAL_DATA::ReleaseTaskBarRefs](#releasetaskbarrefs)|Libera las interfaces obtenidas a través de los métodos GetITaskbarList y GetITaskbarList3.|  
|[AFX_GLOBAL_DATA::resume](#resume)|Reinicializa los punteros a función internos que tienen acceso a los métodos que admiten Windows [temas y estilos visuales](/windows/desktop/Controls/visual-styles-overview).|  
|[AFX_GLOBAL_DATA::SetLayeredAttrib](#setlayeredattrib)|Proporciona una manera sencilla para llamar a la Windows [SetLayeredWindowAttributes](/windows/desktop/api/winuser/nf-winuser-setlayeredwindowattributes) método.|  
|[AFX_GLOBAL_DATA::SetMenuFont](#setmenufont)|Crea la fuente lógica especificada.|  
|[AFX_GLOBAL_DATA::ShellCreateItemFromParsingName](#shellcreateitemfromparsingname)|Crea e inicializa un objeto de elemento del Shell a partir de un nombre de análisis.|  
|[AFX_GLOBAL_DATA::UpdateFonts](#updatefonts)|Reinicializa las fuentes lógicas utilizadas por el marco.|  
|[AFX_GLOBAL_DATA::UpdateSysColors](#updatesyscolors)|Inicializa los colores, la profundidad de color, los pinceles, los lápices y las imágenes utilizadas por el marco.|  
  
### <a name="protected-methods"></a>Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport)|Habilita o deshabilita la compatibilidad con Microsoft Active Accessibility. Active Accessibility proporciona métodos de confianza para exponer información sobre los elementos de la interfaz de usuario.|  
|[AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)|Indica si la compatibilidad con Microsoft Active Accessibility está habilitada.|  
|[Afx_global_data:: iswindowslayersupportavailable](#iswindowslayersupportavailable)|Indica si el sistema operativo admite ventanas superpuestas.|  
  
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


## <a name="bisosalphablendingsupport"></a> AFX_GLOBAL_DATA::bIsOSAlphaBlendingSupport
Indica si el sistema operativo admite la combinación alfa.  
  
  
```  
BOOL  bIsOSAlphaBlendingSupport;  
```  
  
### <a name="remarks"></a>Comentarios  
 TRUE indica que se admite la mezcla alfa; en caso contrario, FALSE.  
  

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
 *ángulo*  
 El ángulo de giro hacia la derecha, en grados.  
  
 *Centro*  
 Punto sobre el que se va a girar.  
  
 *matriz*  
 Cuando este método finaliza, contiene la transformación de rotación de nuevo. Debe asignar el almacenamiento para este parámetro.  
  
### <a name="return-value"></a>Valor devuelto  
 Lo contrario, devuelve S_OK si se realiza correctamente, o un valor de error.  
  
## <a name="drawparentbackground"></a> AFX_GLOBAL_DATA::DrawParentBackground
Dibuja el fondo del elemento primario de un control en el área especificada.  
  
  
```  
BOOL DrawParentBackground(
    CWnd* pWnd,   
    CDC* pDC,   
    LPRECT lpRect = NULL);
```  
  
### <a name="parameters"></a>Parámetros   
*conquistado*<br/>
[in] Puntero a la ventana de un control.  
  
*pDC*<br/>
[in] Puntero a un contexto de dispositivo.  
  
*lpRect*<br/>
[in] Puntero a un rectángulo que delimita el área que se va a dibujar. El valor predeterminado es NULL.  
  
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
[in] Identificador de los datos de una ventana del tema, o NULL. El marco de trabajo usa el tema especificado para dibujar el texto si este parámetro no es NULL y se admiten temas. En caso contrario, el marco no usa un tema para dibujar el texto.  
  
 Use la [OpenThemeData](/windows/desktop/api/uxtheme/nf-uxtheme-openthemedata) método para crear un HTHEME.  
  
*pDC*<br/>
[in] Puntero a un contexto de dispositivo.  
  
*iPartId*<br/>
[in] El elemento de control que tiene la apariencia del texto deseado. Para obtener más información, vea la columna de partes de la tabla en [Estados y elementos](https://msdn.microsoft.com/library/windows/desktop/bb773210). Si este valor es 0, el texto se dibuja en la fuente predeterminada o en una fuente seleccionada en el contexto del dispositivo.  
  
*iStateId*<br/>
[in] Estado del control que tiene la apariencia del texto deseado. Para obtener más información, vea la columna de Estados de la tabla en [Estados y elementos](https://msdn.microsoft.com/library/windows/desktop/bb773210).  
  
*strText*<br/>
[in] El texto que se va a dibujar.  
  
*Rect*<br/>
[in] El límite del área en la que se dibuja el texto especificado.  
  
*dwFlags*<br/>
[in] Una combinación bit a bit (OR) de marcadores que especifican cómo se dibuja el texto especificado.  
  
 Si el *hTheme* parámetro es `NULL` o si no están admitidos y se habilita, los temas del *nFormat* parámetro de la [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext) método describe válido marcas. Si se admiten temas, el *dwFlags* parámetro de la [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) método describe las marcas válidas.  
  
*nGlowSize*<br/>
[in] El tamaño de un efecto de iluminado que se dibuja en segundo plano antes de dibujar el texto especificado. El valor predeterminado es 0.  
  
*clrText*<br/>
[in] El color en el que se dibuja el texto especificado. El valor predeterminado es el color predeterminado.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se usa un tema para dibujar el texto especificado; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Un tema define el estilo visual de una aplicación. Un tema no se usa para dibujar el texto si el *hTheme* parámetro es NULL, o si el [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex) no se admite el método, o si [Administrador de ventanas de escritorio](/windows/desktop/dwm/dwm-overview) composición (DWM) está deshabilitado.  
  
### <a name="see-also"></a>Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [Estados y elementos](https://msdn.microsoft.com/library/windows/desktop/bb773210)   
 [CDC:: DrawText](../../mfc/reference/cdc-class.md#drawtext)   
 [DrawThemeTextEx](/windows/desktop/api/uxtheme/nf-uxtheme-drawthemetextex)   
 [Administrador de ventanas de escritorio](/windows/desktop/dwm/dwm-overview)   
 [Habilitar y controlar la composición de DWM](/windows/desktop/dwm/composition-ovw)

## <a name="enableaccessibilitysupport"></a> AFX_GLOBAL_DATA::EnableAccessibilitySupport
Habilita o deshabilita la compatibilidad con Microsoft Active Accessibility.  
  
  
```  
void EnableAccessibilitySupport(BOOL bEnable=TRUE);
```  
  
### <a name="parameters"></a>Parámetros   
*bHabilitar el*<br/>
[in] TRUE para habilitar la compatibilidad de accesibilidad; FALSE para deshabilitar la compatibilidad de accesibilidad. El valor predeterminado es TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Active Accessibility es una tecnología basada en COM que mejora el funcionamiento de los programas y el sistema operativo Windows trabajan junto con los productos de tecnología. Proporciona métodos confiables para exponer información sobre los elementos de interfaz de usuario. Sin embargo, ahora está disponible un nuevo modelo de accesibilidad llama a la automatización de interfaz de usuario de Microsoft. Para obtener una comparación de las dos tecnologías, consulte [UI Automation y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility).  
  
 Use la [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport) método para determinar si está habilitada la compatibilidad con Microsoft Active Accessibility.  
  
 
### <a name="see-also"></a>Vea también  
 [Automatización de interfaz de usuario y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)   
 [AFX_GLOBAL_DATA::IsAccessibilitySupport](#isaccessibilitysupport)

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
[in] Un búfer de texto.  
  
*lpszTag*<br/>
[in] El nombre de un par de apertura y cierre de las etiquetas XML.  
  
*strTag*<br/>
[out] Cuando este método finaliza, el *strTag* parámetro contiene el texto que se encuentra entre la apertura y cierre XML las etiquetas que se denominan mediante el *lpszTag* parámetro. Ningún espacio en blanco inicial o final se recorta del resultado.  
  
*bIsCharsList*<br/>
[in] True para los símbolos de convert para caracteres de escape en el *strTag* parámetro en caracteres de escape real; Si es FALSE, no para realizar la conversión. El valor predeterminado es FALSE. Para obtener más información, vea la sección Comentarios.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Un par de etiqueta XML consta de llamada de apertura y cierre de las etiquetas que indican el inicio y final de una ejecución de texto en el búfer especificado. El *strBuffer* parámetro especifica el búfer y el *lpszTag* parámetro especifica el nombre de las etiquetas XML.  
  
 Use los símbolos en la tabla siguiente para codificar un juego de caracteres de escape en el búfer especificado. Especifique TRUE para el *bIsCharsList* parámetro para convertir los símbolos en el *strTag* parámetro en caracteres de escape real. La tabla siguiente se usa el [_T ()](../../c-runtime-library/data-type-mappings.md) macro para especificar el símbolo de y las cadenas de caracteres de escape.  
  
|Símbolo|Carácter de escape|  
|------------|----------------------|  
|_T ("\\\t")|_T("\t")|  
|_T ("\\\n")|_T("\n")|  
|_T ("\\\r")|_T("\r")|  
|_T ("\\\b")|_T("\b")|  
|_T("LT")|_T ("\<")|  
|_T("GT")|_T("&GT;")|  
|_T("AMP")|_T("&AMP;")|  
  
## <a name="getcolor"></a> AFX_GLOBAL_DATA::GetColor
Recupera el color actual del elemento de la interfaz de usuario especificado.  
  
  
```  
COLORREF GetColor(int nColor);
```  
  
### <a name="parameters"></a>Parámetros   
*nColor*<br/>
[in] Un valor que especifica un elemento de la interfaz de usuario cuyo color se recupera. Para obtener una lista de valores válidos, vea el *nIndex* parámetro de la [GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor) método.  
  
### <a name="return-value"></a>Valor devuelto  
 El valor de color RGB del elemento de interfaz de usuario especificado. Para obtener más información, vea la sección Comentarios.  
  
### <a name="remarks"></a>Comentarios  
 Si el *nColor* parámetro está fuera del intervalo, el valor devuelto es cero. Dado que cero también es un valor RGB válido, no puede usar este método para determinar si un color del sistema es compatible con el sistema operativo actual. En su lugar, use el [GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush) método, que devuelve NULL si no se admite el color.  
  
### <a name="see-also"></a>Vea también  

 [Función GetSysColor](/windows/desktop/api/winuser/nf-winuser-getsyscolor)   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [GetSysColorBrush](/windows/desktop/api/winuser/nf-winuser-getsyscolorbrush)

## <a name="getdirect2dfactory"></a> AFX_GLOBAL_DATA::GetDirect2dFactory
 Devuelve un puntero a la interfaz de ID2D1Factory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.  
  
  
```  
ID2D1Factory* GetDirect2dFactory();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a interfaz de ID2D1Factory si la creación de una fábrica se realiza correctamente, o NULL si no se puede crear o sistema operativo actual no tiene compatibilidad D2D.  
  
## <a name="gethandcursor"></a>  AFX_GLOBAL_DATA::GetHandCursor
Recupera el cursor predefinido que se parece a una mano y cuyo identificador es IDC_HAND.  
  
  
```  
HCURSOR GetHandCursor();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El identificador del cursor de mano.  

## <a name="getnonclientmetrics"></a> AFX_GLOBAL_DATA::GetNonClientMetrics
Recupera las métricas asociadas al área no cliente de las ventanas no minimizadas.  
  
  
```  
BOOL GetNonClientMetrics(NONCLIENTMETRICS& info);
```  
  
### <a name="parameters"></a>Parámetros   
*Info*<br/>
[in, out] Un [NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175) estructura que contiene las métricas escalables asociadas con el área no cliente de una ventana no minimizada.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
 
  
### <a name="see-also"></a>Vea también   
 [Estructura NONCLIENTMETRICS](https://msdn.microsoft.com/library/windows/desktop/ff729175)

## <a name="gettextheight"></a> AFX_GLOBAL_DATA::GetTextHeight
 Recupera el alto de caracteres de texto en la fuente actual.  
  
  
```  
int GetTextHeight(BOOL bHorz = TRUE);
```  
  
### <a name="parameters"></a>Parámetros   
*bHorz*<br/>
[in] TRUE para recuperar el alto de caracteres al texto que se ejecuta horizontalmente; FALSE para recuperar el alto de caracteres al texto que se ejecuta verticalmente. El valor predeterminado es TRUE.  
  
### <a name="return-value"></a>Valor devuelto  
 El alto de la fuente actual, que se mide desde su ascender hasta su descendiente.  
  
## <a name="getwicfactory"></a> AFX_GLOBAL_DATA::GetWICFactory
Devuelve un puntero a la interfaz de IWICImagingFactory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.  
  
  
```  
IWICImagingFactory* GetWICFactory();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a interfaz de IWICImagingFactory si la creación de una fábrica se realiza correctamente, o NULL si no se puede crear o sistema operativo actual no tiene soporte técnico WIC.  
  
## <a name="getwritefactory"></a> AFX_GLOBAL_DATA::GetWriteFactory
Devuelve un puntero a la interfaz de IDWriteFactory que se almacena en los datos globales. Si no se inicializa la interfaz, se crea y tiene los parámetros predeterminados.  
  
  
```  
IDWriteFactory* GetWriteFactory();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a interfaz de IDWriteFactory si la creación de una fábrica se realiza correctamente, o NULL si no se puede crear o sistema operativo actual no tiene soporte técnico de DirectWrite.  
 
## <a name="initd2d"></a> AFX_GLOBAL_DATA::InitD2D
Inicializa los generadores de WIC, DirectWrite y D2D. Llame a este método antes de que se inicialice la ventana principal.  
  
  
```  
BOOL InitD2D(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,  
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```  
  
### <a name="parameters"></a>Parámetros   
 *d2dFactoryType*  
 El modelo de subprocesos de la fábrica D2D y los recursos que crea.  
  
 *writeFactoryType*  
 Un valor que especifica si el objeto de fábrica de escritura se comparten o aislado  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si los generadores eran intilalizrd, FALSE: en caso contrario  
  
## <a name="is32biticons"></a> AFX_GLOBAL_DATA::Is32BitIcons
Indica si se admiten los iconos de 32 bits predefinidos.  
  
  
```  
BOOL Is32BitIcons() const;

 
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se admiten los iconos de 32 bits predefinidos; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método devuelve TRUE si el marco admite iconos de 32 bits integrados, si el sistema operativo admite 16 bits por píxel o más, y si no se muestran imágenes en contraste alto.  
  
## <a name="isaccessibilitysupport"></a> AFX_GLOBAL_DATA::IsAccessibilitySupport
Indica si la compatibilidad con Microsoft Active Accessibility está habilitada.  
  
  
```  
BOOL IsAccessibilitySupport() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si está habilitada la compatibilidad de accesibilidad; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Microsoft Active Accessibility fue la solución anterior para hacer que las aplicaciones sean accesibles. Automatización de interfaz de usuario de Microsoft es el nuevo modelo de accesibilidad de Microsoft Windows y está pensado para abordar las necesidades de los productos de tecnología y herramientas de pruebas automatizadas.   
  
 Use la [AFX_GLOBAL_DATA::EnableAccessibilitySupport](#enableaccessibilitysupport) método para habilitar o deshabilitar la compatibilidad con Active Accessibility.  
  

### <a name="see-also"></a>Vea también  
 [Automatización de la interfaz de usuario y Microsoft Active Accessibility](/dotnet/framework/ui-automation/ui-automation-and-microsoft-active-accessibility)

## <a name="isd2dinitialized"></a> AFX_GLOBAL_DATA::IsD2DInitialized
 Determina si se ha inicializado el D2D  
  
  
```  
BOOL IsD2DInitialized() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se inicializó D2D; en caso contrario, FALSE.  
  
## <a name="isdwmcompositionenabled"></a> AFX_GLOBAL_DATA::IsDwmCompositionEnabled
Proporciona una manera sencilla para llamar a la Windows [DwmIsCompositionEnabled](/windows/desktop/api/dwmapi/nf-dwmapi-dwmiscompositionenabled) método.  
  
  
```  
BOOL IsDwmCompositionEnabled();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si [Administrador de ventanas de escritorio](/windows/desktop/dwm/dwm-overview) composición (DWM) está habilitada; en caso contrario, FALSE.  
  
### <a name="see-also"></a>Vea también    
 [Administrador de ventanas de escritorio](/windows/desktop/dwm/dwm-overview)   
 [Habilitar y controlar la composición de DWM](/windows/desktop/dwm/composition-ovw)

## <a name="ishighcontrastmode"></a> AFX_GLOBAL_DATA::IsHighContrastMode
 Indica si las imágenes se muestran actualmente en contraste alto.    
```  
BOOL IsHighContrastMode() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si las imágenes se muestran actualmente en modo de contraste alto o negro; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 En el modo de contraste alto negro, orientado a la luz de bordes son el blancos y el fondo negro. En el modo de contraste alto en blanco, son de color negros orientado a la luz de los bordes y el fondo es blanco.  
  
## <a name="iswindowslayersupportavailable"></a> Afx_global_data:: iswindowslayersupportavailable
Indica si el sistema operativo admite ventanas superpuestas.  
  
  
```  
BOOL IsWindowsLayerSupportAvailable() const; 
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si se admiten las ventanas superpuestas; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Si se admiten las ventanas por capas, *acoplamiento inteligente* marcadores de usar las ventanas superpuestas.  
  
## <a name="m_busebuiltin32biticons"></a> AFX_GLOBAL_DATA::m_bUseBuiltIn32BitIcons
Indica si el marco usa iconos de colores de 32 bits predefinidos o iconos de una resolución inferior.  
  
  
```  
BOOL  m_bUseBuiltIn32BitIcons;  
```  
  
### <a name="remarks"></a>Comentarios  
 TRUE especifica que el marco de trabajo utilizan los iconos de color de 32 bits; FALSE especifica los iconos de resolución inferior. El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en TRUE.  
  
 Este miembro debe establecerse al iniciar la aplicación.  
  
## <a name="m_busesystemfont"></a> AFX_GLOBAL_DATA::m_bUseSystemFont
Indica si se usa una fuente del sistema para los menús, las barras de herramientas y las cintas.  
  
  
```  
BOOL m_bUseSystemFont;  
```  
  
### <a name="remarks"></a>Comentarios  
 TRUE especifica que se use una fuente del sistema; en caso contrario, FALSE. El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en FALSE.  
  
 Las pruebas de este miembro no es la única forma para el marco de trabajo determinar la fuente de usar. El `AFX_GLOBAL_DATA::UpdateFonts` método también comprueba las fuentes predeterminadas y alternativas para determinar qué estilos visuales están disponibles para aplicarse a los menús, barras de herramientas y las cintas.  
  
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
Especifica el desplazamiento de la barra de herramientas Ocultar automáticamente situada más a la izquierda de la barra de acoplamiento.  
  
  
```  
int  m_nAutoHideToolBarMargin;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro de 4 píxeles.  
  
## <a name="m_nautohidetoolbarspacing"></a> AFX_GLOBAL_DATA::m_nAutoHideToolBarSpacing
Especifica la separación entre las barras de herramientas Ocultar automáticamente.  
  
  
```  
int   m_nAutoHideToolBarSpacing;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro a 14 píxeles.  
  
## <a name="m_ndragframethicknessdock"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessDock

Especifica el grosor del marco de arrastrar que se usa para indicar el estado acoplado.  
  
  
```  
int  m_nDragFrameThicknessDock;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro en 3 píxeles.  
  
## <a name="m_ndragframethicknessfloat"></a> AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat
Especifica el grosor del marco de arrastrar que se usa para indicar el estado flotante.  
  
  
```  
int  m_nDragFrameThicknessFloat;  
```  
  
### <a name="remarks"></a>Comentarios  
 El `AFX_GLOBAL_DATA::AFX_GLOBAL_DATA` constructor inicializa este miembro de 4 píxeles.  
  
## <a name="onsettingchange"></a> AFX_GLOBAL_DATA::OnSettingChange
Detecta el estado actual de las características del escritorio para la animación de menús y para ocultar automáticamente la barra de tareas.  
  
  
```  
void OnSettingChange();
```  
  
### <a name="remarks"></a>Comentarios  
 Este método establece las variables de marco de trabajo en el estado de ciertos atributos del escritorio del usuario. Este método detecta el estado actual de la animación de menús, atenuación de menús y barra de funciones de ocultación automática de tareas.  
  
## <a name="registerwindowclass"></a> AFX_GLOBAL_DATA::RegisterWindowClass
Registra la clase de ventana MFC especificada.  
  
  
```  
CString RegisterWindowClass(LPCTSTR lpszClassNamePrefix);
```  
  
### <a name="parameters"></a>Parámetros   
*lpszClassNamePrefix*<br/>
[in] El nombre de la clase de ventana para registrar.  
  
### <a name="return-value"></a>Valor devuelto  
 El nombre completo de la clase registrada si este método se realiza correctamente; en caso contrario, un [excepción recursos](exception-processing.md#afxthrowresourceexception).  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto es una lista delimitada por signos de la *lpszClassNamePrefix* la cadena de parámetros y las representaciones de texto hexadecimal de los manipuladores de la instancia actual de la aplicación; el cursor de la aplicación, que es la flecha cursor cuyo identificador es IDC_ARROW; y el pincel del fondo. Para obtener más información sobre cómo registrar las clases de ventana MFC, vea [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass).  
  
### <a name="see-also"></a>Vea también    
 [AfxRegisterClass](../../mfc/reference/application-information-and-management.md#afxregisterclass)   
 [AfxThrowResourceException](../../mfc/reference/exception-processing.md#afxthrowresourceexception)

## <a name="resume"></a> AFX_GLOBAL_DATA::resume
 Reinicializa los punteros a función internos que tienen acceso a los métodos que admiten los temas de Windows y los estilos visuales. 
  
  
```  
BOOL Resume();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE. En modo de depuración, este método declara si este método es incorrecto.  
  
### <a name="remarks"></a>Comentarios  
 Este método se llama cuando el marco de trabajo recibe el [WM_POWERBROADCAST](/windows/desktop/Power/wm-powerbroadcast) mensaje.  
  
## <a name="setlayeredattrib"></a> AFX_GLOBAL_DATA::SetLayeredAttrib
Proporciona una manera sencilla para llamar a la Windows [SetLayeredWindowAttributes](/windows/desktop/api/winuser/nf-winuser-setlayeredwindowattributes) método.  
  
  
```  
BOOL SetLayeredAttrib(
    HWND hwnd,  
    COLORREF crKey,  
    BYTE bAlpha,  
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parámetros   
*HWND*<br/>
[in] Identificador de la ventana por capas.  
  
*crKey*<br/>
[in] El color de transparencia de clave que el [Administrador de ventanas de escritorio](/windows/desktop/dwm/dwm-overview) usa para componer la ventana por capas.  
  
*bAlpha*<br/>
[in] El valor alfa que se usa para describir la opacidad de la ventana superpuesta.  
  
*dwFlags*<br/>
[in] Una combinación bit a bit (OR) de marcadores que especifican qué parámetros de método que se usarán. Especificar LWA_COLORKEY para usar el *crKey* parámetro como el color de transparencia. Especificar LWA_ALPHA para usar el *bAlpha* parámetro para determinar la opacidad de la ventana superpuesta.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.   
 
### <a name="see-also"></a>Vea también   
 [COLORREF](/windows/desktop/gdi/colorref)   
 [SetLayeredWindowAttributes](/windows/desktop/api/winuser/nf-winuser-setlayeredwindowattributes)

## <a name="setmenufont"></a> AFX_GLOBAL_DATA::SetMenuFont
Crea la fuente lógica especificada.  
  
  
```  
BOOL SetMenuFont(
    LPLOGFONT lpLogFont,  
    BOOL bHorz);
```  
  
### <a name="parameters"></a>Parámetros   
*lpLogFont*<br/>
[in] Puntero a una estructura que contiene los atributos de una fuente.  
  
*bHorz*<br/>
[in] TRUE para especificar que las ejecuciones de texto horizontalmente; FALSE para especificar que las ejecuciones de texto verticalmente.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE. En modo de depuración, este método declara si este método es incorrecto.  
  
### <a name="remarks"></a>Comentarios  
 Este método crea una fuente regular horizontal, una fuente subrayada, y una fuente en negrita que usa de forma predeterminada en los elementos de menú. Opcionalmente, este método crea una fuente vertical regular. Para obtener más información acerca de las fuentes lógicas, consulte [CFont::CreateFontIndirect](../../mfc/reference/cfont-class.md#createfontindirect).  
  
## <a name="updatefonts"></a> AFX_GLOBAL_DATA::UpdateFonts
Reinicializa las fuentes lógicas utilizadas por el marco.  
  
  
```  
void UpdateFonts();
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de las fuentes lógicas, consulte `CFont::CreateFontIndirect`.  
  
## <a name="updatesyscolors"></a> AFX_GLOBAL_DATA::UpdateSysColors
Inicializa los colores, la profundidad de color, los pinceles, los lápices y las imágenes utilizadas por el marco.  
  
  
```  
void UpdateSysColors();
```  
  
## <a name="biswindows7"></a> AFX_GLOBAL_DATA::bIsWindows7
Indica si la aplicación se está ejecutando en Windows 7 o posterior.  
  
  
```  
BOOL bIsWindows7;  
```  
  
## <a name="clractivecaptiongradient"></a> AFX_GLOBAL_DATA::clrActiveCaptionGradient
Especifica el color del degradado de la leyenda activa. Se suele utilizar para acoplar paneles.  
  
  
```  
COLORREF clrActiveCaptionGradient;  
```  
  
## <a name="clrinactivecaptiongradient"></a> AFX_GLOBAL_DATA::clrInactiveCaptionGradient
Especifica el color del degradado de la leyenda inactiva. Se suele utilizar para acoplar paneles.  
  
  
```  
COLORREF clrInactiveCaptionGradient;  
```  
  
## <a name="getitaskbarlist"></a> AFX_GLOBAL_DATA::GetITaskbarList
Crea y almacena en los datos globales un puntero a la `ITaskBarList` interfaz.  
  
  
```  
ITaskbarList *GetITaskbarList();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `ITaskbarList` interfaz si se realiza correctamente la creación de una barra de objeto de lista de tareas; NULL si no se puede crear o si el sistema operativo actual es menor que Windows 7.  
  
## <a name="getitaskbarlist3"></a> AFX_GLOBAL_DATA::GetITaskbarList3
Crea y almacena en los datos globales un puntero a la `ITaskBarList3` interfaz.  
  
  
```  
ITaskbarList3 *GetITaskbarList3();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a la `ITaskbarList3` interfaz si se realiza correctamente la creación de una barra de objeto de lista de tareas; NULL si no se puede crear o si el sistema operativo actual es menor que Windows 7.  
  
## <a name="getshellautohidebars"></a> AFX_GLOBAL_DATA::GetShellAutohideBars
Determina las posiciones de las barras Ocultar automáticamente del Shell.  
  
  
```  
int GetShellAutohideBars();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor entero con codificado marcadores que especifican las posiciones de auto ocultar las barras. Puede combinar los siguientes valores: AFX_AUTOHIDE_BOTTOM, AFX_AUTOHIDE_TOP, AFX_AUTOHIDE_LEFT, AFX_AUTOHIDE_RIGHT.  
  
## <a name="releasetaskbarrefs"></a> AFX_GLOBAL_DATA::ReleaseTaskBarRefs
Libera las interfaces obtenidas a través de la `GetITaskbarList` y `GetITaskbarList3` métodos.  
  
  
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
 *pszPath*  
 [in] Un puntero a un nombre para mostrar.  
  
 *PBC*  
 Un puntero a un contexto de enlace que controla la operación de análisis.  
  
 *riid*  
 Una referencia a un identificador de interfaz.  
  
 *PPV*  
 [out] Cuando esta función devuelve, contiene el puntero de interfaz solicitado en *riid*. Normalmente será `IShellItem` o `IShellItem2`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se realiza correctamente; un valor de error en caso contrario.  

