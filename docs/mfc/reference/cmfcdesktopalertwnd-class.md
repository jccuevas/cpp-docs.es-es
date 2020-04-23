---
title: CMFCDesktopAlertWnd Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
ms.openlocfilehash: cf453b6e69f012bedaf0bd91b5eaf11f7caffa12
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752452"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

La `CMFCDesktopAlertWnd` clase implementa la funcionalidad de un cuadro de diálogo no basado en el cuadro de diálogo que aparece en la pantalla para informar al usuario sobre un evento.

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

## <a name="syntax"></a>Sintaxis

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Crear](#create)|Crea e inicializa la ventana de alerta de escritorio.|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|Devuelve la velocidad de animación.|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|Devuelve el tipo de animación.|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|Devuelve el tiempo de espera de cierre automático.|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|Devuelve el alto del título.|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|Devuelve la última posición válida de la ventana de alerta de escritorio en la pantalla.|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|Devuelve el nivel de transparencia.|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|Determina si la ventana de alerta de escritorio se muestra con el título pequeño.|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|Llamado por el marco de trabajo cuando el usuario hace clic en un botón de vínculo ubicado en el menú de alerta del escritorio.|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|El marco de trabajo llama a esta función miembro cuando el usuario selecciona un elemento de un menú, cuando un control secundario envía un mensaje de notificación o cuando se traduce una pulsación de tecla del acelerador. (Reemplaza [CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand).)|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|Establece la nueva velocidad de animación.|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|Establece el tipo de animación.|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|Establece el tiempo de espera de cierre automático.|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|Cambia entre subtítulos pequeños y normales.|
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|Establece el nivel de transparencia.|

## <a name="remarks"></a>Observaciones

Una ventana de alerta de escritorio puede ser transparente, puede aparecer con efectos de animación y puede desaparecer (después de un retraso especificado o cuando el usuario lo descarta haciendo clic en el botón Cerrar).

Una ventana de alerta de escritorio también puede contener un cuadro de diálogo predeterminado que, a su vez, contiene un icono, un texto de mensaje (una etiqueta) y un vínculo. Como alternativa, una ventana de alerta de escritorio puede contener un cuadro de diálogo personalizado de los recursos de la aplicación.

Cree una ventana de alerta de escritorio en dos pasos. En primer lugar, llame `CMFCDesktopAlertWnd` al constructor para construir el objeto. En segundo lugar, llame a la [CMFCDesktopAlertWnd::Create](#create) función miembro para crear la ventana y adjuntarla al `CMFCDesktopAlertWnd` objeto.

El `CMFCDesktopAlertWnd` objeto crea un cuadro de diálogo secundario especial que rellena el área de cliente de la ventana de alerta de escritorio. El cuadro de diálogo posee todos los controles que se colocan en él.

Para mostrar un cuadro de diálogo personalizado en la ventana emergente, siga estos pasos:

1. Derivar una clase de `CMFCDesktopAlertDialog`.

1. Cree una plantilla de cuadro de diálogo secundario en los recursos.

1. Llame a [CMFCDesktopAlertWnd::Create](#create) utilizando el identificador de recurso de la plantilla de cuadro de diálogo y un puntero a la información de clase en tiempo de ejecución de la clase derivada.

1. Programe el cuadro de diálogo personalizado para controlar todas las notificaciones procedentes de los controles hospedados o programe los controles hospedados para controlar estas notificaciones directamente.

Utilice las siguientes funciones para controlar el comportamiento de la ventana de alerta de escritorio:

- Establezca el tipo de animación llamando a [CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype). Las opciones válidas incluyen desdoblar, deslizar y desvanecer.

- Establezca la velocidad del fotograma de animación llamando a [CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed).

- Establezca el nivel de transparencia llamando a [CMFCDesktopAlertWnd::SetTransparency](#settransparency).

- Cambie el tamaño del título a pequeño llamando a [CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption). El título pequeño tiene 7 píxeles de alto.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra `CMFCDesktopAlertWnd` cómo utilizar `CMFCDesktopAlertWnd` varios métodos de la clase para configurar un objeto. En el ejemplo se muestra cómo establecer un tipo de animación, establecer la transparencia de la ventana emergente, especificar que la ventana de alerta muestra un título pequeño y establecer el tiempo que transcurre antes de que la ventana de alerta se cierre automáticamente. En el ejemplo también se muestra cómo crear e inicializar la ventana de alerta de escritorio. Este fragmento de código forma parte del [ejemplo Demostración de alertas](../../overview/visual-cpp-samples.md)de escritorio.

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>Requisitos

**Encabezado:** afxDesktopAlertWnd.h

## <a name="cmfcdesktopalertwndcreate"></a><a name="create"></a>CMFCDesktopAlertWnd::Crear

Crea e inicializa la ventana de alerta de escritorio.

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>Parámetros

*pWndOwner*<br/>
[adentro, fuera] Especifica el propietario de la ventana de alerta. A continuación, ese propietario recibirá todas las notificaciones de la ventana de alerta de escritorio. Este valor no puede ser NULL.

*uiDlgResID*<br/>
[en] Especifica el identificador de recurso de la ventana de alerta.

*hMenú*<br/>
[en] Especifica el menú que se muestra cuando el usuario hace clic en el botón de menú. Si NULL, no se muestra el botón de menú.

*ptPos*<br/>
[en] Especifica la posición inicial en la que se muestra la ventana de alerta, utilizando coordenadas de pantalla. Si este parámetro es (-1, -1), la ventana de alerta se muestra en la esquina inferior derecha de la pantalla.

*pRTIDlgBar*<br/>
[en] Información de clase en tiempo de ejecución para una clase de cuadro de diálogo personalizado que cubre el área de cliente de la ventana de alerta.

*params*<br/>
[en] Especifica los parámetros que se utilizan para crear una ventana de alerta.

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana de alerta se creó correctamente; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Llame a este método para crear una ventana de alerta. El área de cliente de la ventana de alerta contiene un cuadro de diálogo secundario que hospeda todos los controles que se muestran al usuario.

La primera sobrecarga de método crea una ventana de alerta que contiene un cuadro de diálogo secundario que se carga desde los recursos de la aplicación. La primera sobrecarga de método también puede especificar información de clase en tiempo de ejecución para una clase de cuadro de diálogo personalizado.

La segunda sobrecarga del método crea una ventana de alerta que contiene controles predeterminados. Puede especificar qué controles mostrar modificando la [clase CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md).

## <a name="cmfcdesktopalertwndgetanimationspeed"></a><a name="getanimationspeed"></a>CMFCDesktopAlertWnd::GetAnimationSpeed

Devuelve la velocidad de animación.

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>Valor devuelto

La velocidad de animación de la ventana de alerta, en milisegundos.

### <a name="remarks"></a>Observaciones

La velocidad de animación describe la velocidad con la que se abre y se cierra la ventana de alerta.

## <a name="cmfcdesktopalertwndgetanimationtype"></a><a name="getanimationtype"></a>CMFCDesktopAlertWnd::GetAnimationType

Devuelve el tipo de animación.

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>Valor devuelto

Uno de los siguientes tipos de animación:

- NO_ANIMATION

- Revelan

- Deslice

- Se descolora

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndgetautoclosetime"></a><a name="getautoclosetime"></a>CMFCDesktopAlertWnd::GetAutoCloseTime

Devuelve el tiempo de espera de cierre automático.

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>Valor devuelto

El tiempo, en milisegundos, después del cual la ventana de alerta se cerrará automáticamente.

### <a name="remarks"></a>Observaciones

Utilice este método para determinar cuánto tiempo debe transcurrir antes de que la ventana de alerta se cierre automáticamente.

## <a name="cmfcdesktopalertwndgetcaptionheight"></a><a name="getcaptionheight"></a>CMFCDesktopAlertWnd::GetCaptionHeight

Devuelve el alto del título.

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>Valor devuelto

La altura, en píxeles, del título.

### <a name="remarks"></a>Observaciones

Este método se puede invalidar en una clase derivada. La implementación predeterminada: devuelve el valor de altura de título pequeño (7 píxeles) si la ventana `GetSystemMetrics(SM_CYSMCAPTION)`emergente debe mostrar el título pequeño o el valor obtenido de la función de API de Windows.

## <a name="cmfcdesktopalertwndgetlastpos"></a><a name="getlastpos"></a>CMFCDesktopAlertWnd::GetLastPos

Devuelve la última posición de la ventana de alerta de escritorio en la pantalla.

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>Valor devuelto

Un punto, en coordenadas de pantalla.

### <a name="remarks"></a>Observaciones

Este método devuelve la última posición válida de la ventana de alerta en la pantalla.

## <a name="cmfcdesktopalertwndgettransparency"></a><a name="gettransparency"></a>CMFCDesktopAlertWnd::GetTransparency

Devuelve el nivel de transparencia.

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>Valor devuelto

Un nivel de transparencia entre 0 y 255, ambos inclusive. Cuanto mayor sea el valor, más opaca será la ventana.

### <a name="remarks"></a>Observaciones

Utilice este método para recuperar el nivel de transparencia actual de la ventana de alerta.

## <a name="cmfcdesktopalertwndhassmallcaption"></a><a name="hassmallcaption"></a>CMFCDesktopAlertWnd::HasSmallCaption

Determina si la ventana de alerta de escritorio tiene un título pequeño o un título de tamaño normal.

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi la ventana emergente se muestra con un título pequeño; FALSE si la ventana emergente se muestra con un título de tamaño normal.

### <a name="remarks"></a>Observaciones

Utilice este método para determinar si la ventana emergente tiene un título pequeño o un título de tamaño normal. De forma predeterminada, el título pequeño tiene 7 píxeles de alto. Puede obtener el alto del título de tamaño normal `GetSystemMetrics(SM_CYCAPTION)`llamando a la función API de Windows.

## <a name="cmfcdesktopalertwndonbeforeshow"></a><a name="onbeforeshow"></a>CMFCDesktopAlertWnd::OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>Parámetros

[en] *CPoint&*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcdesktopalertwndonclicklinkbutton"></a><a name="onclicklinkbutton"></a>CMFCDesktopAlertWnd::OnClickLinkButton

Llamado por el marco de trabajo cuando el usuario hace clic en un botón de vínculo ubicado en el menú de alerta del escritorio.

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>Parámetros

*uiCmdID*<br/>
[en] Este parámetro no se utiliza.

### <a name="return-value"></a>Valor devuelto

Siempre FALSE.

### <a name="remarks"></a>Observaciones

Invalide este método en una clase derivada si desea recibir una notificación cuando un usuario hace clic en el vínculo de la ventana de alerta.

## <a name="cmfcdesktopalertwndoncommand"></a><a name="oncommand"></a>CMFCDesktopAlertWnd::OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parámetros

[en] *wParam*<br/>

[en] *lParam*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcdesktopalertwndondraw"></a><a name="ondraw"></a>CMFCDesktopAlertWnd::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parámetros

[en] *pDC*<br/>

### <a name="remarks"></a>Observaciones

## <a name="cmfcdesktopalertwndprocesscommand"></a><a name="processcommand"></a>CMFCDesktopAlertWnd::ProcessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>Parámetros

[en] *hwnd*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcdesktopalertwndsetanimationspeed"></a><a name="setanimationspeed"></a>CMFCDesktopAlertWnd::SetAnimationSpeed

Establece la nueva velocidad de animación.

```cpp
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>Parámetros

*nVelocidad*<br/>
[en] Especifica la nueva velocidad de animación, en milisegundos.

### <a name="remarks"></a>Observaciones

Llame a este método para establecer la velocidad de animación para la ventana de alerta. La velocidad de animación predeterminada es de 30 milisegundos.

## <a name="cmfcdesktopalertwndsetanimationtype"></a><a name="setanimationtype"></a>CMFCDesktopAlertWnd::SetAnimationType

Establece el tipo de animación.

```cpp
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>Parámetros

*type*<br/>
[en] Especifica el tipo de animación.

### <a name="remarks"></a>Observaciones

Llame a este método para establecer el tipo de animación. Puede especificar uno de los siguientes valores:

- NO_ANIMATION

- Revelan

- Deslice

- Se descolora

- SYSTEM_DEFAULT_ANIMATION

## <a name="cmfcdesktopalertwndsetautoclosetime"></a><a name="setautoclosetime"></a>CMFCDesktopAlertWnd::SetAutoCloseTime

Establece el tiempo de espera de cierre automático.

```cpp
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>Parámetros

*Ntime*<br/>
[en] El tiempo, en milisegundos, que transcurre antes de que la ventana de alerta se cierre automáticamente.

### <a name="remarks"></a>Observaciones

La ventana de alerta se cierra automáticamente después del tiempo especificado si el usuario no interactúa con la ventana.

## <a name="cmfcdesktopalertwndsetsmallcaption"></a><a name="setsmallcaption"></a>CMFCDesktopAlertWnd::SetSmallCaption

Cambia entre subtítulos pequeños y de tamaño normal.

```cpp
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>Parámetros

*bSmallCaption*<br/>
[en] TRUE para especificar que la ventana de alerta muestra un título pequeño; de lo contrario, FALSE para especificar que la ventana de alerta muestra un título de tamaño normal.

### <a name="remarks"></a>Observaciones

Llame a este método para mostrar el título de tamaño pequeño o regular. De forma predeterminada, el título pequeño tiene 7 píxeles de alto. Puede obtener el tamaño del título normal llamando `GetSystemMetrics(SM_CYCAPTION)`a la función API de Windows.

## <a name="cmfcdesktopalertwndsettransparency"></a><a name="settransparency"></a>CMFCDesktopAlertWnd::SetTransparency

Establece el nivel de transparencia de la ventana emergente.

```cpp
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>Parámetros

*nTransparencia*<br/>
[en] Especifica el nivel de transparencia. Este valor debe estar entre 0 y 255, ambos inclusive. Cuanto mayor sea el valor, más opaca será la ventana.

### <a name="remarks"></a>Observaciones

Llame a esta función para establecer el nivel de transparencia de la ventana emergente.

## <a name="cmfcdesktopalertwndgetdialogsize"></a><a name="getdialogsize"></a>CMFCDesktopAlertWnd::GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo Clase](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog (clase)](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)
