---
title: CDateTimeCtrl (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CDateTimeCtrl
- AFXDTCTL/CDateTimeCtrl::CloseMonthCal
- AFXDTCTL/CDateTimeCtrl::Create
- AFXDTCTL/CDateTimeCtrl::GetDateTimePickerInfo
- AFXDTCTL/CDateTimeCtrl::GetIdealSize
- AFXDTCTL/CDateTimeCtrl::GetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::GetMonthCalCtrl
- AFXDTCTL/CDateTimeCtrl::GetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::GetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::GetRange
- AFXDTCTL/CDateTimeCtrl::GetTime
- AFXDTCTL/CDateTimeCtrl::SetFormat
- AFXDTCTL/CDateTimeCtrl::SetMonthCalColor
- AFXDTCTL/CDateTimeCtrl::SetMonthCalFont
- AFXDTCTL/CDateTimeCtrl::SetMonthCalStyle
- AFXDTCTL/CDateTimeCtrl::SetRange
- AFXDTCTL/CDateTimeCtrl::SetTime
dev_langs:
- C++
helpviewer_keywords:
- DateTimePicker control [MFC], CDateTimeCtrl class
- date-picking functionality
- CDateTimeCtrl class
- DateTimePicker control [MFC]
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
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
ms.openlocfilehash: e5407934021abdb64dfb625e3dfb2c1841b7a5f0
ms.lasthandoff: 02/24/2017

---
# <a name="cdatetimectrl-class"></a>CDateTimeCtrl (clase)
Encapsula la funcionalidad de un control selector de fecha y hora.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDateTimeCtrl::CDateTimeCtrl](#cdatetimectrl)|Construye un objeto `CDateTimeCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDateTimeCtrl::CloseMonthCal](#closemonthcal)|Cierra el control de selector de fecha y hora actual.|  
|[CDateTimeCtrl::Create](#create)|Crea el control de selector de fecha y hora y lo adjunta a la `CDateTimeCtrl` objeto.|  
|[CDateTimeCtrl::GetDateTimePickerInfo](#getdatetimepickerinfo)|Recupera información sobre el control de selector de fecha y hora actual.|  
|[CDateTimeCtrl::GetIdealSize](#getidealsize)|Devuelve el tamaño ideal de control de selector de fecha y hora en que se requiere para mostrar la fecha u hora actuales.|  
|[CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor)|Recupera el color de una parte determinada del calendario de mes en el control de selector de fecha y hora.|  
|[CDateTimeCtrl:: GetMonthCalCtrl](#getmonthcalctrl)|Recupera el `CMonthCalCtrl` objeto asociado con el control de selector de fecha y hora.|  
|[CDateTimeCtrl::GetMonthCalFont](#getmonthcalfont)|Recupera la fuente usada actualmente por la fecha y el control de calendario mensual del control de selector de hora secundarios.|  
|[CDateTimeCtrl::GetMonthCalStyle](#getmonthcalstyle)|Obtiene el estilo del control de selector de fecha y hora actual.|  
|[CDateTimeCtrl::GetRange](#getrange)|Recupera actual mínimo y máximo permitido de horas del sistema para un control de selector de fecha y hora.|  
|[CDateTimeCtrl::GetTime](#gettime)|Recupera el tiempo seleccionado de un control de selector de fecha y hora y lo coloca en un especificado `SYSTEMTIME` estructura.|  
|[CDateTimeCtrl:: SetFormat](#setformat)|Establece la presentación de un control de selector de fecha y hora con arreglo a una cadena de formato especificado.|  
|[CDateTimeCtrl::SetMonthCalColor](#setmonthcalcolor)|Establece el color de una parte determinada del calendario de mes dentro de un control de selector de fecha y hora.|  
|[CDateTimeCtrl:: SetMonthCalFont](#setmonthcalfont)|Establece la fuente que utilizará el control de calendario mensual de fecha y hora selector del control secundario.|  
|[CDateTimeCtrl::SetMonthCalStyle](#setmonthcalstyle)|Establece el estilo del control de selector de fecha y hora actual.|  
|[CDateTimeCtrl::SetRange](#setrange)|Establece las horas de máximo y mínimo sistema permitido para un control de selector de fecha y hora.|  
|[CDateTimeCtrl::SetTime](#settime)|Establece el tiempo en un control de selector de fecha y hora.|  
  
## <a name="remarks"></a>Comentarios  
 El control de selector de fecha y hora (control DTP) proporciona una interfaz sencilla para intercambiar información de fecha y hora con un usuario. Esta interfaz contiene campos, cada uno de ellos muestra una parte de la información de fecha y hora almacenada en el control. El usuario puede cambiar la información almacenada en el control cambiando el contenido de la cadena en un campo determinado. El usuario puede mover el campo con el mouse o el teclado.  
  
 Puede personalizar el control de selector de fecha y hora aplicando una variedad de estilos para el objeto al crearlo. Consulte [estilos de fecha y hora selector Control](http://msdn.microsoft.com/library/windows/desktop/bb761728) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre los estilos específicos para el control de selector de fecha y hora. Puede establecer el formato de presentación del control DTP mediante estilos de formato. Estos estilos de formato se describen en "Estilos de formato" en la [!INCLUDE[winsdkshort](../../atl-mfc-shared/reference/includes/winsdkshort_md.md)] tema [estilos de fecha y hora selector de Control](http://msdn.microsoft.com/library/windows/desktop/bb761728).  
  
 El control de selector de fecha y hora también usa las notificaciones y devoluciones de llamada, que se describen en [utilizar CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdtctl.h  
  
##  <a name="cdatetimectrl"></a>CDateTimeCtrl::CDateTimeCtrl  
 Construye un objeto `CDateTimeCtrl`.  
  
```  
CDateTimeCtrl();
```  
  
##  <a name="closemonthcal"></a>CDateTimeCtrl::CloseMonthCal  
 Cierra el control de selector de fecha y hora actual.  
  
```  
void CloseMonthCal() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [DTM_CLOSEMONTHCAL](http://msdn.microsoft.com/library/windows/desktop/bb761753) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_dateTimeCtrl`, que se utiliza para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[1 NVC_MFC_CDateTimeCtrl_s1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se cierra el calendario desplegable para el control de selector de fecha y hora actual.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;5](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_2.cpp)]  
  
##  <a name="create"></a>CDateTimeCtrl::Create  
 Crea el control de selector de fecha y hora y lo adjunta a la `CDateTimeCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica la combinación de estilos de control de tiempo de fecha. Consulte [estilos de fecha y hora selector Control](http://msdn.microsoft.com/library/windows/desktop/bb761728) en la [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información acerca de los estilos de selector de fecha y hora.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura, que es la posición y el tamaño del control de selector de fecha y hora.  
  
 `pParentWnd`  
 Un puntero a un [CWnd](../../mfc/reference/cwnd-class.md) objeto de la ventana primaria del control de selector de fecha y hora. No debe ser **NULL**.  
  
 `nID`  
 Especifica el identificador de control de. fecha y hora selector del control  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si se creó correctamente; en caso contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
  
##### <a name="to-create-a-date-and-time-picker-control"></a>Para crear un control de selector de fecha y hora  
  
1.  Llame a [CDateTimeCtrl](#cdatetimectrl) para construir un `CDateTimeCtrl` objeto.  
  
2.  Llame a esta función miembro, que crea el control de selector de fecha y hora de Windows y lo adjunta a la `CDateTimeCtrl` objeto.  
  
 Cuando se llama a **crear**, se inicializan los controles comunes.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_MFC_CDateTimeCtrl](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_3.cpp)]  
  
##  <a name="getdatetimepickerinfo"></a>CDateTimeCtrl::GetDateTimePickerInfo  
 Recupera información sobre el control de selector de fecha y hora actual.  
  
```   
BOOL GetDateTimePickerInfo(LPDATETIMEPICKERINFO pDateTimePickerInfo) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `pDateTimePickerInfo`|Un puntero a un [DATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761729) estructura que recibe una descripción del control de selector de fecha y hora actual.<br /><br /> El llamador es responsable de asignar esta estructura. Sin embargo, este método inicializa la `cbSize` miembro de la estructura.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si este método se realiza correctamente; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [DTM_GETDATETIMEPICKERINFO](http://msdn.microsoft.com/library/windows/desktop/bb761755) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_dateTimeCtrl`, que se utiliza para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[1 NVC_MFC_CDateTimeCtrl_s1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se indica si correctamente recupera información sobre el control de selector de fecha y hora actual.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1 Nº&4;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_4.cpp)]  
  
##  <a name="getmonthcalcolor"></a>CDateTimeCtrl::GetMonthCalColor  
 Recupera el color de una parte determinada del calendario de mes en el control de selector de fecha y hora.  
  
```  
COLORREF GetMonthCalColor(int iColor) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `iColor`  
 Un `int` especificar qué área de color del calendario de mes para recuperar el valor. Para obtener una lista de valores, vea el `iColor` parámetro [SetMonthCalColor](#setmonthcalcolor).  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que representa la configuración de color de la parte especificada del control de calendario mensual si se realiza correctamente. La función devuelve -1 si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761759), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CDateTimeCtrl&#2;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_5.cpp)]  
  
##  <a name="getmonthcalctrl"></a>CDateTimeCtrl:: GetMonthCalCtrl  
 Recupera el `CMonthCalCtrl` objeto asociado con el control de selector de fecha y hora.  
  
```  
CMonthCalCtrl* GetMonthCalCtrl() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CMonthCalCtrl](../../mfc/reference/cmonthcalctrl-class.md) objeto, o **NULL** si es incorrecta o si la ventana no está visible.  
  
### <a name="remarks"></a>Comentarios  
 Controles de selector de fecha y hora en crean un control de calendario mensual secundario cuando el usuario hace clic en la flecha de lista desplegable. Cuando el `CMonthCalCtrl` objeto ya no es necesario, se destruye, por lo que la aplicación no debe basarse en almacenar el objeto que representa el calendario mensual de fecha hora selector del control secundario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CDateTimeCtrl&3;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_6.cpp)]  
  
##  <a name="getmonthcalfont"></a>CDateTimeCtrl::GetMonthCalFont  
 Obtiene la fuente usada actualmente por la fecha y el control de calendario mensual del control de selector de hora.  
  
```  
CFont* GetMonthCalFont() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero a un [CFont](../../mfc/reference/cfont-class.md) objeto, o **NULL** si no lo consigue.  
  
### <a name="remarks"></a>Comentarios  
 La `CFont` objeto al que señala el valor devuelto es un objeto temporal y se destruye durante el tiempo de procesamiento inactivo siguiente.  
  
##  <a name="getmonthcalstyle"></a>CDateTimeCtrl::GetMonthCalStyle  
 Obtiene el estilo del control de calendario mensual de lista desplegable que está asociado con el control de selector de fecha y hora actual.  
  
```  
DWORD GetMonthCalStyle() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estilo del control de calendario mensual de lista desplegable, que es una combinación bit a bit (o) de los estilos de control de selector de fecha y hora. Para obtener más información, consulte [estilos de Control de calendario de mes](http://msdn.microsoft.com/library/windows/desktop/bb760919).  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [DTM_GETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761763) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="getrange"></a>CDateTimeCtrl::GetRange  
 Recupera actual mínimo y máximo permitido de horas del sistema para un control de selector de fecha y hora.  
  
```  
DWORD GetRange(
    COleDateTime* pMinRange,  
    COleDateTime* pMaxRange) const;  
  
DWORD GetRange(
    CTime* pMinRange,  
    CTime* pMaxRange) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `pMinRange`  
 Un puntero a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora más temprana permitida en la `CDateTimeCtrl` objeto.  
  
 `pMaxRange`  
 Un puntero a un `COleDateTime` objeto o un `CTime` objeto que contiene la hora más reciente permitida en la `CDateTimeCtrl` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `DWORD` valor que contiene marcas que indican qué intervalos configurados. Si  
  
 `return value & GDTR_MAX` == 0  
  
 a continuación, el segundo parámetro es válido. De forma similar, si  
  
 `return value & GDTR_MIN` == 0  
  
 a continuación, el primer parámetro es válido.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761767), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC, puede especificar `COleDateTime` o `CTime` usos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CDateTimeCtrl Nº&4;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_7.cpp)]  
  
##  <a name="gettime"></a>CDateTimeCtrl::GetTime  
 Recupera el tiempo seleccionado de un control de selector de fecha y hora y lo coloca en un especificado `SYSTEMTIME` estructura.  
  
```  
BOOL GetTime(COleDateTime& timeDest) const;  
DWORD GetTime(CTime& timeDest) const;  
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *timeDest*  
 En la primera versión, una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que recibirá la información de hora del sistema. En la segunda versión, una referencia a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que recibirá la información de hora del sistema.  
  
 *pTimeDest*  
 Un puntero a la [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura para recibir la información de hora del sistema. No debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 En la primera versión es distinto de cero si se ha escrito correctamente el tiempo para la `COleDateTime` objeto; en caso contrario, 0. En las versiones de la segunda y terceros, un `DWORD` valor igual a la **dwFlag** conjunto de miembros el [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) estructura. Consulte la **comentarios** sección para obtener más información.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_GETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761769), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de **GetTime**, puede usar `COleDateTime` o `CTime` clases, o puede usar un `SYSTEMTIME` estructura para almacenar la información de tiempo.  
  
 El valor devuelto `DWORD` en las versiones de la segunda y terceros, indica si el control de selector de fecha y hora se establece en el estado "sin fecha", como se indica en la [NMDATETIMECHANGE](http://msdn.microsoft.com/library/windows/desktop/bb761730) miembro de la estructura `dwFlags`. Si el valor devuelto es igual a **GDT_NONE**, el control se establece en el estado "sin fecha" y utiliza el **DTS_SHOWNONE** estilo. Si el valor devuelto es igual a **GDT_VALID**, la hora del sistema se almacena correctamente en la ubicación de destino.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CDateTimeCtrl&#5;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_8.cpp)]  
  
##  <a name="getidealsize"></a>CDateTimeCtrl::GetIdealSize  
 Devuelve el tamaño ideal de control de selector de fecha y hora en que se requiere para mostrar la fecha u hora actuales.  
  
```  
BOOL GetIdealSize(LPSIZE psize) const;  
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[out] `psize`|Puntero a un [tamaño](http://msdn.microsoft.com/library/windows/desktop/dd145106) estructura que contiene el tamaño ideal para el control.|  
  
### <a name="return-value"></a>Valor devuelto  
 El valor devuelto es siempre `true`.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [DTM_GETIDEALSIZE](http://msdn.microsoft.com/library/windows/desktop/bb761757) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_dateTimeCtrl`, que se utiliza para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[1 NVC_MFC_CDateTimeCtrl_s1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se recupera el tamaño ideal para mostrar el control de selector de fecha y hora.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s&#1;2](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_9.cpp)]  
  
##  <a name="setformat"></a>CDateTimeCtrl:: SetFormat  
 Establece la presentación de un control de selector de fecha y hora con arreglo a una cadena de formato especificado.  
  
```  
BOOL SetFormat(LPCTSTR pstrFormat);
```  
  
### <a name="parameters"></a>Parámetros  
 *pstrFormat*  
 Puntero a una cadena de formato terminada en cero que define la presentación deseada. Establecer este parámetro en **NULL** restablecerá el control a la cadena de formato predeterminado para el estilo actual.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
> [!NOTE]
>  Proporcionados por el usuario no determinan el éxito o error para esta llamada.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb761771), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CDateTimeCtrl Nº&6;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_10.cpp)]  
  
##  <a name="setmonthcalcolor"></a>CDateTimeCtrl::SetMonthCalColor  
 Establece el color de una parte determinada del calendario de mes dentro de un control de selector de fecha y hora.  
  
```  
COLORREF SetMonthCalColor(
    int iColor,  
    COLORREF ref);
```  
  
### <a name="parameters"></a>Parámetros  
 `iColor`  
 `int`valor que especifica qué área del control de calendario mensual para establecer. Este valor puede ser uno de los siguientes.  
  
|Valor|Significado|  
|-----------|-------------|  
|MCSC_BACKGROUND|Establecer el color de fondo que se muestran entre los meses.|  
|MCSC_MONTHBK|Establecer el color de fondo que se muestra dentro de un mes.|  
|MCSC_TEXT|Establezca el color utilizado para mostrar texto en un mes.|  
|MCSC_TITLEBK|Establecer el color de fondo que se muestra en el título del calendario.|  
|MCSC_TITLETEXT|Establece el color utilizado para mostrar texto en el título del calendario.|  
|MCSC_TRAILINGTEXT|Establezca el color utilizado para mostrar texto de encabezado y al final de día. Encabezado y los días finales son los días de los meses anteriores y siguientes que aparecen en el calendario actual.|  
  
 `ref`  
 Un **COLORREF** valor que representa el color que se establecerá para el área especificada del calendario del mes.  
  
### <a name="return-value"></a>Valor devuelto  
 Un **COLORREF** valor que representa la configuración de color anteriores de la parte especificada del control de calendario mensual si se realiza correctamente. De lo contrario, el mensaje devuelve -1.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETMCCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761773), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDateTimeCtrl::GetMonthCalColor](#getmonthcalcolor).  
  
##  <a name="setmonthcalfont"></a>CDateTimeCtrl:: SetMonthCalFont  
 Establece la fuente que utilizará el control de calendario mensual de fecha y hora selector del control secundario.  
  
```  
void SetMonthCalFont(
    HFONT hFont,  
    BOOL bRedraw = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `hFont`  
 Identificador de la fuente que se establecerá.  
  
 `bRedraw`  
 Especifica si el control debe volver a dibujar inmediatamente tras la configuración de la fuente. Establecer este parámetro en **TRUE** hace que vuelva a dibujarse el control.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETMCFONT](http://msdn.microsoft.com/library/windows/desktop/bb761775), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CDateTimeCtrl&#7;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_11.cpp)]  
  
> [!NOTE]
>  Si utiliza este código, deseará convertir en miembro de la `CDialog`-derivado de la clase denominada `m_MonthFont` de tipo **CFont**.  
  
##  <a name="setmonthcalstyle"></a>CDateTimeCtrl::SetMonthCalStyle  
 Establece el estilo del control de calendario mensual de lista desplegable que está asociado con el control de selector de fecha y hora actual.  
  
```  
DWORD SetMonthCalStyle(DWORD dwStyle);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `dwStyle`|Estilo del control, que es una combinación bit a bit (OR) de estilos de control de calendario de mes del calendario de un nuevo mes. Para obtener más información, consulte [estilos de Control de calendario de mes](http://msdn.microsoft.com/library/windows/desktop/bb760919).|  
  
### <a name="return-value"></a>Valor devuelto  
 Estilo anterior del control de calendario mensual de la lista desplegable.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [DTM_SETMCSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb761778) mensaje, que se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se define la variable `m_dateTimeCtrl`, que se utiliza para obtener acceso mediante programación el control de selector de fecha y hora. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[1 NVC_MFC_CDateTimeCtrl_s1](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_1.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se establece el control de selector de fecha y hora para mostrar los números de semana, los nombres abreviados de los días de la semana y no hay indicador de hoy.  
  
 [!code-cpp[NVC_MFC_CDateTimeCtrl_s1&3;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_12.cpp)]  
  
##  <a name="setrange"></a>CDateTimeCtrl::SetRange  
 Establece las horas de máximo y mínimo sistema permitido para un control de selector de fecha y hora.  
  
```  
BOOL SetRange(
    const COleDateTime* pMinRange,  
    const COleDateTime* pMaxRange);

 
BOOL SetRange(
    const CTime* pMinRange,  
    const CTime* pMaxRange);
```  
  
### <a name="parameters"></a>Parámetros  
 `pMinRange`  
 Un puntero a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto o un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora más temprana permitida en la `CDateTimeCtrl` objeto.  
  
 `pMaxRange`  
 Un puntero a un `COleDateTime` objeto o un `CTime` objeto que contiene la hora más reciente permitida en la `CDateTimeCtrl` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETRANGE](http://msdn.microsoft.com/library/windows/desktop/bb761780), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC, puede especificar `COleDateTime` o `CTime` usos. Si el `COleDateTime` objeto tiene una **NULL** estado, se quitará el intervalo. Si el `CTime` puntero o `COleDateTime` puntero es **NULL**, se quitará el intervalo.  
  
### <a name="example"></a>Ejemplo  
  Vea el ejemplo de [CDateTimeCtrl::GetRange](#getrange).  
  
##  <a name="settime"></a>CDateTimeCtrl::SetTime  
 Establece el tiempo en un control de selector de fecha y hora.  
  
```  
BOOL SetTime(const COleDateTime& timeNew);  
BOOL SetTime(const CTime* pTimeNew);  
BOOL SetTime(LPSYSTEMTIME pTimeNew = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 *timeNew*  
 Una referencia a un [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) objeto que contiene el para que se establecerá el control.  
  
 *pTimeNew*  
 En la segunda versión anterior, un puntero a un [CTime](../../atl-mfc-shared/reference/ctime-class.md) objeto que contiene la hora a la que se establecerá el control. En la tercera versión anterior, un puntero a un [SYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/ms724950) estructura que contiene la hora a la que se establecerá el control.  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro implementa el comportamiento del mensaje de Win32 [DTM_SETSYSTEMTIME](http://msdn.microsoft.com/library/windows/desktop/bb761782), como se describe en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]. En la implementación de MFC de **SetTime**, puede utilizar el `COleDateTime` o `CTime` clases, o puede usar un `SYSTEMTIME` estructura para establecer la información de hora.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CDateTimeCtrl Nº&8;](../../mfc/reference/codesnippet/cpp/cdatetimectrl-class_13.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL1 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl (clase)](../../mfc/reference/cmonthcalctrl-class.md)

