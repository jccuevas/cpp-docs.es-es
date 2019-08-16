---
title: Clase CMFCAcceleratorKeyAssignCtrl
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: 5e57bf149fdbc293692c613afcabcf2d11d32221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505467"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Clase CMFCAcceleratorKeyAssignCtrl

La `CMFCAcceleratorKeyAssignCtrl` clase extiende la [clase CEDIT](../../mfc/reference/cedit-class.md) para admitir botones del sistema adicionales, como Alt, control y Shift.

## <a name="syntax"></a>Sintaxis

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Construye un objeto `CMFCAcceleratorKeyAssignCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Recupera la estructura `ACCEL` para una tecla de método abreviado pulsada en el objeto `CMFCAcceleratorKeyAssignCtrl`.|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Determina si se ha definido una tecla de método abreviado.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|La clase [CWinApp](../../mfc/reference/cwinapp-class.md) lo usa para traducir los mensajes de ventana antes de que se envíen a las funciones de Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Restablece la tecla de método abreviado.|

## <a name="remarks"></a>Comentarios

Esta clase extiende la funcionalidad de la clase `CEdit` ofreciendo compatibilidad con teclas de método abreviado, también conocido como teclas de aceleración. La `CMFCAcceleratorKeyAssignCtrl` clase funciona como una [clase CEDIT](../../mfc/reference/cedit-class.md) y también puede reconocer los botones del sistema.

Esta clase asigna combinaciones de teclas físicas de método abreviado a valores de cadena. Por ejemplo, suponga que la combinación de teclas ALT + B se asigna a la cadena "Alt + B". Cuando el usuario presione esta combinación de teclas en un objeto `CMFCAcceleratorKeyAssignCtrl`, se le mostrará "Alt + B". Para obtener más información sobre la asignación entre las teclas de método abreviado y un formato de cadena, consulte [clase cmfcacceleratorkey (](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo construir un objeto `CMFCAcceleratorKeyAssignCtrl` y utilizar su método `ResetKey` para restablecer la tecla de método abreviado.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxacceleratorkeyassignctrl. h

##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Construye un objeto [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel

Recupera la `ACCEL` estructura de una tecla de método abreviado presionada en el objeto [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Valor devuelto

`ACCEL` Estructura que describe la tecla de método abreviado.

### <a name="remarks"></a>Comentarios

Utilice esta función para recuperar la `ACCEL` estructura de una tecla de método abreviado que el usuario `CMFCAcceleratorKeyAssignCtrl` escribió en el objeto.

##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Determina si se ha definido una tecla de método abreviado en el objeto [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ya ha presionado una combinación válida de claves que definen una tecla de método abreviado; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Utilice esta función para determinar si el usuario ha escrito una tecla de método abreviado válida en el `CMFCAcceleratorKeyAssignCtrl` objeto. Si existe una tecla de método abreviado, puede utilizar el método [CMFCAcceleratorKeyAssignCtrl:: GetAccel](#getaccel) para obtener la `ACCEL` estructura asociada a esta tecla de método abreviado.

##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Para obtener más información, consulte el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\MFC** de la instalación de Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

de *pMsg*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Comentarios

##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey

Restablece la tecla de método abreviado.

```
void ResetKey();
```

### <a name="remarks"></a>Comentarios

La función borra el texto del control de edición. Esto incluye las teclas de método abreviado que el usuario presionó.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey (clase)](../../mfc/reference/cmfcacceleratorkey-class.md)
