---
title: CProgressCtrl (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CProgressCtrl
- AFXCMN/CProgressCtrl
- AFXCMN/CProgressCtrl::CProgressCtrl
- AFXCMN/CProgressCtrl::Create
- AFXCMN/CProgressCtrl::CreateEx
- AFXCMN/CProgressCtrl::GetBarColor
- AFXCMN/CProgressCtrl::GetBkColor
- AFXCMN/CProgressCtrl::GetPos
- AFXCMN/CProgressCtrl::GetRange
- AFXCMN/CProgressCtrl::GetState
- AFXCMN/CProgressCtrl::GetStep
- AFXCMN/CProgressCtrl::OffsetPos
- AFXCMN/CProgressCtrl::SetBarColor
- AFXCMN/CProgressCtrl::SetBkColor
- AFXCMN/CProgressCtrl::SetMarquee
- AFXCMN/CProgressCtrl::SetPos
- AFXCMN/CProgressCtrl::SetRange
- AFXCMN/CProgressCtrl::SetState
- AFXCMN/CProgressCtrl::SetStep
- AFXCMN/CProgressCtrl::StepIt
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl [MFC], CProgressCtrl
- CProgressCtrl [MFC], Create
- CProgressCtrl [MFC], CreateEx
- CProgressCtrl [MFC], GetBarColor
- CProgressCtrl [MFC], GetBkColor
- CProgressCtrl [MFC], GetPos
- CProgressCtrl [MFC], GetRange
- CProgressCtrl [MFC], GetState
- CProgressCtrl [MFC], GetStep
- CProgressCtrl [MFC], OffsetPos
- CProgressCtrl [MFC], SetBarColor
- CProgressCtrl [MFC], SetBkColor
- CProgressCtrl [MFC], SetMarquee
- CProgressCtrl [MFC], SetPos
- CProgressCtrl [MFC], SetRange
- CProgressCtrl [MFC], SetState
- CProgressCtrl [MFC], SetStep
- CProgressCtrl [MFC], StepIt
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6317ce9484cc471611762d10e6f1482f24c2742a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cprogressctrl-class"></a>CProgressCtrl (clase)
Proporciona la funcionalidad del control de barra de progreso común de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CProgressCtrl::CProgressCtrl](#cprogressctrl)|Construye un objeto `CProgressCtrl`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CProgressCtrl::Create](#create)|Crea un control de barra de progreso y lo adjunta a un `CProgressCtrl` objeto.|  
|[CProgressCtrl::CreateEx](#createex)|Crea un control de progreso con los estilos extendidos de Windows especificados y lo adjunta a un `CProgressCtrl` objeto.|  
|[CProgressCtrl::GetBarColor](#getbarcolor)|Obtiene el color de la barra de indicador de progreso para el control de barra de progreso actual.|  
|[CProgressCtrl::GetBkColor](#getbkcolor)|Obtiene el color de fondo de la barra de progreso actual.|  
|[CProgressCtrl::GetPos](#getpos)|Obtiene la posición actual de la barra de progreso.|  
|[CProgressCtrl::GetRange](#getrange)|Obtiene los límites inferiores y superiores del intervalo del control de barra de progreso.|  
|[CProgressCtrl:: GetState](#getstate)|Obtiene el estado del control de barra de progreso actual.|  
|[CProgressCtrl::GetStep](#getstep)|Recupera el incremento de paso de la barra de progreso del control de barra de progreso actual.|  
|[CProgressCtrl::OffsetPos](#offsetpos)|Hace avanzar la posición actual de un control de barra de progreso en un incremento especificado y vuelve a dibujar la barra para reflejar la nueva posición.|  
|[CProgressCtrl::SetBarColor](#setbarcolor)|Establece el color de la barra de indicador de progreso en el control de barra de progreso actual.|  
|[CProgressCtrl::SetBkColor](#setbkcolor)|Establece el color de fondo de la barra de progreso.|  
|[CProgressCtrl::SetMarquee](#setmarquee)|Desactiva el modo de marquesina activado o desactivado para el control de barra de progreso actual.|  
|[CProgressCtrl::SetPos](#setpos)|Establece la posición actual para un control de barra de progreso y vuelve a dibujar la barra para reflejar la nueva posición.|  
|[CProgressCtrl::SetRange](#setrange)|Establece el intervalo mínimo y máximo para un control de barra de progreso y vuelve a dibujar la barra para reflejar los nuevos intervalos.|  
|[CProgressCtrl::SetState](#setstate)|Establece el estado del control de la barra de progreso actual.|  
|[CProgressCtrl::SetStep](#setstep)|Especifica el incremento de paso de un control de barra de progreso.|  
|[CProgressCtrl::StepIt](#stepit)|Hace avanzar la posición actual para un control de barra de progreso en el incremento de paso (vea [SetStep](#setstep)) y vuelve a dibujar la barra para reflejar la nueva posición.|  
  
## <a name="remarks"></a>Comentarios  
 Un control de barra de progreso es una ventana que una aplicación puede utilizar para indicar el progreso de una operación larga. Está formada por un rectángulo que se rellena gradualmente, de izquierda a derecha, con el sistema de color de resaltado como que una operación progresa.  
  
 Un control de barra de progreso tiene un intervalo y la posición actual. El intervalo representa la duración total de la operación y la posición actual representa el progreso realizado por la aplicación para completar la operación. El procedimiento de ventana utiliza el intervalo y la posición actual para determinar el porcentaje de la barra de progreso para rellenar con el color de resaltado. Porque el intervalo y los valores actuales de posición se expresan como enteros con signo, el intervalo posible de los valores de posición actual es de -2.147.483.648 a 2.147.483.647 ambos inclusive.  
  
 Para obtener más información sobre el uso de `CProgressCtrl`, consulte [controles](../../mfc/controls-mfc.md) y [usar CProgressCtrl](../../mfc/using-cprogressctrl.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxcmn.h  
  
##  <a name="cprogressctrl"></a>  CProgressCtrl::CProgressCtrl  
 Construye un objeto `CProgressCtrl`.  
  
```  
CProgressCtrl();
```  
  
### <a name="remarks"></a>Comentarios  
 Después de crear el `CProgressCtrl` objeto, llame a `CProgressCtrl::Create` para crear el control de barra de progreso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CProgressCtrl::Create  
 Crea un control de barra de progreso y lo adjunta a un `CProgressCtrl` objeto.  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwStyle`  
 Especifica el estilo del control de barra de progreso. Aplicar cualquier combinación de ventana stylesdescribed en [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) del SDK de Windows, además de la barra estilos de control, para el control de progreso siguiente:  
  
- `PBS_VERTICAL` Muestra información de progreso verticalmente, de arriba a abajo. Sin esta marca, el control de barra de progreso muestra horizontalmente, de izquierda a derecha.  
  
- `PBS_SMOOTH` Muestra gradual y suave rellenar el control de barra de progreso. Sin esta marca, el control se rellenará con bloques.  
  
 `rect`  
 Especifica el tamaño y la posición del control de barra de progreso. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura. Dado que el control debe ser una ventana secundaria, las coordenadas especificadas están en relación con el área cliente de la `pParentWnd`.  
  
 `pParentWnd`  
 Especifica el progreso de la barra de la ventana primaria de control, normalmente un `CDialog`. No debe ser **NULL.**  
  
 `nID`  
 Especifica el identificador. del control de barra de progreso  
  
### <a name="return-value"></a>Valor devuelto  
 **TRUE** si la `CProgressCtrl` objeto se creó correctamente; en caso contrario **FALSE**.  
  
### <a name="remarks"></a>Comentarios  
 Crear un `CProgressCtrl` objeto en dos pasos. En primer lugar, llame al constructor, que crea el `CProgressCtrl` objeto y, a continuación, llame a **crear**, que crea el control de barra de progreso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CProgressCtrl::CreateEx  
 Crea un control (una ventana secundaria) y lo asocia a la `CProgressCtrl` objeto.  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwExStyle`  
 Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el `dwExStyle` parámetro [CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680) del SDK de Windows.  
  
 `dwStyle`  
 Especifica el estilo del control de barra de progreso. Aplicar cualquier combinación de los estilos de ventana se describe en [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679) del SDK de Windows.  
  
 `rect`  
 Una referencia a un [RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y la posición de la ventana que se creará, en coordenadas de cliente de `pParentWnd`.  
  
 `pParentWnd`  
 Un puntero a la ventana que es primario del control.  
  
 `nID`  
 Identificador de ventana secundaria. del control  
  
### <a name="return-value"></a>Valor devuelto  
 Si es correcta, su valor es distinto de cero. En caso contrario, es cero.  
  
### <a name="remarks"></a>Comentarios  
 Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.  
  
##  <a name="getbarcolor"></a>  CProgressCtrl::GetBarColor  
 Obtiene el color de la barra de indicador de progreso para el control de barra de progreso actual.  
  
```  
COLORREF GetBarColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color de la barra de progreso actual, representado como un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor, o `CLR_DEFAULT` si el color de la barra de progreso indicador es el color predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PBM_GETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760826) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getbkcolor"></a>  CProgressCtrl::GetBkColor  
 Obtiene el color de fondo de la barra de progreso actual.  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El color de fondo de la barra de progreso actual, representado como un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PBM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760828) mensaje, que se describe en el SDK de Windows.  
  
##  <a name="getpos"></a>  CProgressCtrl::GetPos  
 Recupera la posición actual de la barra de progreso.  
  
```  
int GetPos();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición del control de barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 La posición del control de barra de progreso no es la ubicación física en la pantalla, pero en su lugar se entre la parte superior e inferior intervalo indicado en [SetRange](#setrange).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_3.cpp)]  
  
##  <a name="getrange"></a>  CProgressCtrl::GetRange  
 Obtiene los límites inferiores y superiores actuales o el intervalo, del control de barra de progreso.  
  
```  
void GetRange(
    int& nLower,  
    int& nUpper);
```  
  
### <a name="parameters"></a>Parámetros  
 `nLower`  
 Una referencia a un entero que recibir el límite inferior del control de barra de progreso.  
  
 `nUpper`  
 Una referencia a un entero que recibir el límite superior del control de barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 Esta función copia los valores de los límites inferiores y superiores para los enteros encontrados por `nLower` y `nUpper`, respectivamente.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_4.cpp)]  
  
##  <a name="getstate"></a>  CProgressCtrl:: GetState  
 Obtiene el estado del control de barra de progreso actual.  
  
```  
int GetState() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El estado del control de barra de progreso actual, que es uno de los siguientes valores:  
  
|Valor|Estado|  
|-----------|-----------|  
|`PBST_NORMAL`|En curso|  
|`PBST_ERROR`|Error|  
|`PBST_PAUSED`|En pausa|  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PBM_GETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760834) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se recupera el estado del control de barra de progreso actual.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_6.cpp)]  
  
##  <a name="getstep"></a>  CProgressCtrl::GetStep  
 Recupera el incremento de paso de la barra de progreso del control de barra de progreso actual.  
  
```  
int GetStep() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El incremento del paso de la barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 El incremento de paso es la cantidad por el que una llamada a [CProgressCtrl::StepIt](#stepit) incrementa la posición actual de la barra de progreso.  
  
 Este método envía el [PBM_GETSTEP](http://msdn.microsoft.com/library/windows/desktop/bb760836) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se recupera el incremento del paso del control de barra de progreso actual.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#3](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_7.cpp)]  
  
##  <a name="offsetpos"></a>  CProgressCtrl::OffsetPos  
 Hace avanzar la posición actual del control de barra de progreso en el incremento especificado por `nPos` y vuelve a dibujar la barra para reflejar la nueva posición.  
  
```  
int OffsetPos(int nPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Cantidad de avanzar la posición.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición anterior del control de barra de progreso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#5](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_8.cpp)]  
  
##  <a name="setbarcolor"></a>  CProgressCtrl::SetBarColor  
 Establece el color de la barra de indicador de progreso en el control de barra de progreso actual.  
  
```  
COLORREF SetBarColor(COLORREF clrBar);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `clrBar`|A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que especifica el nuevo color de la barra de indicador de progreso. Especificar `CLR_DEFAULT` para hacer que la barra de progreso usar su color predeterminado.|  
  
### <a name="return-value"></a>Valor devuelto  
 El color anterior de la barra de indicador de progreso, representado como un [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor, o `CLR_DEFAULT` si el color de la barra de indicador de progreso es el color predeterminado.  
  
### <a name="remarks"></a>Comentarios  
 El `SetBarColor` método establece el progreso de la barra solo si de color una [!INCLUDE[windowsver](../../build/reference/includes/windowsver_md.md)] [tema](https://msdn.microsoft.com/library/windows/desktop/hh270423.aspx) no está en vigor.  
  
 Este método envía el [PBM_SETBARCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb760838) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se cambia el color de la barra de progreso a rojo, verde, azul o el valor predeterminado.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_9.cpp)]  
  
##  <a name="setbkcolor"></a>  CProgressCtrl::SetBkColor  
 Establece el color de fondo de la barra de progreso.  
  
```  
COLORREF SetBkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `clrNew`  
 A **COLORREF** valor que especifica el nuevo color de fondo. Especifique el `CLR_DEFAULT` valor para utilizar el color de fondo predeterminado en la barra de progreso.  
  
### <a name="return-value"></a>Valor devuelto  
 El [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449) valor que indica el color de fondo anterior, o **CLR_DEFAULT** si el color de fondo es el color predeterminado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#6](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_10.cpp)]  
  
##  <a name="setmarquee"></a>  CProgressCtrl::SetMarquee  
 Desactiva el modo de marquesina activado o desactivado para el control de barra de progreso actual.  
  
```  
BOOL SetMarquee(
    BOOL fMarqueeMode,   
    int nInterval);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `fMarqueeMode`|`true` Para activar el modo de marquesina o `false` para desactivar el modo de marquesina.|  
|[in] `nInterval`|Tiempo en milisegundos entre las actualizaciones de la animación de la marquesina.|  
  
### <a name="return-value"></a>Valor devuelto  
 Este método devuelve siempre `true`.  
  
### <a name="remarks"></a>Comentarios  
 Cuando el modo de marquesina está activado, se anima la barra de progreso y se desplaza al igual que un inicio de sesión en un recuadro de pantalla completa.  
  
 Este método envía el [PBM_SETMARQUEE](http://msdn.microsoft.com/library/windows/desktop/bb760842) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo de código siguiente se inicia y detiene la animación con desplazamiento de marquesina.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_11.cpp)]  
  
##  <a name="setpos"></a>  CProgressCtrl::SetPos  
 Establece el progreso de la posición actual del control según lo especificado por la barra `nPos` y vuelve a dibujar la barra para reflejar la nueva posición.  
  
```  
int SetPos(int nPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `nPos`  
 Nueva posición del control de barra de progreso.  
  
### <a name="return-value"></a>Valor devuelto  
 La posición anterior del control de barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 La posición del control de barra de progreso no es la ubicación física en la pantalla, pero en su lugar se entre la parte superior e inferior intervalo indicado en [SetRange](#setrange).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#7](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_12.cpp)]  
  
##  <a name="setrange"></a>  CProgressCtrl::SetRange  
 Establece los límites superiores e inferiores de la barra de intervalo del control de progreso y vuelve a dibujar la barra para reflejar los nuevos intervalos.  
  
```  
void SetRange(
    short nLower,  
    short nUpper);

 
void SetRange32(
    int nLower,  
    int nUpper);
```  
  
### <a name="parameters"></a>Parámetros  
 `nLower`  
 Especifica el límite inferior del intervalo (el valor predeterminado es cero).  
  
 `nUpper`  
 Especifica el límite superior del intervalo (el valor predeterminado es 100).  
  
### <a name="remarks"></a>Comentarios  
 La función miembro `SetRange32` establece el intervalo de 32 bits para el control de progreso.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#8](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_13.cpp)]  
  
##  <a name="setstate"></a>  CProgressCtrl::SetState  
 Establece el estado del control de la barra de progreso actual.  
  
```  
int SetState(int iState);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|[in] `iState`|El estado para establecer la barra de progreso. Utilice uno de los siguientes valores:<br /><br /> - `PBST_NORMAL` -En curso<br />- `PBST_ERROR` : Error<br />- `PBST_PAUSED` -En pausa|  
  
### <a name="return-value"></a>Valor devuelto  
 El estado anterior del control de la barra de progreso actual.  
  
### <a name="remarks"></a>Comentarios  
 Este método envía el [PBM_SETSTATE](http://msdn.microsoft.com/library/windows/desktop/bb760850) mensaje, que se describe en el SDK de Windows.  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código define la variable, `m_progressCtrl`, que se utiliza para acceder mediante programación al control de barra de progreso. Esta variable se utiliza en el siguiente ejemplo.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_5.h)]  
  
### <a name="example"></a>Ejemplo  
 El siguiente ejemplo de código establece el estado del control de la de barra de progreso actual como En pausa o En curso.  
  
 [!code-cpp[NVC_MFC_CProgressCtrl_s1#4](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_14.cpp)]  
  
##  <a name="setstep"></a>  CProgressCtrl::SetStep  
 Especifica el incremento de paso de un control de barra de progreso.  
  
```  
int SetStep(int nStep);
```  
  
### <a name="parameters"></a>Parámetros  
 *nPaso*  
 Nuevo incremento del paso.  
  
### <a name="return-value"></a>Valor devuelto  
 El incremento del paso anterior.  
  
### <a name="remarks"></a>Comentarios  
 El incremento de paso es la cantidad por el que una llamada a `CProgressCtrl::StepIt` aumenta el progreso de la barra de la posición actual.  
  
 El incremento de paso predeterminado es 10.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#9](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_15.cpp)]  
  
##  <a name="stepit"></a>  CProgressCtrl::StepIt  
 Hace avanzar la posición actual para un control de barra de progreso en el incremento de paso y vuelve a dibujar la barra para reflejar la nueva posición.  
  
```  
int StepIt();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La posición anterior del control de barra de progreso.  
  
### <a name="remarks"></a>Comentarios  
 El incremento de paso se establece mediante el `CProgressCtrl::SetStep` función miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFC_CProgressCtrl#10](../../mfc/reference/codesnippet/cpp/cprogressctrl-class_16.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [CMNCTRL2 de ejemplo MFC](../../visual-cpp-samples.md)   
 [CWnd (clase)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)


