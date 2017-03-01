---
title: CMonthCalCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMonthCalCtrl
dev_langs:
- C++
helpviewer_keywords:
- month calendar controls, CMonthCalCtrl class
- common controls, Internet Explorer 4.0
- CMonthCalCtrl class
- Internet Explorer 4.0 common controls
- month calendar controls
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 96cefbeb7692a07088f596fe08fec2bf179b98bc
ms.lasthandoff: 02/24/2017

---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl (clase)
Encapsula la funcionalidad de un control de calendario mensual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Construye un objeto `CMonthCalCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CMonthCalCtrl::Create](#create)|Crea un control de calendario mensual y lo adjunta a la `CMonthCalCtrl` objeto.|  
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Recupera el ancho del borde del control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Recupera el número de calendarios que se muestran en el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Recupera información sobre el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCalID](#getcalid)|Recupera el identificador de calendario para el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetColor](#getcolor)|Obtiene el color de un área especificada de un control de calendario mensual.|  
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Recupera la vista que se muestra actualmente en el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCurSel](#getcursel)|Recupera la hora del sistema como se indica por la fecha seleccionada actualmente.|  
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Obtiene el primer día de la semana que se mostrará en la columna más a la izquierda del calendario.|  
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Recupera el actual número máximo de días que se pueden seleccionar en un control de calendario mensual.|  
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Recupera el ancho máximo de la cadena "Hoy" para el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario mensual.|  
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Recupera la tasa de desplazamiento para un control de calendario mensual.|  
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Recupera la información que representa los límites superior e inferior de pantalla del control de calendario mensual de fecha.|  
|[CMonthCalCtrl::GetRange](#getrange)|Recupera las fechas mínimas y máxima actuales que se establece en un control de calendario mensual.|  
|[CMonthCalCtrl::GetSelRange](#getselrange)|Recupera información de fecha que representa los límites superiores e inferiores del intervalo de fechas seleccionado actualmente por el usuario.|  
|[CMonthCalCtrl::GetToday](#gettoday)|Recupera la información de fecha de la fecha especificada como "hoy" para un control de calendario mensual.|  
|[CMonthCalCtrl::HitTest](#hittest)|Determina qué sección de un control de calendario mensual se encuentra en un punto determinado en la pantalla.|  
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Indica si la vista actual del control de calendario mensual actual es la vista de siglo.|  
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Indica si la vista actual del control de calendario mensual actual es la vista de la década.|  
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Indica si la vista actual del control de calendario mensual actual es la vista del mes.|  
|[CMonthCalCtrl::IsYearView](#isyearview)|Indica si la vista actual del control de calendario mensual actual es la vista de año.|  
|[CMonthCalCtrl::SetCalendarBorder](#setcalendarborder)|Establece el ancho del borde del control de calendario del mes actual.|  
|[CMonthCalCtrl::SetCalendarBorderDefault](#setcalendarborderdefault)|Establece el ancho predeterminado del borde del control de calendario del mes actual.|  
|[CMonthCalCtrl::SetCalID](#setcalid)|Establece el identificador de calendario para el control de calendario del mes actual.|  
|[CMonthCalCtrl::SetCenturyView](#setcenturyview)|Establece el control de calendario del mes actual para mostrar la vista de siglo.|  
|[CMonthCalCtrl::SetColor](#setcolor)|Establece el color de un área especificada de un control de calendario mensual.|  
|[CMonthCalCtrl::SetCurrentView](#setcurrentview)|Establece el control de calendario del mes actual para mostrar la vista especificada.|  
|[CMonthCalCtrl::SetCurSel](#setcursel)|Establece la fecha seleccionada actualmente para un control de calendario mensual.|  
|[CMonthCalCtrl:: SetDayState](#setdaystate)|Establece la presentación de días en un control de calendario mensual.|  
|[CMonthCalCtrl::SetDecadeView](#setdecadeview)|Establece el calendario del mes actual control a la vista de la década.|  
|[CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek)|Establece el día de la semana que se mostrará en la columna más a la izquierda del calendario.|  
|[CMonthCalCtrl::SetMaxSelCount](#setmaxselcount)|Establece el número máximo de días que se pueden seleccionar en un control de calendario mensual.|  
|[CMonthCalCtrl::SetMonthDelta](#setmonthdelta)|Establece la tasa de desplazamiento para un control de calendario mensual.|  
|[CMonthCalCtrl::SetMonthView](#setmonthview)|Establece el control de calendario del mes actual para mostrar la vista del mes.|  
|[CMonthCalCtrl::SetRange](#setrange)|Establece los valores mínimo y máximo permitido de fechas para un control de calendario mensual.|  
|[CMonthCalCtrl::SetSelRange](#setselrange)|Establece la selección de un calendario de mes control con un intervalo de fechas determinado.|  
|[CMonthCalCtrl::SetToday](#settoday)|Establece el control de calendario para el día actual.|  
|[CMonthCalCtrl::SetYearView](#setyearview)|Establece el calendario del mes actual control a la vista de año.|  
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Vuelve a dibujar el calendario mensual control a su tamaño mínimo, un mes.|  
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Para el control de calendario del mes actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo determinado.|  
  
## <a name="remarks"></a>Comentarios  
 El control de calendario mensual proporciona al usuario con una interfaz de calendario simple, desde el que el usuario puede seleccionar una fecha. El usuario puede cambiar la visualización por:  
  
-   Desplazarse hacia atrás y hacia delante, de mes a mes.  
  
-   Haga clic en el texto de hoy para mostrar la fecha actual (si la **MCS_NOTODAY** no se utiliza el estilo).  
  
-   Seleccionar un mes o un año a partir de un menú emergente.  
  
 Puede personalizar el mes de calendario control aplicando una variedad de estilos para el objeto al crearlo. Estos estilos se describen en [estilos de Control de calendario de mes](http://msdn.microsoft.com/library/windows/desktop/bb760919) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 El control de calendario mensual puede mostrar más de un mes, y puede indicar los días especiales (como festividades) mediante negrita la fecha.  
  
 Para obtener más información acerca de cómo utilizar el control de calendario mensual, consulte [utilizar CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdtctl.h  
  
##  <a name="a-namecmonthcalctrla--cmonthcalctrlcmonthcalctrl"></a><a name="cmonthcalctrl"></a>CMonthCalCtrl::CMonthCalCtrl  
 Construye un objeto `CMonthCalCtrl`.  
  
```  
CMonthCalCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Se debe llamar a **crear** después de crear el objeto.  
  
##  <a name="a-namecreatea--cmonthcalctrlcreate"></a><a name="create"></a>CMonthCalCtrl::Create  
 Crea un control de calendario mensual y lo adjunta a la `CMonthCalCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);

 
virtual BOOL Create(
    DWORD dwStyle,  
    const POINT& pt,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica la combinación de los estilos de Windows aplicados al control de calendario mensual. Consulte [estilos de Control de calendario de mes](http://msdn.microsoft.com/library/windows/desktop/bb760919) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de los estilos.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura. Contiene la posición y el tamaño del control de calendario mensual.  
  
 `pt`  
 Una referencia a un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura que identifica la ubicación del control de calendario mensual.  
  
 `pParentWnd`  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto de la ventana primaria del control de calendario mensual. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador del control. del control de calendario mensual  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la inicialización es correcta; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Creación de un mes del calendario control en dos pasos:  
  
1.  Llame a [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) para construir un `CMonthCalCtrl` objeto.  
  
2.  Llame a esta función miembro, que crea un control de calendario mensual y lo adjunta a la `CMonthCalCtrl` objeto.  
  
 Cuando se llama a **crear**, se inicializan los controles comunes. La versión de **crear** , llamada determina cómo tiene un tamaño:  
  
-   Para que MFC automáticamente el tamaño del control a un mes, llame a la invalidación que usa el `pt` parámetro.  
  
-   Para ajustar el control, llame a la invalidación de esta función que usa el `rect` parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CMonthCalCtrl](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]  
  
##  <a name="a-namegetcalendarbordera--cmonthcalctrlgetcalendarborder"></a><a name="getcalendarborder"></a>CMonthCalCtrl::GetCalendarBorder  
 Recupera el ancho del borde del control de calendario del mes actual.  
  
```  
int GetCalendarBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del borde del control, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760945) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetcalendarcounta--cmonthcalctrlgetcalendarcount"></a><a name="getcalendarcount"></a>CMonthCalCtrl::GetCalendarCount  
 Recupera el número de calendarios que se muestran en el control de calendario del mes actual.  
  
```  
int GetCalendarCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de calendarios que se muestra actualmente en el control de calendario mensual. El número máximo permitido de calendarios es 12.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCALENDARCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760947) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetcalendargridinfoa--cmonthcalctrlgetcalendargridinfo"></a><a name="getcalendargridinfo"></a>CMonthCalCtrl::GetCalendarGridInfo  
 Recupera información sobre el control de calendario del mes actual.  
  
```  
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `pmcGridInfo`|Puntero a un [MCGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760925) estructura que recibe información sobre el control de calendario del mes actual. El llamador es responsable de asignar e inicializar esta estructura.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCALENDARGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760949) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_monthCalCtrl`, que se utiliza para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código utiliza el `GetCalendarGridInfo` método para recuperar la fecha del calendario que muestra el control de calendario del mes actual.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1&3;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]  
  
##  <a name="a-namegetcalida--cmonthcalctrlgetcalid"></a><a name="getcalid"></a>CMonthCalCtrl::GetCalID  
 Recupera el identificador de calendario para el control de calendario del mes actual.  
  
```  
CALID GetCalID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los [identificador de calendario](http://msdn.microsoft.com/library/windows/desktop/dd317732) constantes.  
  
### <a name="remarks"></a>Comentarios  
 Un identificador de calendario denota un calendario específico de la región, como gregoriano (localizado), japonés o Hijri calendarios. La aplicación puede utilizar un identificador de calendario que tiene varios idiomas admite funciones.  
  
 Este método envía el [MCM_GETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760951) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetcolora--cmonthcalctrlgetcolor"></a><a name="getcolor"></a>CMonthCalCtrl::GetColor  
 Recupera el color de un área del mes especificado por el control de calendario `nRegion`.  
  
```  
COLORREF GetColor(int nRegion) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `nRegion`  
 La región del control de calendario mensual del que se recupera el color. Para obtener una lista de valores, vea el `nRegion` parámetro de [SetColor](#setcolor).  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que especifica el color asociado a la parte del control de calendario mensual, si se realiza correctamente. De lo contrario, esta función miembro devuelve -1.  
  
##  <a name="a-namegetcurrentviewa--cmonthcalctrlgetcurrentview"></a><a name="getcurrentview"></a>CMonthCalCtrl::GetCurrentView  
 Recupera la vista que se muestra actualmente en el control de calendario del mes actual.  
  
```  
DWORD GetCurrentView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La vista actual, que se indica mediante uno de los siguientes valores:  
  
|Valor|Significado|  
|-----------|-------------|  
|`MCMV_MONTH`|Vista mensual|  
|`MCMV_YEAR`|Vista anual|  
|`MCMV_DECADE`|Vista de la década|  
|`MCMV_CENTURY`|Vista de siglo|  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_monthCalCtrl`, que se utiliza para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 Los siguientes informes de ejemplo de código que permite ver el calendario mensual controlan muestra actualmente.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]  
  
##  <a name="a-namegetcursela--cmonthcalctrlgetcursel"></a><a name="getcursel"></a>CMonthCalCtrl::GetCurSel  
 Recupera la hora del sistema como se indica por la fecha seleccionada actualmente.  
  
```  
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;  
   
BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `refDateTime`  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto. Recibe la hora actual.  
  
 `pDateTime`  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que recibirá la información de la fecha seleccionada actualmente. Este parámetro debe ser una dirección válida y no puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si es correcto; otherwize 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb760957), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
> [!NOTE]
>  Esta función miembro produce un error si el estilo **MCS_MULTISELECT** se establece.  
  
 En la implementación de MFC de `GetCurSel`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
##  <a name="a-namegetfirstdayofweeka--cmonthcalctrlgetfirstdayofweek"></a><a name="getfirstdayofweek"></a>CMonthCalCtrl::GetFirstDayOfWeek  
 Obtiene el primer día de la semana que se mostrará en la columna más a la izquierda del calendario.  
  
```  
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pbLocal*  
 Un puntero a un **BOOL** valor. Si el valor es distinto de cero, el valor del control no coincide con la configuración en el panel de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor entero que representa el primer día de la semana. Consulte **comentarios** para obtener más información sobre estos enteros que representan.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb760958), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Los días de la semana se representan como números enteros, como sigue.  
  
|Valor|Día de la semana|  
|-----------|---------------------|  
|0|Lunes|  
|1|Martes|  
|2|Miércoles|  
|3|Jueves|  
|4|Viernes|  
|5|Sábado|  
|6|Domingo|  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl::SetFirstDayOfWeek](#setfirstdayofweek).  
  
##  <a name="a-namegetmaxselcounta--cmonthcalctrlgetmaxselcount"></a><a name="getmaxselcount"></a>CMonthCalCtrl::GetMaxSelCount  
 Recupera el actual número máximo de días que se pueden seleccionar en un control de calendario mensual.  
  
```  
int GetMaxSelCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor entero que representa el número total de días que se pueden seleccionar para el control.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760960), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Utilice esta función miembro para los controles con el **MCS_MULTISELECT** conjunto de estilos.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).  
  
##  <a name="a-namegetmaxtodaywidtha--cmonthcalctrlgetmaxtodaywidth"></a><a name="getmaxtodaywidth"></a>CMonthCalCtrl::GetMaxTodayWidth  
 Recupera el ancho máximo de la cadena "Hoy" para el control de calendario del mes actual.  
  
```  
DWORD GetMaxTodayWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho de la cadena "Hoy", en píxeles.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_monthCalCtrl`, que se utiliza para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `GetMaxTodayWidth` método.  
  
 [!code-cpp[1 NVC_MFC_CMonthCalCtrl_s1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]  
  
### <a name="remarks"></a>Comentarios  
 El usuario puede volver a la fecha actual, haga clic en la cadena "Hoy", que se muestra en la parte inferior del control de calendario mensual. La cadena "Hoy" incluye el texto de etiqueta y fecha.  
  
 Este método envía el [MCM_GETMAXTODAYWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760962) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetminreqrecta--cmonthcalctrlgetminreqrect"></a><a name="getminreqrect"></a>CMonthCalCtrl::GetMinReqRect  
 Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario mensual.  
  
```  
BOOL GetMinReqRect(RECT* pRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pRect`  
 Un puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibirá información de rectángulo delimitador. Este parámetro debe ser una dirección válida y no puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, esta función miembro devuelve distinto de cero y `lpRect` recibe la información de límite aplicable. Si no lo consigue, la función miembro devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMINREQRECT](http://msdn.microsoft.com/library/windows/desktop/bb760978), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetmonthdeltaa--cmonthcalctrlgetmonthdelta"></a><a name="getmonthdelta"></a>CMonthCalCtrl::GetMonthDelta  
 Recupera la tasa de desplazamiento para un control de calendario mensual.  
  
```  
int GetMonthDelta() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La tasa de desplazamiento para el control de calendario mensual. La tasa de desplazamiento es el número de meses que el control mueve su presentación cuando el usuario hace clic en un botón de desplazamiento de una vez.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb760980), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namegetmonthrangea--cmonthcalctrlgetmonthrange"></a><a name="getmonthrange"></a>CMonthCalCtrl::GetMonthRange  
 Recupera la información que representa los límites superior e inferior de pantalla del control de calendario mensual de fecha.  
  
```  
int GetMonthRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    CTime& refMinRange,  
    CTime& refMaxRange,  
    DWORD dwFlags) const;  
  
int GetMonthRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange,  
    DWORD dwFlags) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `refMinRange`  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la fecha mínima permitida.  
  
 `refMaxRange`  
 Una referencia a un `COleDateTime` o `CTime` objeto que contiene la fecha máxima permitida.  
  
 `pMinRange`  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 `pMaxRange`  
 Un puntero a un `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
 `dwFlags`  
 Valor que especifica el ámbito de los límites del intervalo que se va a recuperar. Este valor debe ser uno de los siguientes.  
  
|Valor|Significado|  
|-----------|-------------|  
|GMR_DAYSTATE|Incluir iniciales ni finales meses del rango visible que sólo se muestran parcialmente.|  
|GMR_VISIBLE|Incluir sólo los meses que se muestran por completo.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un entero que representa el intervalo en meses, abarca los dos límites indicado por `refMinRange` y `refMaxRange` en las versiones de primeros y segunda, o `pMinRange` y `pMaxRange` en la tercera versión.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMONTHRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760981), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de `GetMonthRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl:: SetDayState](#setdaystate).  
  
##  <a name="a-namegetrangea--cmonthcalctrlgetrange"></a><a name="getrange"></a>CMonthCalCtrl::GetRange  
 Recupera las fechas mínimas y máxima actuales que se establece en un control de calendario mensual.  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
  
DWORD GetRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pMinRange`  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 `pMaxRange`  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `DWORD` que puede ser cero (no se establecen límites) o una combinación de los siguientes valores que especifican información de límite.  
  
|Valor|Significado|  
|-----------|-------------|  
|GDTR_MAX|Se establece un límite máximo para el control; `pMaxRange` es válido y contiene la información de fecha es aplicable.|  
|GDTR_MIN|Se establece un límite mínimo para el control; `pMinRange` es válido y contiene la información de fecha es aplicable.|  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760983), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de `GetRange`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl&#2;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]  
  
##  <a name="a-namegetselrangea--cmonthcalctrlgetselrange"></a><a name="getselrange"></a>CMonthCalCtrl::GetSelRange  
 Recupera información de fecha que representa los límites superiores e inferiores del intervalo de fechas seleccionado actualmente por el usuario.  
  
```  
BOOL GetSelRange(
    COleDateTime& refMinRange,  
    COleDateTime& refMaxRange) const;  
  
BOOL GetSelRange(
    CTime& refMinRange,  
    CTime& refMaxRange) const;  
  
BOOL GetSelRange(
    LPSYSTEMTIME pMinRange,  
    LPSYSTEMTIME pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `refMinRange`  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la fecha mínima permitida.  
  
 `refMaxRange`  
 Una referencia a un `COleDateTime` o `CTime` objeto que contiene la fecha máxima permitida.  
  
 `pMinRange`  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 `pMaxRange`  
 Un puntero a un `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760985), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. `GetSelRange`se producirá un error si se aplica a un control de calendario mensual que no utilice la **MCS_MULTISELECT** estilo.  
  
 En la implementación de MFC de `GetSelRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
##  <a name="a-namegettodaya--cmonthcalctrlgettoday"></a><a name="gettoday"></a>CMonthCalCtrl::GetToday  
 Recupera la información de fecha de la fecha especificada como "hoy" para un control de calendario mensual.  
  
```  
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;  
   
BOOL GetToday(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `refDateTime`  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que indica el día actual.  
  
 `pDateTime`  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que recibirá la información de fecha. Este parámetro debe ser una dirección válida y no puede ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb760987), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de `GetToday`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl&3;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]  
  
##  <a name="a-namehittesta--cmonthcalctrlhittest"></a><a name="hittest"></a>CMonthCalCtrl::HitTest  
 Determina qué control de calendario mensual, si los hay, está en una posición especificada.  
  
```  
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```  
  
### <a name="parameters"></a>Parámetros  
 *pMCHitTest*  
 Un puntero a un [MCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760927) estructura que contiene la prueba de posicionamiento los puntos de control de calendario mensual.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor `DWORD`. Igual que el **uHit** miembro de la **MCHITTESTINFO** estructura.  
  
### <a name="remarks"></a>Comentarios  
 `HitTest`usa el **MCHITTESTINFO** estructura, que contiene información acerca de la prueba de posicionamiento.  
  
##  <a name="a-nameiscenturyviewa--cmonthcalctrliscenturyview"></a><a name="iscenturyview"></a>CMonthCalCtrl::IsCenturyView  
 Indica si la vista actual del control de calendario mensual actual es la vista de siglo.  
  
```  
BOOL IsCenturyView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la vista actual es el siglo; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Si mensaje devuelve `MCMV_CENTURY`, este método devuelve `true`.  
  
##  <a name="a-nameisdecadeviewa--cmonthcalctrlisdecadeview"></a><a name="isdecadeview"></a>CMonthCalCtrl::IsDecadeView  
 Indica si la vista actual del control de calendario mensual actual es la vista de la década.  
  
```  
BOOL IsDecadeView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la vista actual es la década; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Si mensaje devuelve `MCMV_DECADE`, este método devuelve `true`.  
  
##  <a name="a-nameismonthviewa--cmonthcalctrlismonthview"></a><a name="ismonthview"></a>CMonthCalCtrl::IsMonthView  
 Indica si la vista actual del control de calendario mensual actual es la vista del mes.  
  
```  
BOOL IsMonthView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la vista actual es el mes; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Si mensaje devuelve `MCMV_MONTH`, este método devuelve `true`.  
  
##  <a name="a-nameisyearviewa--cmonthcalctrlisyearview"></a><a name="isyearview"></a>CMonthCalCtrl::IsYearView  
 Indica si la vista actual del control de calendario mensual actual es la vista de año.  
  
```  
BOOL IsYearView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si la vista actual es el año; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. Si mensaje devuelve `MCMV_YEAR`, este método devuelve `true`.  
  
##  <a name="a-namesetcalendarbordera--cmonthcalctrlsetcalendarborder"></a><a name="setcalendarborder"></a>CMonthCalCtrl::SetCalendarBorder  
 Establece el ancho del borde del control de calendario del mes actual.  
  
```  
void SetCalendarBorder(int cxyBorder);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `cxyBorder`|El ancho del borde, en píxeles.|  
  
### <a name="remarks"></a>Comentarios  
 Si este método se realiza correctamente, se establece el ancho del borde en el `cxyBorder` parámetro. De lo contrario, el ancho del borde se restablece al valor predeterminado especificado por actual [tema](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), o cero si no se utilizan temas.  
  
 Este método envía el [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_monthCalCtrl`, que se utiliza para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 Ejemplo de código siguiente se establece el ancho del borde del calendario del mes control a ocho píxeles. Utilice la [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) método para determinar si este método se realizó correctamente.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1 Nº&6;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]  
  
##  <a name="a-namesetcalendarborderdefaulta--cmonthcalctrlsetcalendarborderdefault"></a><a name="setcalendarborderdefault"></a>CMonthCalCtrl::SetCalendarBorderDefault  
 Establece el ancho predeterminado del borde del control de calendario del mes actual.  
  
```  
void SetCalendarBorderDefault();
```  
  
### <a name="remarks"></a>Comentarios  
 El ancho del borde se establece en el valor predeterminado especificado por el actual [tema](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), o cero si no se utilizan temas.  
  
 Este método envía el [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetcalida--cmonthcalctrlsetcalid"></a><a name="setcalid"></a>CMonthCalCtrl::SetCalID  
 Establece el identificador de calendario para el control de calendario del mes actual.  
  
```  
BOOL SetCalID(CALID calid);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `calid`|Uno de los [identificador de calendario](http://msdn.microsoft.com/library/windows/desktop/dd317732) constantes.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Un identificador de calendario especifica un calendario específico de la región, como gregoriano (localizado), japonés o Hijri calendarios. Utilice la `SetCalID` método para mostrar un calendario especificado por el `calid` parámetro si la configuración regional que contiene el calendario está instalada en el equipo.  
  
 Este método envía el [MCM_SETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760995) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_monthCalCtrl`, que se utiliza para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el control de calendario mensual para mostrar el calendario Era japonés imperial. El `SetCalID` método se realiza correctamente sólo si dicho calendario está instalado en el equipo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1 Nº&4;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]  
  
##  <a name="a-namesetcenturyviewa--cmonthcalctrlsetcenturyview"></a><a name="setcenturyview"></a>CMonthCalCtrl::SetCenturyView  
 Establece el control de calendario del mes actual para mostrar la vista de siglo.  
  
```  
BOOL SetCenturyView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista `MCMV_CENTURY`, que representa la vista de siglo.  
  
##  <a name="a-namesetcolora--cmonthcalctrlsetcolor"></a><a name="setcolor"></a>CMonthCalCtrl::SetColor  
 Establece el color de un área especificada de un control de calendario mensual.  
  
```  
COLORREF SetColor(
    int nRegion,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Parámetros  
 `nRegion`  
 Valor entero que especifica el color de calendario del mes para establecer. Este valor puede ser uno de los siguientes.  
  
|Valor|Significado|  
|-----------|-------------|  
|MCSC_BACKGROUND|El color de fondo que se muestran entre los meses.|  
|MCSC_MONTHBK|Color de fondo que se muestra dentro del mes.|  
|MCSC_TEXT|Color utilizado para mostrar texto en un mes.|  
|MCSC_TITLEBK|Color de fondo que se muestra en el título del calendario.|  
|MCSC_TITLETEXT|Color utilizado para mostrar texto en el título del calendario.|  
|MCSC_TRAILINGTEXT|El color utilizado para mostrar texto de encabezado y al final de día. Encabezado y los días finales son los días de los meses anteriores y siguientes que aparecen en el calendario actual.|  
  
 `ref`  
 Un **COLORREF** valor para el nuevo valor de color de la parte especificada del control de calendario mensual.  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que representa la configuración de color anteriores de la parte especificada del control de calendario mensual, si se realiza correctamente. De lo contrario, este mensaje devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760997), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl Nº&4;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]  
  
##  <a name="a-namesetcurrentviewa--cmonthcalctrlsetcurrentview"></a><a name="setcurrentview"></a>CMonthCalCtrl::SetCurrentView  
 Establece el control de calendario del mes actual para mostrar la vista especificada.  
  
```  
BOOL SetCurrentView(DWORD dwNewView);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `dwNewView`|Uno de los siguientes valores que especifican un mensual, anual, década o vista de siglo.<br /><br /> MCMV_MONTH: Vista mensual<br /><br /> MCMV_YEAR: Vista anual<br /><br /> MCMV_DECADE: Vista de la década<br /><br /> MCMV_CENTURY: Vista de siglo|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_SETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760998) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetcursela--cmonthcalctrlsetcursel"></a><a name="setcursel"></a>CMonthCalCtrl::SetCurSel  
 Establece la fecha seleccionada actualmente para un control de calendario mensual.  
  
```  
BOOL SetCurSel(const COleDateTime& refDateTime);  
BOOL SetCurSel(const CTime& refDateTime);  
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Parámetros  
 `refDateTime`  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que indica el control de calendario mensual seleccionada actualmente.  
  
 `pDateTime`  
 Puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en que se establecerá como la selección actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb761002), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de `SetCurSel`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl&#5;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]  
  
##  <a name="a-namesetdaystatea--cmonthcalctrlsetdaystate"></a><a name="setdaystate"></a>CMonthCalCtrl:: SetDayState  
 Establece la presentación de días en un control de calendario mensual.  
  
```  
BOOL SetDayState(
    int nMonths,  
    LPMONTHDAYSTATE pStates);
```  
  
### <a name="parameters"></a>Parámetros  
 *nMonths*  
 Valor que indica el número de elementos de la matriz que `pStates` señala.  
  
 `pStates`  
 Un puntero a un [MONTHDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760915) matriz de valores que definen cómo el control de calendario mensual dibujará cada día en su presentación. El **MONTHDAYSTATE** tipo de datos es un campo de bits, donde cada bit (1 a 31) representa el estado de un día en un mes. Si un bit está activado, el día correspondiente aparecerá en negrita; de lo contrario, se mostrará con ningún énfasis.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761004), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl Nº&6;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]  
  
##  <a name="a-namesetdecadeviewa--cmonthcalctrlsetdecadeview"></a><a name="setdecadeview"></a>CMonthCalCtrl::SetDecadeView  
 Establece el calendario del mes actual control a la vista de la década.  
  
```  
BOOL SetDecadeView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista `MCMV_DECADE`, que representa la vista de la década.  
  
##  <a name="a-namesetfirstdayofweeka--cmonthcalctrlsetfirstdayofweek"></a><a name="setfirstdayofweek"></a>CMonthCalCtrl::SetFirstDayOfWeek  
 Establece el día de la semana que se mostrará en la columna más a la izquierda del calendario.  
  
```  
BOOL SetFirstDayOfWeek(
    int iDay,  
    int* lpnOld = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *iDay*  
 Valor entero que representa el día que se va a establecer como el primer día de la semana. Este valor debe ser uno de los números de día. Consulte [GetFirstDayOfWeek](#getfirstdayofweek) para obtener una descripción de los números de día.  
  
 *lpnOld*  
 Establece un puntero a un entero que indica el primer día de la semana anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el primer día de la semana anterior se establece en un valor distinto de **LOCALE_IFIRSTDAYOFWEEK**, que es el día indicado en la configuración del panel de control. De lo contrario, esta función devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb761006), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl&#7;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]  
  
##  <a name="a-namesetmaxselcounta--cmonthcalctrlsetmaxselcount"></a><a name="setmaxselcount"></a>CMonthCalCtrl::SetMaxSelCount  
 Establece el número máximo de días que se pueden seleccionar en un control de calendario mensual.  
  
```  
BOOL SetMaxSelCount(int nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 `nMax`  
 El valor que se establecerá para representar el número máximo de días seleccionables.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761008), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl Nº&8;](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]  
  
##  <a name="a-namesetmonthdeltaa--cmonthcalctrlsetmonthdelta"></a><a name="setmonthdelta"></a>CMonthCalCtrl::SetMonthDelta  
 Establece la tasa de desplazamiento para un control de calendario mensual.  
  
```  
int SetMonthDelta(int iDelta);
```  
  
### <a name="parameters"></a>Parámetros  
 *iDelta*  
 El número de meses que se establecerá como la tasa de desplazamiento del control. Si este valor es cero, el incremento mensual se restablece al valor predeterminado, que es el número de meses que se muestra en el control.  
  
### <a name="return-value"></a>Valor devuelto  
 La tasa de desplazamiento anterior. Si la tasa de desplazamiento no se ha establecido previamente, el valor devuelto es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb761010), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namesetmonthviewa--cmonthcalctrlsetmonthview"></a><a name="setmonthview"></a>CMonthCalCtrl::SetMonthView  
 Establece el control de calendario del mes actual para mostrar la vista del mes.  
  
```  
BOOL SetMonthView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista `MCMV_MONTH`, que representa la vista del mes.  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_monthCalCtrl`, que se utiliza para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el control de calendario mensual para mostrar el mes, año, diez años y vistas de siglo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s&#1;2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]  
  
##  <a name="a-namesetrangea--cmonthcalctrlsetrange"></a><a name="setrange"></a>CMonthCalCtrl::SetRange  
 Establece las fechas permitidas mínimas y máxima para un control de calendario mensual.  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);

 
BOOL SetRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMinRange`  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 `pMaxRange`  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761012), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de `SetRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl::GetRange](#getrange).  
  
##  <a name="a-namesetselrangea--cmonthcalctrlsetselrange"></a><a name="setselrange"></a>CMonthCalCtrl::SetSelRange  
 Establece la selección de un calendario de mes control con un intervalo de fechas determinado.  
  
```  
BOOL SetSelRange(
    const COleDateTime& pMinRange,  
    const COleDateTime& pMaxRange);

 
BOOL SetSelRange(
    const CTime& pMinRange,  
    const CTime& pMaxRange);

 
BOOL SetSelRange(
    const LPSYSTEMTIME pMinRange,  
    const LPSYSTEMTIME pMaxRange);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMinRange`  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 `pMaxRange`  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761014), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de `SetSelRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura de uso.  
  
##  <a name="a-namesettodaya--cmonthcalctrlsettoday"></a><a name="settoday"></a>CMonthCalCtrl::SetToday  
 Establece el control de calendario para el día actual.  
  
```  
void SetToday(const COleDateTime& refDateTime);  
void SetToday(const CTime* pDateTime);  
  void SetToday(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Parámetros  
 `refDateTime`  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha actual.  
  
 `pDateTime`  
 En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la información de la fecha actual. En la tercera versión, un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la información de la fecha actual.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb761016), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl::GetToday](#gettoday).  
  
##  <a name="a-namesetyearviewa--cmonthcalctrlsetyearview"></a><a name="setyearview"></a>CMonthCalCtrl::SetYearView  
 Establece el calendario del mes actual control a la vista de año.  
  
```  
BOOL SetYearView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista `MCMV_YEAR`, que representa la vista anual.  
  
##  <a name="a-namesizeminreqa--cmonthcalctrlsizeminreq"></a><a name="sizeminreq"></a>CMonthCalCtrl::SizeMinReq  
 Muestra el mes en el control de calendario en el mínimo tamaño que muestra un mes.  
  
```  
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRepaint`  
 Especifica si el control es necesario volver a dibujar. De forma predeterminada, **TRUE**. Si **FALSE**, ninguna actualización de la pantalla se produce.  
  
### <a name="return-value"></a>Valor devuelto  
 Es distinto de cero si el control de calendario mensual es el tamaño mínimo; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a `SizeMinReq` muestra correctamente el control de calendario de mes completo para el calendario de un mes.  
  
##  <a name="a-namesizerecttomina--cmonthcalctrlsizerecttomin"></a><a name="sizerecttomin"></a>CMonthCalCtrl::SizeRectToMin  
 Para el control de calendario del mes actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo determinado.  
  
```  
LPRECT SizeRectToMin(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `lpRect`|Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que define un rectángulo que contiene el número deseado de calendarios.|  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que define un rectángulo cuyo tamaño es menor o igual que el rectángulo definido por el `lpRect` parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula cuántos calendarios cabe en el rectángulo especificado por el `lpRect` parámetro y, a continuación, devuelve el rectángulo más pequeño que puede contener el número de calendarios. En efecto, este método reduce el rectángulo especificado para ajustarse exactamente el número deseado de calendarios.  
  
 Este método envía el [MCM_SIZERECTTOMIN](http://msdn.microsoft.com/library/windows/desktop/bb761020) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL1 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl (clase)](../../mfc/reference/cdatetimectrl-class.md)

