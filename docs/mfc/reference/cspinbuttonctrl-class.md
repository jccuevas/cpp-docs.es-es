---
title: CSpinButtonCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::CSpinButtonCtrl
- AFXCMN/CSpinButtonCtrl::Create
- AFXCMN/CSpinButtonCtrl::CreateEx
- AFXCMN/CSpinButtonCtrl::GetAccel
- AFXCMN/CSpinButtonCtrl::GetBase
- AFXCMN/CSpinButtonCtrl::GetBuddy
- AFXCMN/CSpinButtonCtrl::GetPos
- AFXCMN/CSpinButtonCtrl::GetRange
- AFXCMN/CSpinButtonCtrl::SetAccel
- AFXCMN/CSpinButtonCtrl::SetBase
- AFXCMN/CSpinButtonCtrl::SetBuddy
- AFXCMN/CSpinButtonCtrl::SetPos
- AFXCMN/CSpinButtonCtrl::SetRange
helpviewer_keywords:
- CSpinButtonCtrl [MFC], CSpinButtonCtrl
- CSpinButtonCtrl [MFC], Create
- CSpinButtonCtrl [MFC], CreateEx
- CSpinButtonCtrl [MFC], GetAccel
- CSpinButtonCtrl [MFC], GetBase
- CSpinButtonCtrl [MFC], GetBuddy
- CSpinButtonCtrl [MFC], GetPos
- CSpinButtonCtrl [MFC], GetRange
- CSpinButtonCtrl [MFC], SetAccel
- CSpinButtonCtrl [MFC], SetBase
- CSpinButtonCtrl [MFC], SetBuddy
- CSpinButtonCtrl [MFC], SetPos
- CSpinButtonCtrl [MFC], SetRange
ms.assetid: 509bfd76-1c5a-4af6-973f-e133c0b87734
ms.openlocfilehash: 4230d43bad8bcc15bcb26aaf0357e70216909ba1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318125"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl (clase)

Proporciona la funcionalidad del control de botón de número común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Construye un objeto `CSpinButtonCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSpinButtonCtrl::Crear](#create)|Crea un control de botón de `CSpinButtonCtrl` giro y lo adjunta a un objeto.|
|[CSpinButtonCtrl::CreateEx](#createex)|Crea un control de botón de giro con los `CSpinButtonCtrl` estilos extendidos de Windows especificados y lo asocia a un objeto.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Recupera información de aceleración para un control de botón de giro.|
|[CSpinButtonCtrl::GetBase](#getbase)|Recupera la base actual para un control de botón de giro.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Recupera un puntero a la ventana de compañero actual.|
|[CSpinButtonCtrl::GetPos](#getpos)|Recupera la posición actual de un control de botón de giro.|
|[CSpinButtonCtrl::GetRange](#getrange)|Recupera los límites superior e inferior (rango) para un control de botón de giro.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Establece la aceleración de un control de botón de giro.|
|[CSpinButtonCtrl::SetBase](#setbase)|Establece la base para un control de botón de giro.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Establece la ventana de compañero para un control de botón de giro.|
|[CSpinButtonCtrl::SetPos](#setpos)|Establece la posición actual del control.|
|[CSpinButtonCtrl::SetRange](#setrange)|Establece los límites superior e inferior (rango) para un control de botón de giro.|

## <a name="remarks"></a>Observaciones

Un "control de botón de giro" (también conocido como control arriba-abajo) es un par de botones de flecha que el usuario puede hacer clic para incrementar o disminuir un valor, como una posición de desplazamiento o un número que se muestra en un control complementario. El valor asociado a un control de botón de giro se denomina su posición actual. Un control de botón de giro se utiliza con mayor frecuencia con un control complementario, llamado una "ventana de amigo".

Este control (y, por lo tanto, la `CSpinButtonCtrl` clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3.51 y versiones posteriores.

Para el usuario, un control de botón de giro y su ventana de amigo a menudo parecen un solo control. Puede especificar que un control de botón de giro se coloque automáticamente junto a su ventana de compañero y que establezca automáticamente el título de la ventana de compañero en su posición actual. Puede utilizar un control de botón de giro con un control de edición para solicitar al usuario la entrada numérica.

Al hacer clic en la flecha hacia arriba, la posición actual se mueve hacia el máximo y al hacer clic en la flecha hacia abajo se mueve la posición actual hacia el mínimo. De forma predeterminada, el mínimo es 100 y el máximo es 0. Cada vez que la configuración mínima es mayor que la configuración máxima (por ejemplo, cuando se utiliza la configuración predeterminada), al hacer clic en la flecha hacia arriba se reduce el valor de posición y al hacer clic en la flecha hacia abajo se aumenta.

Un control de botón de giro sin una ventana de amigo funciona como una especie de barra de desplazamiento simplificada. Por ejemplo, un control de ficha a veces muestra un control de botón de giro para permitir al usuario desplazar fichas adicionales a la vista.

Para obtener más `CSpinButtonCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y uso de [CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="cspinbuttonctrlcreate"></a><a name="create"></a>CSpinButtonCtrl::Crear

Crea un control de botón de `CSpinButtonCtrl` giro y lo adjunta a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de botón de giro. Aplique cualquier combinación de estilos de control de botón de giro al control. Estos estilos se describen en [Estilos](/windows/win32/Controls/up-down-control-styles) de control descendente en el Windows SDK.

*Rect*<br/>
Especifica el tamaño y la posición del control del botón de giro. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [RECT](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Un puntero a la ventana primaria del control `CDialog`de botón de giro, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de botón de giro.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Construir un `CSpinButtonCtrl` objeto en dos pasos Primero, `Create`llamar al constructor y, a continuación, `CSpinButtonCtrl` llamar a , que crea el control de botón de giro y lo adjunta al objeto.

Para crear un control de botón de giro con estilos de `Create`ventana extendidos, llame a [CSpinButtonCtrl::CreateEx](#createex) en lugar de .

## <a name="cspinbuttonctrlcreateex"></a><a name="createex"></a>CSpinButtonCtrl::CreateEx

Crea un control (una ventana secundaria) `CSpinButtonCtrl` y lo asocia con el objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de ventanas extendidas, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de botón de giro. Aplique cualquier combinación de estilos de control de botón de giro al control. Estos estilos se describen en [Estilos](/windows/win32/Controls/up-down-control-styles) de control descendente en el Windows SDK.

*Rect*<br/>
Una referencia a una estructura [RECT](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Utilícelo `CreateEx` en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el WS_EX_ de estilo extendido de Windows.

## <a name="cspinbuttonctrlcspinbuttonctrl"></a><a name="cspinbuttonctrl"></a>CSpinButtonCtrl::CSpinButtonCtrl

Construye un objeto `CSpinButtonCtrl`.

```
CSpinButtonCtrl();
```

## <a name="cspinbuttonctrlgetaccel"></a><a name="getaccel"></a>CSpinButtonCtrl::GetAccel

Recupera información de aceleración para un control de botón de giro.

```
UINT GetAccel(
    int nAccel,
    UDACCEL* pAccel) const;
```

### <a name="parameters"></a>Parámetros

*nAccel*<br/>
Número de elementos de la matriz especificada por *pAccel*.

*pAccel*<br/>
Puntero a una matriz de estructuras [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) que recibe información de aceleración.

### <a name="return-value"></a>Valor devuelto

Número de estructuras aceleradoras recuperadas.

## <a name="cspinbuttonctrlgetbase"></a><a name="getbase"></a>CSpinButtonCtrl::GetBase

Recupera la base actual para un control de botón de giro.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Valor devuelto

El valor base actual.

## <a name="cspinbuttonctrlgetbuddy"></a><a name="getbuddy"></a>CSpinButtonCtrl::GetBuddy

Recupera un puntero a la ventana de compañero actual.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de compañero actual.

## <a name="cspinbuttonctrlgetpos"></a><a name="getpos"></a>CSpinButtonCtrl::GetPos

Recupera la posición actual de un control de botón de giro.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpbError*<br/>
Puntero a un valor booleano que se establece en cero si el valor se recupera correctamente o no es cero si se produce un error. Si este parámetro se establece en NULL, no se notifican errores.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve la posición actual de 16 bits en la palabra de orden bajo. La palabra de orden superior es distinta de cero si se ha producido un error.

La segunda versión devuelve la posición de 32 bits.

### <a name="remarks"></a>Observaciones

Cuando procesa el valor devuelto, el control actualiza su posición actual en función de la leyenda de la ventana de compañero. El control devuelve un error si no hay ninguna ventana de compañero o si el título especifica un valor no válido o fuera de rango.

## <a name="cspinbuttonctrlgetrange"></a><a name="getrange"></a>CSpinButtonCtrl::GetRange

Recupera los límites superior e inferior (rango) para un control de botón de giro.

```
DWORD GetRange() const;

void GetRange(
    int& lower,
    int& upper) const;

void GetRange32(
    int& lower,
    int &upper) const;
```

### <a name="parameters"></a>Parámetros

*Inferior*<br/>
Referencia a un entero que recibe el límite inferior para el control.

*Superior*<br/>
Referencia a un entero que recibe el límite superior del control.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve un valor de 32 bits que contiene los límites superior e inferior. La palabra de orden inferior es el límite superior para el control y la palabra de orden superior es el límite inferior.

### <a name="remarks"></a>Observaciones

La función `GetRange32` miembro recupera el intervalo del control de botón de giro como un entero de 32 bits.

## <a name="cspinbuttonctrlsetaccel"></a><a name="setaccel"></a>CSpinButtonCtrl::SetAccel

Establece la aceleración de un control de botón de giro.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parámetros

*nAccel*<br/>
Número de estructuras [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) especificadas por *pAccel*.

*pAccel*<br/>
Puntero a una matriz de estructuras UDACCEL, que contienen información de aceleración. Los elementos deben ordenarse en `nSec` orden ascendente en función del miembro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

## <a name="cspinbuttonctrlsetbase"></a><a name="setbase"></a>CSpinButtonCtrl::SetBase

Establece la base para un control de botón de giro.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parámetros

*nBase*<br/>
Nuevo valor base para el control. Puede ser 10 para decimal o 16 para hexadecimal.

### <a name="return-value"></a>Valor devuelto

El valor base anterior si se realiza correctamente, o cero si se proporciona una base no válida.

### <a name="remarks"></a>Observaciones

El valor base determina si la ventana de compañero muestra números en dígitos decimales o hexadecimales. Los números hexadecimales siempre no están firmados; los números decimales están firmados.

## <a name="cspinbuttonctrlsetbuddy"></a><a name="setbuddy"></a>CSpinButtonCtrl::SetBuddy

Establece la ventana de compañero para un control de botón de giro.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parámetros

*pWndBuddy*<br/>
Puntero a la nueva ventana de amigo.

### <a name="return-value"></a>Valor devuelto

Un puntero a la ventana de compañero anterior.

### <a name="remarks"></a>Observaciones

Un control de giro casi siempre está asociado a otra ventana, como un control de edición, que muestra algún contenido. Esta otra ventana se llama el "compañero" del control de giro.

## <a name="cspinbuttonctrlsetpos"></a><a name="setpos"></a>CSpinButtonCtrl::SetPos

Establece la posición actual de un control de botón de giro.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parámetros

*Fnco*<br/>
Nueva posición para el control. Este valor debe estar en el intervalo especificado por los límites superior e inferior del control.

### <a name="return-value"></a>Valor devuelto

La posición anterior (precisión de `SetPos`16 bits para `SetPos32`, precisión de 32 bits para ).

### <a name="remarks"></a>Observaciones

`SetPos32`establece la posición de 32 bits.

## <a name="cspinbuttonctrlsetrange"></a><a name="setrange"></a>CSpinButtonCtrl::SetRange

Establece los límites superior e inferior (rango) para un control de botón de giro.

```
void SetRange(
    short nLower,
    short nUpper);

void SetRange32(
    int nLower,
    int nUpper);
```

### <a name="parameters"></a>Parámetros

*nLower* y *nUpper*<br/>
Límites superior e inferior para el control. Para `SetRange`, ninguno de los límites puede ser mayor que UD_MAXVAL o menor que UD_MINVAL; además, la diferencia entre los dos límites no puede superar UD_MAXVAL. `SetRange32`no impone restricciones a los límites; utilizar cualquier entero.

### <a name="remarks"></a>Observaciones

La función `SetRange32` miembro establece el rango de 32 bits para el control de botón de giro.

> [!NOTE]
> El rango predeterminado para el botón de giro tiene el máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba disminuirá la posición y al hacer clic en la flecha hacia abajo se aumentará. Utilícelo `CSpinButtonCtrl::SetRange` para ajustar estos valores.

## <a name="see-also"></a>Consulte también

[Ejemplo cmNCTRL2 de MFC](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CSliderCtrl](../../mfc/reference/csliderctrl-class.md)
