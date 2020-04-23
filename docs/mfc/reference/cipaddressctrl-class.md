---
title: CIPAddressCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CIPAddressCtrl
- AFXCMN/CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::CIPAddressCtrl
- AFXCMN/CIPAddressCtrl::ClearAddress
- AFXCMN/CIPAddressCtrl::Create
- AFXCMN/CIPAddressCtrl::CreateEx
- AFXCMN/CIPAddressCtrl::GetAddress
- AFXCMN/CIPAddressCtrl::IsBlank
- AFXCMN/CIPAddressCtrl::SetAddress
- AFXCMN/CIPAddressCtrl::SetFieldFocus
- AFXCMN/CIPAddressCtrl::SetFieldRange
helpviewer_keywords:
- CIPAddressCtrl [MFC], CIPAddressCtrl
- CIPAddressCtrl [MFC], ClearAddress
- CIPAddressCtrl [MFC], Create
- CIPAddressCtrl [MFC], CreateEx
- CIPAddressCtrl [MFC], GetAddress
- CIPAddressCtrl [MFC], IsBlank
- CIPAddressCtrl [MFC], SetAddress
- CIPAddressCtrl [MFC], SetFieldFocus
- CIPAddressCtrl [MFC], SetFieldRange
ms.assetid: 9764d2f4-cb14-4ba8-b799-7f57a55a47c6
ms.openlocfilehash: 0613dea766b022acf140a82bb4b01784793c2589
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754961"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl (clase)

Proporciona la funcionalidad del control de dirección IP común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Construye un objeto `CIPAddressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Borra el contenido del Control de direcciones IP.|
|[CIPAddressCtrl::Crear](#create)|Crea un control de direcciones `CIPAddressCtrl` IP y lo adjunta a un objeto.|
|[CIPAddressCtrl::CreateEx](#createex)|Crea un control de dirección IP con los estilos `CIPAddressCtrl` extendidos de Windows especificados y lo asocia a un objeto.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Recupera los valores de dirección para los cuatro campos en el control de direcciones IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Determina si todos los campos del control de direcciones IP están vacíos.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Establece los valores de dirección para los cuatro campos en el Control de direcciones IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Establece el foco del teclado en el campo especificado en el Control de direcciones IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Establece el intervalo en el campo especificado en el Control de direcciones IP.|

## <a name="remarks"></a>Observaciones

Un control de dirección IP, un control similar a un control de edición, le permite introducir y manipular una dirección numérica en formato de protocolo de Internet (IP).

Este control (y, por lo tanto, la `CIPAddressCtrl` clase) solo está disponible para los programas que se ejecutan en Microsoft Internet Explorer 4.0 y versiones posteriores. También estarán disponibles en futuras versiones de Windows y Windows NT.

Para obtener más información general sobre el control de direcciones IP, vea [Controles de direcciones IP](/windows/win32/Controls/ip-address-controls) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="cipaddressctrlcipaddressctrl"></a><a name="cipaddressctrl"></a>CIPAddressCtrl::CIPAddressCtrl

Crea un objeto `CIPAddressCtrl` .

```
CIPAddressCtrl();
```

## <a name="cipaddressctrlclearaddress"></a><a name="clearaddress"></a>CIPAddressCtrl::ClearAddress

Borra el contenido del Control de direcciones IP.

```cpp
void ClearAddress();
```

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32 [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress), como se describe en el Windows SDK.

## <a name="cipaddressctrlcreate"></a><a name="create"></a>CIPAddressCtrl::Crear

Crea un control de direcciones `CIPAddressCtrl` IP y lo adjunta a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilo del control de dirección IP. Aplique una combinación de estilos de ventana. Debe incluir el estilo WS_CHILD porque el control debe ser una ventana secundaria. Consulte [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK para obtener una lista de estilos de Windows.

*Rect*<br/>
Una referencia al tamaño y la posición del Control de direcciones IP. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura.

*pParentWnd*<br/>
Un puntero a la ventana primaria del control de dirección IP. No debe ser NULL.

*nID*<br/>
Id. del Control de direcciones IP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Construir un `CIPAddressCtrl` objeto en dos pasos.

1. Llame al constructor, `CIPAddressCtrl` que crea el objeto.

1. Llamada `Create`, que crea el control de dirección IP.

Si desea utilizar estilos de ventanas extendidas `Create`con el control, llame a [CreateEx](#createex) en lugar de .

## <a name="cipaddressctrlcreateex"></a><a name="createex"></a>CIPAddressCtrl::CreateEx

Llame a esta función para crear un control `CIPAddressCtrl` (una ventana secundaria) y asociarlo con el objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Estilo del control de dirección IP. Aplique una combinación de estilos de ventana. Debe incluir el estilo WS_CHILD porque el control debe ser una ventana secundaria. Consulte [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK para obtener una lista de estilos de Windows.

*Rect*<br/>
Una referencia a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

## <a name="cipaddressctrlgetaddress"></a><a name="getaddress"></a>CIPAddressCtrl::GetAddress

Recupera los valores de dirección para los cuatro campos en el control de direcciones IP.

```
int GetAddress(
    BYTE& nField0,
    BYTE& nField1,
    BYTE& nField2,
    BYTE& nField3);

int GetAddress(DWORD& dwAddress);
```

### <a name="parameters"></a>Parámetros

*nField0*<br/>
Una referencia al valor del campo 0 de una dirección IP empaquetada.

*nField1*<br/>
Una referencia al valor del campo 1 de una dirección IP empaquetada.

*nField2*<br/>
Una referencia al valor del campo 2 de una dirección IP empaquetada.

*nField3*<br/>
Una referencia al valor del campo 3 de una dirección IP empaquetada.

*dwAddress*<br/>
Una referencia a la dirección de un valor DWORD que recibe la dirección IP. Consulte **Comentarios** para obtener una tabla que muestra cómo se rellena *dwAddress.*

### <a name="return-value"></a>Valor devuelto

El número de campos no en blanco en el Control de direcciones IP.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del mensaje Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress), como se describe en el Windows SDK. En el primer prototipo anterior, los números de los campos 0 a 3 del control, leídos de izquierda a derecha respectivamente, rellenan los cuatro parámetros. En el segundo prototipo anterior, *dwAddress* se rellena de la siguiente manera.

|Campo|Bits que contienen el valor del campo|
|-----------|-------------------------------------|
|0|24 a 31|
|1|16 a 23|
|2|8 a 15|
|3|0 a 7|

## <a name="cipaddressctrlisblank"></a><a name="isblank"></a>CIPAddressCtrl::IsBlank

Determina si todos los campos del control de direcciones IP están vacíos.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si todos los campos de control de dirección IP están vacíos; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/ipm-isblank)Win32 IPM_ISBLANK , como se describe en el Windows SDK.

## <a name="cipaddressctrlsetaddress"></a><a name="setaddress"></a>CIPAddressCtrl::SetAddress

Establece los valores de dirección para los cuatro campos en el Control de direcciones IP.

```cpp
void SetAddress(
    BYTE nField0,
    BYTE nField1,
    BYTE nField2,
    BYTE nField3);

void SetAddress(DWORD dwAddress);
```

### <a name="parameters"></a>Parámetros

*nField0*<br/>
El valor del campo 0 de una dirección IP empaquetada.

*nField1*<br/>
El valor del campo 1 de una dirección IP empaquetada.

*nField2*<br/>
El valor del campo 2 de una dirección IP empaquetada.

*nField3*<br/>
El valor del campo 3 de una dirección IP empaquetada.

*dwAddress*<br/>
Un valor DWORD que contiene la nueva dirección IP. Consulte **Comentarios** para obtener una tabla que muestra cómo se rellena el valor DWORD.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento de la [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress)de mensaje de Win32 , como se describe en el Windows SDK. En el primer prototipo anterior, los números de los campos 0 a 3 del control, leídos de izquierda a derecha respectivamente, rellenan los cuatro parámetros. En el segundo prototipo anterior, *dwAddress* se rellena de la siguiente manera.

|Campo|Bits que contienen el valor del campo|
|-----------|-------------------------------------|
|0|24 a 31|
|1|16 a 23|
|2|8 a 15|
|3|0 a 7|

## <a name="cipaddressctrlsetfieldfocus"></a><a name="setfieldfocus"></a>CIPAddressCtrl::SetFieldFocus

Establece el foco del teclado en el campo especificado en el Control de direcciones IP.

```cpp
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parámetros

*nField*<br/>
Indice de campo de base cero al que se debe establecer el foco. Si este valor es mayor que el número de campos, el foco se establece en el primer campo en blanco. Si todos los campos no están en blanco, el foco se establece en el primer campo.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje de](/windows/win32/Controls/ipm-setfocus)Win32 IPM_SETFOCUS , como se describe en el Windows SDK.

## <a name="cipaddressctrlsetfieldrange"></a><a name="setfieldrange"></a>CIPAddressCtrl::SetFieldRange

Establece el intervalo en el campo especificado en el Control de direcciones IP.

```cpp
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parámetros

*nField*<br/>
Indice de campo de base cero al que se aplicará el rango.

*nLower*<br/>
Una referencia a un entero que recibe el límite inferior del campo especificado en este control de dirección IP.

*nUpper*<br/>
Una referencia a un entero que recibe el límite superior del campo especificado en este control de dirección IP.

### <a name="remarks"></a>Observaciones

Esta función miembro implementa el comportamiento del [mensaje Win32 IPM_SETRANGE](/windows/win32/Controls/ipm-setrange), como se describe en el Windows SDK. Utilice los dos parámetros, *nLower* y *nUpper*, para indicar los límites inferior y superior del campo, en lugar del parámetro *wRange* utilizado con el mensaje Win32.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
