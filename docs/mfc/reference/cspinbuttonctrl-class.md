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
ms.openlocfilehash: c167745eed45b7081e62a2c3be225a33e7ee0520
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502441"
---
# <a name="cspinbuttonctrl-class"></a>CSpinButtonCtrl (clase)

Proporciona la funcionalidad del control de botón de número común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CSpinButtonCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSpinButtonCtrl::CSpinButtonCtrl](#cspinbuttonctrl)|Construye un objeto `CSpinButtonCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSpinButtonCtrl::Create](#create)|Crea un control de botón de número y lo adjunta a `CSpinButtonCtrl` un objeto.|
|[CSpinButtonCtrl::CreateEx](#createex)|Crea un control de botón de número con los estilos extendidos de Windows especificados y `CSpinButtonCtrl` lo adjunta a un objeto.|
|[CSpinButtonCtrl::GetAccel](#getaccel)|Recupera información de aceleración para un control de botón de número.|
|[CSpinButtonCtrl::GetBase](#getbase)|Recupera la base actual para un control de botón de número.|
|[CSpinButtonCtrl::GetBuddy](#getbuddy)|Recupera un puntero a la ventana relacionada actual.|
|[CSpinButtonCtrl::GetPos](#getpos)|Recupera la posición actual de un control de botón de número.|
|[CSpinButtonCtrl::GetRange](#getrange)|Recupera los límites superior e inferior (intervalo) de un control de botón de número.|
|[CSpinButtonCtrl::SetAccel](#setaccel)|Establece la aceleración para un control de botón de número.|
|[CSpinButtonCtrl::SetBase](#setbase)|Establece la base para un control de botón de número.|
|[CSpinButtonCtrl::SetBuddy](#setbuddy)|Establece la ventana relacionada para un control de botón de número.|
|[CSpinButtonCtrl::SetPos](#setpos)|Establece la posición actual del control.|
|[CSpinButtonCtrl::SetRange](#setrange)|Establece los límites superior e inferior (intervalo) de un control de botón de número.|

## <a name="remarks"></a>Comentarios

Un "control de botón de número" (también conocido como control de flechas) es un par de botones de flecha en los que el usuario puede hacer clic para aumentar o disminuir un valor, como una posición de desplazamiento o un número que se muestra en un control complementario. El valor asociado a un control de botón de número se denomina su posición actual. Un control de botón de número se usa con mayor frecuencia con un control complementario, denominado "ventana relacionada".

Este control (y, por `CSpinButtonCtrl` lo tanto, la clase) solo está disponible para programas que se ejecutan en Windows 95/98 y Windows NT versión 3,51 y versiones posteriores.

Para el usuario, un control de botón de número y su ventana relacionada suelen tener el mismo control. Puede especificar que un control de botón de número se coloque automáticamente junto a su ventana relacionada y que establezca automáticamente el título de la ventana relacionada en su posición actual. Puede usar un control de botón de número con un control de edición para solicitar al usuario una entrada numérica.

Al hacer clic en la flecha arriba, se mueve la posición actual hacia el máximo y al hacer clic en la flecha hacia abajo se mueve la posición actual hacia el mínimo. De forma predeterminada, el mínimo es 100 y el máximo es 0. Siempre que el valor mínimo sea mayor que el valor máximo (por ejemplo, cuando se utiliza la configuración predeterminada), al hacer clic en la flecha hacia arriba se reduce el valor de posición y, al hacer clic en la flecha hacia abajo, se aumenta.

Un control de botón de número sin una ventana relacionada funciona como un tipo de barra de desplazamiento simplificada. Por ejemplo, un control de ficha a veces muestra un control de botón de número para permitir al usuario desplazarse por las pestañas adicionales a la vista.

Para obtener más información sobre `CSpinButtonCtrl`el uso de, vea [controles](../../mfc/controls-mfc.md) y [usar CSpinButtonCtrl](../../mfc/using-cspinbuttonctrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSpinButtonCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="create"></a>  CSpinButtonCtrl::Create

Crea un control de botón de número y lo adjunta a `CSpinButtonCtrl` un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de botón de número. Aplique cualquier combinación de estilos de control de botón de número al control. Estos estilos se describen en los [estilos de control de arriba](/windows/win32/Controls/up-down-control-styles) en el Windows SDK.

*rect*<br/>
Especifica el tamaño y la posición del control de botón de número. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\))

*pParentWnd*<br/>
Puntero a la ventana primaria del control de botón de número, normalmente `CDialog`una. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de botón de número.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Primero se construye `CSpinButtonCtrl` un objeto en dos pasos, se llama al constructor y, a `Create`continuación, se llama a, que crea el control de botón de `CSpinButtonCtrl` número y lo adjunta al objeto.

Para crear un control de botón de número con estilos de ventana extendidos, llame a [CSpinButtonCtrl:: CreateEx](#createex) en lugar de `Create`a.

##  <a name="createex"></a>  CSpinButtonCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia al `CSpinButtonCtrl` objeto.

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
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de botón de número. Aplique cualquier combinación de estilos de control de botón de número al control. Estos estilos se describen en los [estilos de control de arriba](/windows/win32/Controls/up-down-control-styles) en el Windows SDK.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar los estilos extendidos de Windows, que especifica el WS_EX_ de estilo extendido de Windows.

##  <a name="cspinbuttonctrl"></a>  CSpinButtonCtrl::CSpinButtonCtrl

Construye un objeto `CSpinButtonCtrl`.

```
CSpinButtonCtrl();
```

##  <a name="getaccel"></a>  CSpinButtonCtrl::GetAccel

Recupera información de aceleración para un control de botón de número.

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

Número de estructuras de acelerador recuperadas.

##  <a name="getbase"></a>  CSpinButtonCtrl::GetBase

Recupera la base actual para un control de botón de número.

```
UINT GetBase() const;
```

### <a name="return-value"></a>Valor devuelto

Valor base actual.

##  <a name="getbuddy"></a>  CSpinButtonCtrl::GetBuddy

Recupera un puntero a la ventana relacionada actual.

```
CWnd* GetBuddy() const;
```

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana relacionada actual.

##  <a name="getpos"></a>  CSpinButtonCtrl::GetPos

Recupera la posición actual de un control de botón de número.

```
int GetPos() const;  int GetPos32(LPBOOL lpbError = NULL) const;
```

### <a name="parameters"></a>Parámetros

*lpbError*<br/>
Un puntero a un valor booleano que se establece en cero si el valor se recupera correctamente o es distinto de cero si se produce un error. Si este parámetro se establece en NULL, no se registran los errores.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve la posición actual de 16 bits en la palabra de orden inferior. La palabra de orden superior es distinto de cero si se produjo un error.

La segunda versión devuelve la posición de 32 bits.

### <a name="remarks"></a>Comentarios

Cuando procesa el valor devuelto, el control actualiza su posición actual en función del título de la ventana relacionada. El control devuelve un error si no hay ninguna ventana relacionada o si el título especifica un valor que no es válido o está fuera del intervalo.

##  <a name="getrange"></a>  CSpinButtonCtrl::GetRange

Recupera los límites superior e inferior (intervalo) de un control de botón de número.

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

*lower*<br/>
Referencia a un entero que recibe el límite inferior del control.

*upper*<br/>
Referencia a un entero que recibe el límite superior del control.

### <a name="return-value"></a>Valor devuelto

La primera versión devuelve un valor de 32 bits que contiene los límites superior e inferior. La palabra de orden inferior es el límite superior del control y la palabra de orden superior es el límite inferior.

### <a name="remarks"></a>Comentarios

La función `GetRange32` miembro recupera el intervalo del control de botón de número como un entero de 32 bits.

##  <a name="setaccel"></a>  CSpinButtonCtrl::SetAccel

Establece la aceleración para un control de botón de número.

```
BOOL SetAccel(
    int nAccel,
    UDACCEL* pAccel);
```

### <a name="parameters"></a>Parámetros

*nAccel*<br/>
Número de estructuras [UDACCEL](/windows/win32/api/commctrl/ns-commctrl-udaccel) especificadas por *pAccel*.

*pAccel*<br/>
Puntero a una matriz de estructuras UDACCEL que contienen información de aceleración. Los elementos deben ordenarse en orden ascendente según el `nSec` miembro.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

##  <a name="setbase"></a>  CSpinButtonCtrl::SetBase

Establece la base para un control de botón de número.

```
int SetBase(int nBase);
```

### <a name="parameters"></a>Parámetros

*nBase*<br/>
Nuevo valor base para el control. Puede ser 10 para decimal o 16 para hexadecimal.

### <a name="return-value"></a>Valor devuelto

Valor base anterior si se realiza correctamente, o cero si se proporciona una base no válida.

### <a name="remarks"></a>Comentarios

El valor base determina si la ventana relacionada muestra números en dígitos decimales o hexadecimales. Los números hexadecimales siempre están sin signo; los números decimales están firmados.

##  <a name="setbuddy"></a>  CSpinButtonCtrl::SetBuddy

Establece la ventana relacionada para un control de botón de número.

```
CWnd* SetBuddy(CWnd* pWndBuddy);
```

### <a name="parameters"></a>Parámetros

*pWndBuddy*<br/>
Puntero a la nueva ventana de Buddy.

### <a name="return-value"></a>Valor devuelto

Puntero a la ventana relacionada anterior.

### <a name="remarks"></a>Comentarios

Un control de número casi siempre está asociado a otra ventana, como un control de edición, que muestra algún contenido. Esta otra ventana se denomina "Buddy" del control de número.

##  <a name="setpos"></a>  CSpinButtonCtrl::SetPos

Establece la posición actual de un control de botón de número.

```
int SetPos(int nPos);
int SetPos32(int nPos);
```

### <a name="parameters"></a>Parámetros

*nPos*<br/>
Nueva posición del control. Este valor debe estar en el intervalo especificado por los límites superior e inferior del control.

### <a name="return-value"></a>Valor devuelto

Posición anterior (precisión de 16 bits para `SetPos`, precisión de 32 bits para `SetPos32`).

### <a name="remarks"></a>Comentarios

`SetPos32`establece la posición de 32 bits.

##  <a name="setrange"></a>  CSpinButtonCtrl::SetRange

Establece los límites superior e inferior (intervalo) de un control de botón de número.

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
Límites superior e inferior del control. Para `SetRange`, ningún límite puede ser mayor que UD_MAXVAL o menor que UD_MINVAL; además, la diferencia entre los dos límites no puede superar UD_MAXVAL. `SetRange32`no impone restricciones en los límites; use cualquier entero.

### <a name="remarks"></a>Comentarios

La función `SetRange32` miembro establece el intervalo de 32 bits para el control de botón de número.

> [!NOTE]
>  El intervalo predeterminado para el botón de número tiene el valor máximo establecido en cero (0) y el mínimo establecido en 100. Dado que el valor máximo es menor que el valor mínimo, al hacer clic en la flecha arriba se reducirá la posición y, al hacer clic en la flecha hacia abajo, se aumentará. Use `CSpinButtonCtrl::SetRange` para ajustar estos valores.

## <a name="see-also"></a>Vea también

[Ejemplo de MFC CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CSliderCtrl (clase)](../../mfc/reference/csliderctrl-class.md)
