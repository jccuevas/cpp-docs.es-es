---
title: CMonthCalCtrl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::CMonthCalCtrl
- AFXDTCTL/CMonthCalCtrl::Create
- AFXDTCTL/CMonthCalCtrl::GetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::GetCalendarCount
- AFXDTCTL/CMonthCalCtrl::GetCalendarGridInfo
- AFXDTCTL/CMonthCalCtrl::GetCalID
- AFXDTCTL/CMonthCalCtrl::GetColor
- AFXDTCTL/CMonthCalCtrl::GetCurrentView
- AFXDTCTL/CMonthCalCtrl::GetCurSel
- AFXDTCTL/CMonthCalCtrl::GetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::GetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::GetMaxTodayWidth
- AFXDTCTL/CMonthCalCtrl::GetMinReqRect
- AFXDTCTL/CMonthCalCtrl::GetMonthDelta
- AFXDTCTL/CMonthCalCtrl::GetMonthRange
- AFXDTCTL/CMonthCalCtrl::GetRange
- AFXDTCTL/CMonthCalCtrl::GetSelRange
- AFXDTCTL/CMonthCalCtrl::GetToday
- AFXDTCTL/CMonthCalCtrl::HitTest
- AFXDTCTL/CMonthCalCtrl::IsCenturyView
- AFXDTCTL/CMonthCalCtrl::IsDecadeView
- AFXDTCTL/CMonthCalCtrl::IsMonthView
- AFXDTCTL/CMonthCalCtrl::IsYearView
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorder
- AFXDTCTL/CMonthCalCtrl::SetCalendarBorderDefault
- AFXDTCTL/CMonthCalCtrl::SetCalID
- AFXDTCTL/CMonthCalCtrl::SetCenturyView
- AFXDTCTL/CMonthCalCtrl::SetColor
- AFXDTCTL/CMonthCalCtrl::SetCurrentView
- AFXDTCTL/CMonthCalCtrl::SetCurSel
- AFXDTCTL/CMonthCalCtrl::SetDayState
- AFXDTCTL/CMonthCalCtrl::SetDecadeView
- AFXDTCTL/CMonthCalCtrl::SetFirstDayOfWeek
- AFXDTCTL/CMonthCalCtrl::SetMaxSelCount
- AFXDTCTL/CMonthCalCtrl::SetMonthDelta
- AFXDTCTL/CMonthCalCtrl::SetMonthView
- AFXDTCTL/CMonthCalCtrl::SetRange
- AFXDTCTL/CMonthCalCtrl::SetSelRange
- AFXDTCTL/CMonthCalCtrl::SetToday
- AFXDTCTL/CMonthCalCtrl::SetYearView
- AFXDTCTL/CMonthCalCtrl::SizeMinReq
- AFXDTCTL/CMonthCalCtrl::SizeRectToMin
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl [MFC], CMonthCalCtrl
- CMonthCalCtrl [MFC], Create
- CMonthCalCtrl [MFC], GetCalendarBorder
- CMonthCalCtrl [MFC], GetCalendarCount
- CMonthCalCtrl [MFC], GetCalendarGridInfo
- CMonthCalCtrl [MFC], GetCalID
- CMonthCalCtrl [MFC], GetColor
- CMonthCalCtrl [MFC], GetCurrentView
- CMonthCalCtrl [MFC], GetCurSel
- CMonthCalCtrl [MFC], GetFirstDayOfWeek
- CMonthCalCtrl [MFC], GetMaxSelCount
- CMonthCalCtrl [MFC], GetMaxTodayWidth
- CMonthCalCtrl [MFC], GetMinReqRect
- CMonthCalCtrl [MFC], GetMonthDelta
- CMonthCalCtrl [MFC], GetMonthRange
- CMonthCalCtrl [MFC], GetRange
- CMonthCalCtrl [MFC], GetSelRange
- CMonthCalCtrl [MFC], GetToday
- CMonthCalCtrl [MFC], HitTest
- CMonthCalCtrl [MFC], IsCenturyView
- CMonthCalCtrl [MFC], IsDecadeView
- CMonthCalCtrl [MFC], IsMonthView
- CMonthCalCtrl [MFC], IsYearView
- CMonthCalCtrl [MFC], SetCalendarBorder
- CMonthCalCtrl [MFC], SetCalendarBorderDefault
- CMonthCalCtrl [MFC], SetCalID
- CMonthCalCtrl [MFC], SetCenturyView
- CMonthCalCtrl [MFC], SetColor
- CMonthCalCtrl [MFC], SetCurrentView
- CMonthCalCtrl [MFC], SetCurSel
- CMonthCalCtrl [MFC], SetDayState
- CMonthCalCtrl [MFC], SetDecadeView
- CMonthCalCtrl [MFC], SetFirstDayOfWeek
- CMonthCalCtrl [MFC], SetMaxSelCount
- CMonthCalCtrl [MFC], SetMonthDelta
- CMonthCalCtrl [MFC], SetMonthView
- CMonthCalCtrl [MFC], SetRange
- CMonthCalCtrl [MFC], SetSelRange
- CMonthCalCtrl [MFC], SetToday
- CMonthCalCtrl [MFC], SetYearView
- CMonthCalCtrl [MFC], SizeMinReq
- CMonthCalCtrl [MFC], SizeRectToMin
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd7160f2998eee18439baa67a93a73fcd73b5c0f
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853555"
---
# <a name="cmonthcalctrl-class"></a>CMonthCalCtrl (clase)
Encapsula la funcionalidad de un control de calendario mensual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonthCalCtrl::CMonthCalCtrl](#cmonthcalctrl)|Construye un objeto `CMonthCalCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonthCalCtrl::Create](#create)|Crea un control de calendario mensual y lo adjunta a la `CMonthCalCtrl` objeto.|  
|[CMonthCalCtrl::GetCalendarBorder](#getcalendarborder)|Recupera el ancho del borde del control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCalendarCount](#getcalendarcount)|Recupera el número de calendarios que se muestran en el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCalendarGridInfo](#getcalendargridinfo)|Recupera información sobre el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCalID](#getcalid)|Recupera el identificador de calendario para el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetColor](#getcolor)|Obtiene el color de un área especificada de un control de calendario mensual.|  
|[CMonthCalCtrl::GetCurrentView](#getcurrentview)|Recupera la vista que se muestra actualmente por el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetCurSel](#getcursel)|Recupera la hora del sistema, tal y como indica la fecha seleccionada actualmente.|  
|[CMonthCalCtrl::GetFirstDayOfWeek](#getfirstdayofweek)|Obtiene el primer día de la semana que se mostrará en la columna más a la izquierda del calendario.|  
|[CMonthCalCtrl::GetMaxSelCount](#getmaxselcount)|Recupera el número máximo actual de días que se pueden seleccionar en un control de calendario mensual.|  
|[CMonthCalCtrl::GetMaxTodayWidth](#getmaxtodaywidth)|Recupera el ancho máximo de la cadena "Today" para el control de calendario del mes actual.|  
|[CMonthCalCtrl::GetMinReqRect](#getminreqrect)|Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario mensual.|  
|[CMonthCalCtrl::GetMonthDelta](#getmonthdelta)|Recupera la tasa de desplazamiento para un control de calendario mensual.|  
|[CMonthCalCtrl::GetMonthRange](#getmonthrange)|Fecha en que recupera la información que representa los límites máximo y mínimo de presentación de un control de calendario mensual.|  
|[CMonthCalCtrl::GetRange](#getrange)|Recupera las fechas mínimas y máxima actuales establecidas en un control de calendario mensual.|  
|[CMonthCalCtrl::GetSelRange](#getselrange)|Recupera información de fecha que representa los límites superiores e inferiores del intervalo de fechas seleccionado actualmente por el usuario.|  
|[CMonthCalCtrl::GetToday](#gettoday)|Recupera la información de fecha para la fecha especificada como 'hoy' para un control de calendario mensual.|  
|[CMonthCalCtrl::HitTest](#hittest)|Determina qué sección de un control de calendario mensual es en un momento dado en la pantalla.|  
|[CMonthCalCtrl::IsCenturyView](#iscenturyview)|Indica si la vista actual del control de calendario mensual actual es la vista de siglo.|  
|[CMonthCalCtrl::IsDecadeView](#isdecadeview)|Indica si la vista actual del control de calendario mensual actual es la vista de la década.|  
|[CMonthCalCtrl::IsMonthView](#ismonthview)|Indica si la vista actual del control de calendario mensual actual es la vista mensual.|  
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
|[CMonthCalCtrl::SetSelRange](#setselrange)|Establece la selección de un calendario mensual control a un intervalo de fechas determinado.|  
|[CMonthCalCtrl::SetToday](#settoday)|Establece el control de calendario para el día actual.|  
|[CMonthCalCtrl::SetYearView](#setyearview)|Establece el calendario del mes actual control a la vista de año.|  
|[CMonthCalCtrl::SizeMinReq](#sizeminreq)|Vuelve a dibujar el calendario mensual control a su tamaño mínimo, un mes.|  
|[CMonthCalCtrl::SizeRectToMin](#sizerecttomin)|Para el control de calendario del mes actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo especificado.|  
  
## <a name="remarks"></a>Comentarios  
 El control de calendario mensual proporciona al usuario con una interfaz de calendario simple, desde el que el usuario puede seleccionar una fecha. El usuario puede cambiar la visualización por:  
  
-   Desplazarse hacia atrás y hacia delante, de mes a mes.  
  
-   Al hacer clic en el texto de hoy en día para mostrar el día actual (si no se usa el estilo MCS_NOTODAY).  
  
-   Seleccionar un mes o un año a partir de un menú emergente.  
  
 Puede personalizar el mes de control de calendario aplicando una variedad de estilos para el objeto al crearlo. Estos estilos se describen en [estilos de Control de calendario de mes](http://msdn.microsoft.com/library/windows/desktop/bb760919) en el SDK de Windows.  
  
 El control de calendario mensual puede mostrar más de un mes, y puede indicar los días especiales (por ejemplo, los días festivos) por poner en negrita la fecha.  
  
 Para obtener más información acerca de cómo utilizar el control de calendario mensual, consulte [usar CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdtctl.h  
  
##  <a name="cmonthcalctrl"></a>  CMonthCalCtrl::CMonthCalCtrl  
 Construye un objeto `CMonthCalCtrl`.  
  
```  
CMonthCalCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a `Create` después de crear el objeto.  
  
##  <a name="create"></a>  CMonthCalCtrl::Create  
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
 *dwStyle*  
 Especifica la combinación de los estilos de Windows aplicados al control de calendario mensual. Consulte [estilos de Control de calendario de mes](http://msdn.microsoft.com/library/windows/desktop/bb760919) en el SDK de Windows para obtener más información acerca de los estilos.  
  
 *Rect*  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura. Contiene la posición y el tamaño del control de calendario mensual.  
  
 *PT*  
 Una referencia a un [punto](http://msdn.microsoft.com/library/windows/desktop/dd162805) estructura que identifica la ubicación del control de calendario mensual.  
  
 *pParentWnd*  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto que es la ventana primaria del control de calendario mensual. No debe ser NULL.  
  
 *nID*  
 Especifica el identificador de control. del control de calendario mensual  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la inicialización se realizó correctamente; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Creación de un mes de calendario control en dos pasos:  
  
1.  Llame a [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) para construir un `CMonthCalCtrl` objeto.  
  
2.  Llame a esta función miembro, que crea un control de calendario mensual y lo adjunta a la `CMonthCalCtrl` objeto.  
  
 Cuando se llama a `Create`, se inicializan los controles comunes. La versión de `Create` , llamada determina cómo tiene un tamaño:  
  
-   Para que MFC automáticamente el tamaño del control a un mes, llamará a la invalidación que usa el *pt* parámetro.  
  
-   Para el tamaño del control, llame a la invalidación de esta función que usa el *rect* parámetro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_1.cpp)]  
  
##  <a name="getcalendarborder"></a>  CMonthCalCtrl::GetCalendarBorder  
 Recupera el ancho del borde del control de calendario del mes actual.  
  
```  
int GetCalendarBorder() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho del borde del control, en píxeles.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760945) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getcalendarcount"></a>  CMonthCalCtrl::GetCalendarCount  
 Recupera el número de calendarios que se muestran en el control de calendario del mes actual.  
  
```  
int GetCalendarCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de calendarios que se muestra actualmente en el control de calendario mensual. El número máximo permitido de calendarios es 12.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCALENDARCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760947) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getcalendargridinfo"></a>  CMonthCalCtrl::GetCalendarGridInfo  
 Recupera información sobre el control de calendario del mes actual.  
  
```  
BOOL GetCalendarGridInfo(PMCGRIDINFO pmcGridInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] *pmcGridInfo*|Puntero a un [MCGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760925) estructura que recibe información sobre el control de calendario del mes actual. El llamador es responsable de la asignación e inicialización de esta estructura.|  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCALENDARGRIDINFO](http://msdn.microsoft.com/library/windows/desktop/bb760949) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente define la variable, `m_monthCalCtrl`, que se usa para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código utiliza el `GetCalendarGridInfo` método para recuperar la fecha del calendario que muestra el control de calendario del mes actual.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_3.cpp)]  
  
##  <a name="getcalid"></a>  CMonthCalCtrl::GetCalID  
 Recupera el identificador de calendario para el control de calendario del mes actual.  
  
```  
CALID GetCalID() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los [identificador calendario](http://msdn.microsoft.com/library/windows/desktop/dd317732) constantes.  
  
### <a name="remarks"></a>Comentarios  
 Un identificador de calendario denota un calendario específico de la región, como el gregoriano (localizado), japonés o Hijri calendarios. La aplicación puede usar un identificador de calendario que tiene diversos de lenguaje admite las funciones.  
  
 Este método envía el [MCM_GETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760951) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getcolor"></a>  CMonthCalCtrl::GetColor  
 Recupera el color de un área del mes especificado por el control de calendario *nRegion*.  
  
```  
COLORREF GetColor(int nRegion) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *nRegion*  
 La región del control de calendario mensual del que se recupera el color. Para obtener una lista de valores, vea el *nRegion* parámetro de [SetColor](#setcolor).  
  
### <a name="return-value"></a>Valor devuelto  
 Un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que especifica el color asociado a la parte del control de calendario mensual, si se realiza correctamente. En caso contrario, esta función miembro devuelve -1.  
  
##  <a name="getcurrentview"></a>  CMonthCalCtrl::GetCurrentView  
 Recupera la vista que se muestra actualmente por el control de calendario del mes actual.  
  
```  
DWORD GetCurrentView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La vista actual, que se indica mediante uno de los valores siguientes:  
  
|Valor|Significado|  
|-----------|-------------|  
|MCMV_MONTH|Vista mensual|  
|MCMV_YEAR|Vista anual|  
|MCMV_DECADE|Vista de la década|  
|MCMV_CENTURY|Vista de siglo|  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente define la variable, `m_monthCalCtrl`, que se usa para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 Los siguientes informes de ejemplo de código que permite ver el calendario mensual controlan muestra actualmente.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_4.cpp)]  
  
##  <a name="getcursel"></a>  CMonthCalCtrl::GetCurSel  
 Recupera la hora del sistema, tal y como indica la fecha seleccionada actualmente.  
  
```  
BOOL GetCurSel(COleDateTime& refDateTime) const;  BOOL GetCurSel(CTime& refDateTime) const;  
   
BOOL GetCurSel(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *refDateTime*  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto. Recibe la hora actual.  
  
 *pDateTime*  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que recibirá la información de fecha seleccionada actualmente. Este parámetro debe ser una dirección válida y no puede ser NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se realiza correctamente; otherwize 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb760957), tal y como se describe en el SDK de Windows.  
  
> [!NOTE]
>  Esta función miembro produce un error si se establece el estilo MCS_MULTISELECT.  
  
 En la implementación de MFC de `GetCurSel`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
##  <a name="getfirstdayofweek"></a>  CMonthCalCtrl::GetFirstDayOfWeek  
 Obtiene el primer día de la semana que se mostrará en la columna más a la izquierda del calendario.  
  
```  
int GetFirstDayOfWeek(BOOL* pbLocal = NULL) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pbLocal*  
 Un puntero a un valor booleano. Si el valor es distinto de cero, el valor del control no coincide con la configuración en el panel de control.  
  
### <a name="return-value"></a>Valor devuelto  
 Valor entero que representa el primer día de la semana. Consulte **comentarios** para obtener más información sobre estos enteros que representan.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb760958), tal y como se describe en el SDK de Windows. Los días de la semana se representan como números enteros, como se indica a continuación.  
  
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
  
##  <a name="getmaxselcount"></a>  CMonthCalCtrl::GetMaxSelCount  
 Recupera el número máximo actual de días que se pueden seleccionar en un control de calendario mensual.  
  
```  
int GetMaxSelCount() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor entero que representa el número total de días que se pueden seleccionar para el control.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb760960), tal y como se describe en el SDK de Windows. Utilice esta función miembro para controles con el conjunto de estilos MCS_MULTISELECT.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl::SetMaxSelCount](#setmaxselcount).  
  
##  <a name="getmaxtodaywidth"></a>  CMonthCalCtrl::GetMaxTodayWidth  
 Recupera el ancho máximo de la cadena "Today" para el control de calendario del mes actual.  
  
```  
DWORD GetMaxTodayWidth() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El ancho de la cadena "Today", en píxeles.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente define la variable, `m_monthCalCtrl`, que se usa para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se muestra el `GetMaxTodayWidth` método.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_5.cpp)]  
  
### <a name="remarks"></a>Comentarios  
 El usuario puede volver a la fecha actual, haga clic en la cadena "Today", que se muestra en la parte inferior del control de calendario mensual. La cadena "Today" incluye el texto de etiqueta y fecha.  
  
 Este método envía el [MCM_GETMAXTODAYWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb760962) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getminreqrect"></a>  CMonthCalCtrl::GetMinReqRect  
 Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario mensual.  
  
```  
BOOL GetMinReqRect(RECT* pRect) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *pRect*  
 Un puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que recibirá la información de rectángulo delimitador. Este parámetro debe ser una dirección válida y no puede ser NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcto, esta función miembro devuelve distinto de cero y `lpRect` recibe la información aplicable de delimitador. Si no lo consigue, la función miembro devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMINREQRECT](http://msdn.microsoft.com/library/windows/desktop/bb760978), tal y como se describe en el SDK de Windows.  
  
##  <a name="getmonthdelta"></a>  CMonthCalCtrl::GetMonthDelta  
 Recupera la tasa de desplazamiento para un control de calendario mensual.  
  
```  
int GetMonthDelta() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La tasa de desplazamiento para el control de calendario mensual. La tasa de desplazamiento es el número de meses que el control mueve su presentación cuando el usuario hace clic en un botón de desplazamiento de una vez.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb760980), tal y como se describe en el SDK de Windows.  
  
##  <a name="getmonthrange"></a>  CMonthCalCtrl::GetMonthRange  
 Fecha en que recupera la información que representa los límites máximo y mínimo de presentación de un control de calendario mensual.  
  
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
 *refMinRange*  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la fecha mínima permitida.  
  
 *refMaxRange*  
 Una referencia a un `COleDateTime` o `CTime` objeto que contiene la fecha máxima permitida.  
  
 *pMinRange*  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 *pMaxRange*  
 Un puntero a un `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
 *dwFlags*  
 Valor que especifica el ámbito de los límites del intervalo que se va a recuperar. Este valor debe ser uno de los siguientes.  
  
|Valor|Significado|  
|-----------|-------------|  
|GMR_DAYSTATE|Incluir iniciales y finales de meses del intervalo visible que se muestran solo parcialmente.|  
|GMR_VISIBLE|Incluir solo los meses que se muestran por completo.|  
  
### <a name="return-value"></a>Valor devuelto  
 Indica un entero que representa el intervalo, en meses, abarca los dos límites *refMinRange* y *refMaxRange* en las versiones de primeros y segunda, o *pMinRange* y *pMaxRange* en la tercera versión.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETMONTHRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760981), tal y como se describe en el SDK de Windows. En la implementación de MFC de `GetMonthRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl:: SetDayState](#setdaystate).  
  
##  <a name="getrange"></a>  CMonthCalCtrl::GetRange  
 Recupera las fechas mínimas y máxima actuales establecidas en un control de calendario mensual.  
  
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
 *pMinRange*  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 *pMaxRange*  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 DWORD que puede ser cero (límites no se establecen) o una combinación de los siguientes valores que especifican la información de límite.  
  
|Valor|Significado|  
|-----------|-------------|  
|GDTR_MAX|Se establece un límite máximo para el control; *pMaxRange* es válido y contiene la información de fecha aplicables.|  
|GDTR_MIN|Se establece un límite mínimo para el control; *pMinRange* es válido y contiene la información de fecha aplicables.|  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760983), tal y como se describe en el SDK de Windows. En la implementación de MFC de `GetRange`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_6.cpp)]  
  
##  <a name="getselrange"></a>  CMonthCalCtrl::GetSelRange  
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
 *refMinRange*  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la fecha mínima permitida.  
  
 *refMaxRange*  
 Una referencia a un `COleDateTime` o `CTime` objeto que contiene la fecha máxima permitida.  
  
 *pMinRange*  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 *pMaxRange*  
 Un puntero a un `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb760985), tal y como se describe en el SDK de Windows. `GetSelRange` se producirá un error si se aplica a un control de calendario mensual que no usa el estilo MCS_MULTISELECT.  
  
 En la implementación de MFC de `GetSelRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
##  <a name="gettoday"></a>  CMonthCalCtrl::GetToday  
 Recupera la información de fecha para la fecha especificada como 'hoy' para un control de calendario mensual.  
  
```  
BOOL GetToday(COleDateTime& refDateTime) const;  BOOL GetToday(COleDateTime& refDateTime) const;  
   
BOOL GetToday(LPSYSTEMTIME pDateTime) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *refDateTime*  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que indica el día actual.  
  
 *pDateTime*  
 Un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que recibirá la información de fecha. Este parámetro debe ser una dirección válida y no puede ser NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_GETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb760987), tal y como se describe en el SDK de Windows. En la implementación de MFC de `GetToday`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#3](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_7.cpp)]  
  
##  <a name="hittest"></a>  CMonthCalCtrl::HitTest  
 Determina qué control de calendario mensual, si existe, está en una posición especificada.  
  
```  
DWORD HitTest(PMCHITTESTINFO pMCHitTest);
```  
  
### <a name="parameters"></a>Parámetros  
 *pMCHitTest*  
 Un puntero a un [MCHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb760927) puntos de la estructura que contiene la prueba de posicionamiento para el control de calendario mensual.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor DWORD. Igual que el **uHit** miembro de la `MCHITTESTINFO` estructura.  
  
### <a name="remarks"></a>Comentarios  
 `HitTest` usa el `MCHITTESTINFO` estructura que contiene información acerca de la prueba de posicionamiento.  
  
##  <a name="iscenturyview"></a>  CMonthCalCtrl::IsCenturyView  
 Indica si la vista actual del control de calendario mensual actual es la vista de siglo.  
  
```  
BOOL IsCenturyView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la vista actual es el siglo; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el SDK de Windows. Si ese mensaje devuelve MCMV_CENTURY, este método devuelve TRUE.  
  
##  <a name="isdecadeview"></a>  CMonthCalCtrl::IsDecadeView  
 Indica si la vista actual del control de calendario mensual actual es la vista de la década.  
  
```  
BOOL IsDecadeView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la vista actual es la vista de la década; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el SDK de Windows. Si ese mensaje devuelve MCMV_DECADE, este método devuelve TRUE.  
  
##  <a name="ismonthview"></a>  CMonthCalCtrl::IsMonthView  
 Indica si la vista actual del control de calendario mensual actual es la vista mensual.  
  
```  
BOOL IsMonthView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la vista actual es el mes; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el SDK de Windows. Si ese mensaje devuelve MCMV_MONTH, este método devuelve TRUE.  
  
##  <a name="isyearview"></a>  CMonthCalCtrl::IsYearView  
 Indica si la vista actual del control de calendario mensual actual es la vista de año.  
  
```  
BOOL IsYearView() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si la vista actual es el año; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_GETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760955) mensaje, que se describe en el SDK de Windows. Si ese mensaje devuelve MCMV_YEAR, este método devuelve TRUE.  
  
##  <a name="setcalendarborder"></a>  CMonthCalCtrl::SetCalendarBorder  
 Establece el ancho del borde del control de calendario del mes actual.  
  
```  
void SetCalendarBorder(int cxyBorder);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *cxyBorder*|El ancho del borde, en píxeles.|  
  
### <a name="remarks"></a>Comentarios  
 Si este método se realiza correctamente, se establece el ancho del borde en el *cxyBorder* parámetro. En caso contrario, el ancho del borde se restablece al valor predeterminado especificado por el actual [tema](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), o cero si no se utilizan temas.  
  
 Este método envía el [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente define la variable, `m_monthCalCtrl`, que se usa para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 Ejemplo de código siguiente se establece el ancho del borde del calendario del mes controlar hasta ocho píxeles. Use la [CMonthCalCtrl::GetCalendarBorder](#getcalendarborder) método para determinar si este método se realizó correctamente.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_8.cpp)]  
  
##  <a name="setcalendarborderdefault"></a>  CMonthCalCtrl::SetCalendarBorderDefault  
 Establece el ancho predeterminado del borde del control de calendario del mes actual.  
  
```  
void SetCalendarBorderDefault();
```  
  
### <a name="remarks"></a>Comentarios  
 El ancho del borde se establece en el valor predeterminado especificado por el actual [tema](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx), o cero si no se utilizan temas.  
  
 Este método envía el [MCM_SETCALENDARBORDER](http://msdn.microsoft.com/library/windows/desktop/bb760993) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="setcalid"></a>  CMonthCalCtrl::SetCalID  
 Establece el identificador de calendario para el control de calendario del mes actual.  
  
```  
BOOL SetCalID(CALID calid);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *IDcalendario*|Uno de los [identificador calendario](http://msdn.microsoft.com/library/windows/desktop/dd317732) constantes.|  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Un identificador de calendario especifica un calendario específico de la región, como el gregoriano (localizado), japonés o Hijri calendarios. Use la `SetCalID` método para mostrar un calendario que se especifica mediante el *IDcalendario* parámetro si la configuración regional que contiene el calendario está instalada en el equipo.  
  
 Este método envía el [MCM_SETCALID](http://msdn.microsoft.com/library/windows/desktop/bb760995) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente define la variable, `m_monthCalCtrl`, que se usa para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente establece el control de calendario mensual para mostrar el calendario japonés Emperor Era. El `SetCalID` método tiene éxito únicamente si dicho calendario está instalado en el equipo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_9.cpp)]  
  
##  <a name="setcenturyview"></a>  CMonthCalCtrl::SetCenturyView  
 Establece el control de calendario del mes actual para mostrar la vista de siglo.  
  
```  
BOOL SetCenturyView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista `MCMV_CENTURY`, que representa la vista de siglo.  
  
##  <a name="setcolor"></a>  CMonthCalCtrl::SetColor  
 Establece el color de un área especificada de un control de calendario mensual.  
  
```  
COLORREF SetColor(
    int nRegion,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Parámetros  
 *nRegion*  
 Valor entero que especifica qué color de calendario del mes para establecer. Este valor puede ser uno de los siguientes.  
  
|Valor|Significado|  
|-----------|-------------|  
|MCSC_BACKGROUND|El color de fondo que se muestra entre meses.|  
|MCSC_MONTHBK|El color de fondo que se muestra dentro del mes.|  
|MCSC_TEXT|El color usado para mostrar texto en un mes.|  
|MCSC_TITLEBK|El color de fondo que se muestra en el título del calendario.|  
|MCSC_TITLETEXT|El color usado para mostrar texto en el título del calendario.|  
|MCSC_TRAILINGTEXT|El color usado para mostrar el texto de encabezado y el día al final. Encabezado y los días finales son los días de los meses anteriores y siguientes que aparecen en el calendario actual.|  
  
 *ref*  
 Un valor COLORREF para la nueva configuración de color de la parte especificada del control de calendario mensual.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor COLORREF que representa la configuración de color anterior de la parte especificada del control de calendario mensual, si se realiza correctamente. En caso contrario, este mensaje devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760997), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#4](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_10.cpp)]  
  
##  <a name="setcurrentview"></a>  CMonthCalCtrl::SetCurrentView  
 Establece el control de calendario del mes actual para mostrar la vista especificada.  
  
```  
BOOL SetCurrentView(DWORD dwNewView);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *dwNewView*|Uno de los siguientes valores que especifica un mensual, anual, década o vista de siglo.<br /><br /> MCMV_MONTH: Vista mensual<br /><br /> MCMV_YEAR: Vista anual<br /><br /> MCMV_DECADE: Vista de la década<br /><br /> MCMV_CENTURY: Vista de siglo|  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [MCM_SETCURRENTVIEW](http://msdn.microsoft.com/library/windows/desktop/bb760998) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="setcursel"></a>  CMonthCalCtrl::SetCurSel  
 Establece la fecha seleccionada actualmente para un control de calendario mensual.  
  
```  
BOOL SetCurSel(const COleDateTime& refDateTime);  
BOOL SetCurSel(const CTime& refDateTime);  
  BOOL SetCurSel(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Parámetros  
 *refDateTime*  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) o [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que indica el control de calendario del mes seleccionado actualmente.  
  
 *pDateTime*  
 Puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en que se establecerá como la selección actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETCURSEL](http://msdn.microsoft.com/library/windows/desktop/bb761002), tal y como se describe en el SDK de Windows. En la implementación de MFC de `SetCurSel`, puede especificar un `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#5](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_11.cpp)]  
  
##  <a name="setdaystate"></a>  CMonthCalCtrl:: SetDayState  
 Establece la presentación de días en un control de calendario mensual.  
  
```  
BOOL SetDayState(
    int nMonths,  
    LPMONTHDAYSTATE pStates);
```  
  
### <a name="parameters"></a>Parámetros  
 *nMonths*  
 Valor que indica cuántos elementos se encuentran en la matriz que *pStates* apunta a.  
  
 *pStates*  
 Un puntero a un [MONTHDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760915) matriz de valores que definen cómo el control de calendario mensual dibujará cada día en su presentación. El tipo de datos MONTHDAYSTATE es un campo de bits, donde cada bit (1 a 31) representa el estado de un día en un mes. Si un bit está activado, el día correspondiente aparecerá en negrita; en caso contrario, se mostrará con no hay ningún énfasis.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETDAYSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761004), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#6](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_12.cpp)]  
  
##  <a name="setdecadeview"></a>  CMonthCalCtrl::SetDecadeView  
 Establece el calendario del mes actual control a la vista de la década.  
  
```  
BOOL SetDecadeView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista `MCMV_DECADE`, que representa la vista de la década.  
  
##  <a name="setfirstdayofweek"></a>  CMonthCalCtrl::SetFirstDayOfWeek  
 Establece el día de la semana que se mostrará en la columna más a la izquierda del calendario.  
  
```  
BOOL SetFirstDayOfWeek(
    int iDay,  
    int* lpnOld = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *iDay*  
 Es un valor entero que representa el día que se establecerá como el primer día de la semana. Este valor debe ser uno de los números de día. Consulte [GetFirstDayOfWeek](#getfirstdayofweek) para obtener una descripción de los números de día.  
  
 *lpnOld*  
 Establece un puntero a un entero que indica el primer día de la semana anterior.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el primer día de la semana anterior se establece en un valor distinto de LOCALE_IFIRSTDAYOFWEEK, que es el día que se indica en la configuración del panel de control. En caso contrario, esta función devuelve 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETFIRSTDAYOFWEEK](http://msdn.microsoft.com/library/windows/desktop/bb761006), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#7](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_13.cpp)]  
  
##  <a name="setmaxselcount"></a>  CMonthCalCtrl::SetMaxSelCount  
 Establece el número máximo de días que se pueden seleccionar en un control de calendario mensual.  
  
```  
BOOL SetMaxSelCount(int nMax);
```  
  
### <a name="parameters"></a>Parámetros  
 *Nmáx.*  
 El valor que se establecerá para representar el número máximo de días seleccionables.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETMAXSELCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb761008), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CMonthCalCtrl#8](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_14.cpp)]  
  
##  <a name="setmonthdelta"></a>  CMonthCalCtrl::SetMonthDelta  
 Establece la tasa de desplazamiento para un control de calendario mensual.  
  
```  
int SetMonthDelta(int iDelta);
```  
  
### <a name="parameters"></a>Parámetros  
 *iDelta*  
 El número de meses que se establecerá como la tasa de desplazamiento del control. Si este valor es cero, se restablece el delta del mes en el valor predeterminado, que es el número de meses que se muestra en el control.  
  
### <a name="return-value"></a>Valor devuelto  
 La tasa de desplazamiento anterior. Si la tasa de desplazamiento no se ha establecido anteriormente, el valor devuelto es 0.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETMONTHDELTA](http://msdn.microsoft.com/library/windows/desktop/bb761010), tal y como se describe en el SDK de Windows.  
  
##  <a name="setmonthview"></a>  CMonthCalCtrl::SetMonthView  
 Establece el control de calendario del mes actual para mostrar la vista del mes.  
  
```  
BOOL SetMonthView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista MCMV_MONTH, que representa la vista mensual.  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente define la variable, `m_monthCalCtrl`, que se usa para obtener acceso mediante programación el control de calendario mensual. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_2.h)]  
  
### <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente establece el control de calendario mensual para mostrar el mes, año, década y vistas de siglo.  
  
 [!code-cpp[NVC_MFC_CMonthCalCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cmonthcalctrl-class_15.cpp)]  
  
##  <a name="setrange"></a>  CMonthCalCtrl::SetRange  
 Establece las fechas permitidas máxima y mínimas para un control de calendario mensual.  
  
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
 *pMinRange*  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 *pMaxRange*  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761012), tal y como se describe en el SDK de Windows. En la implementación de MFC de `SetRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl::GetRange](#getrange).  
  
##  <a name="setselrange"></a>  CMonthCalCtrl::SetSelRange  
 Establece la selección de un calendario mensual control a un intervalo de fechas determinado.  
  
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
 *pMinRange*  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la fecha en el extremo inferior del intervalo.  
  
 *pMaxRange*  
 Un puntero a un `COleDateTime` objeto, un `CTime` objeto, o `SYSTEMTIME` estructura que contiene la fecha en el extremo superior del intervalo.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETSELRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761014), tal y como se describe en el SDK de Windows. En la implementación de MFC de `SetSelRange`, puede especificar `COleDateTime` uso, un `CTime` uso, o un `SYSTEMTIME` estructura uso.  
  
##  <a name="settoday"></a>  CMonthCalCtrl::SetToday  
 Establece el control de calendario para el día actual.  
  
```  
void SetToday(const COleDateTime& refDateTime);  
void SetToday(const CTime* pDateTime);  
  void SetToday(const LPSYSTEMTIME pDateTime);
```  
  
### <a name="parameters"></a>Parámetros  
 *refDateTime*  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene la fecha actual.  
  
 *pDateTime*  
 En la segunda versión, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la información de la fecha actual. En la tercera versión, un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la información de la fecha actual.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [MCM_SETTODAY](http://msdn.microsoft.com/library/windows/desktop/bb761016), tal y como se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CMonthCalCtrl::GetToday](#gettoday).  
  
##  <a name="setyearview"></a>  CMonthCalCtrl::SetYearView  
 Establece el calendario del mes actual control a la vista de año.  
  
```  
BOOL SetYearView();
```  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si este método se realiza correctamente; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Este método usa la [CMonthCalCtrl::SetCurrentView](#setcurrentview) método para establecer la vista MCMV_YEAR, que representa la vista anual.  
  
##  <a name="sizeminreq"></a>  CMonthCalCtrl::SizeMinReq  
 Muestra el mes de control de calendario para el mínimo tamaño que muestra un mes.  
  
```  
BOOL SizeMinReq(BOOL bRepaint = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *bRepaint*  
 Especifica si el control es necesario volver a dibujar. De forma predeterminada, el valor TRUE. Si es FALSE, se produce una sin volver a dibujar.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si el control de calendario mensual tiene un tamaño mínimo; en caso contrario, es 0.  
  
### <a name="remarks"></a>Comentarios  
 Una llamada a `SizeMinReq` muestra correctamente el control de calendario del mes completo para el calendario de un mes.  
  
##  <a name="sizerecttomin"></a>  CMonthCalCtrl::SizeRectToMin  
 Para el control de calendario del mes actual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo especificado.  
  
```  
LPRECT SizeRectToMin(LPRECT lpRect);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] *lpRect*|Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que define un rectángulo que contiene el número deseado de calendarios.|  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que define un rectángulo cuyo tamaño es menor o igual que el rectángulo definido por el *lpRect* parámetro.  
  
### <a name="remarks"></a>Comentarios  
 Este método calcula cuántos calendarios pueden caber en el rectángulo especificado por el *lpRect* parámetro y, a continuación, devuelve el rectángulo más pequeño que puede contener ese número de calendarios. De hecho, este método reduce el rectángulo especificado para ajustarse exactamente el número deseado de calendarios.  
  
 Este método envía el [MCM_SIZERECTTOMIN](http://msdn.microsoft.com/library/windows/desktop/bb761020) mensaje, que se describe en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL1 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl (clase)](../../mfc/reference/cdatetimectrl-class.md)
