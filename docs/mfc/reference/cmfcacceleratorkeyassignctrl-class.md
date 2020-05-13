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
ms.openlocfilehash: 2021a2069885c6314859a65d528cf03712c524b6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751735"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Clase CMFCAcceleratorKeyAssignCtrl

La `CMFCAcceleratorKeyAssignCtrl` clase extiende la [clase CEdit](../../mfc/reference/cedit-class.md) para admitir botones de sistema adicionales como ALT, CONTROL y SHIFT.

## <a name="syntax"></a>Sintaxis

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Construye un objeto `CMFCAcceleratorKeyAssignCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Recupera la estructura `ACCEL` para una tecla de método abreviado pulsada en el objeto `CMFCAcceleratorKeyAssignCtrl`.|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Determina si se ha definido una tecla de método abreviado.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Utilizado por la clase [CWinApp](../../mfc/reference/cwinapp-class.md) para traducir mensajes de ventana antes de que se distribuyen a la [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) y [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) funciones de Windows. (Invalida [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)).|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Restablece la tecla de método abreviado.|

## <a name="remarks"></a>Observaciones

Esta clase extiende la funcionalidad de la clase `CEdit` ofreciendo compatibilidad con teclas de método abreviado, también conocido como teclas de aceleración. La `CMFCAcceleratorKeyAssignCtrl` clase funciona como una [clase CEdit](../../mfc/reference/cedit-class.md) y también puede reconocer botones del sistema.

Esta clase asigna combinaciones de teclas físicas de método abreviado a valores de cadena. Por ejemplo, suponga que la combinación de teclas ALT + B se asigna a la cadena "Alt + B". Cuando el usuario presione esta combinación de teclas en un objeto `CMFCAcceleratorKeyAssignCtrl`, se le mostrará "Alt + B". Para obtener más información acerca de la asignación entre las teclas de método abreviado y un formato de cadena, vea [CMFCAcceleratorKey (Clase)](../../mfc/reference/cmfcacceleratorkey-class.md).

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

**Encabezado:** afxacceleratorkeyassignctrl.h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Construye un [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel

Recupera la `ACCEL` estructura de una tecla de método abreviado presionada en el [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Valor devuelto

Estructura `ACCEL` que describe la tecla de método abreviado.

### <a name="remarks"></a>Observaciones

Utilice esta función `ACCEL` para recuperar la estructura de `CMFCAcceleratorKeyAssignCtrl` una tecla de método abreviado que el usuario introdujo en el objeto.

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Determina si se ha definido una tecla de método abreviado en el [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objeto.

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el usuario ya ha presionado una combinación válida de teclas que definen una tecla de método abreviado; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Utilice esta función para determinar si el `CMFCAcceleratorKeyAssignCtrl` usuario ha introducido una tecla de método abreviado válida en el objeto. Si existe una tecla de método abreviado, puede usar [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) método para obtener la `ACCEL` estructura asociada a esta tecla de método abreviado.

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Para obtener más información, vea el código fuente ubicado en la carpeta **VC\\atlmfc\\src\\mfc** de la instalación de Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parámetros

[en] *pMsg*<br/>

### <a name="return-value"></a>Valor devuelto

### <a name="remarks"></a>Observaciones

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey

Restablece la tecla de método abreviado.

```cpp
void ResetKey();
```

### <a name="remarks"></a>Observaciones

La función borra el texto del control de edición. Esto incluye las teclas de método abreviado que el usuario ha presionado.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clases](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey (clase)](../../mfc/reference/cmfcacceleratorkey-class.md)
