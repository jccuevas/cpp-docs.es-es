---
title: Clase CIPAddressCtrl
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
ms.openlocfilehash: fe8e3109b110c27ab32dc1a4f9a132f1e1c18638
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505817"
---
# <a name="cipaddressctrl-class"></a>Clase CIPAddressCtrl

Proporciona la funcionalidad del control de dirección IP común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Construye un objeto `CIPAddressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Borra el contenido del control de dirección IP.|
|[CIPAddressCtrl::Create](#create)|Crea un control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.|
|[CIPAddressCtrl::CreateEx](#createex)|Crea un control de dirección IP con los estilos extendidos de Windows especificados y lo `CIPAddressCtrl` adjunta a un objeto.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Recupera los valores de dirección de los cuatro campos en el control de dirección IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Determina si todos los campos del control de dirección IP están vacíos.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Establece los valores de dirección de los cuatro campos en el control de dirección IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Establece el foco de teclado en el campo especificado en el control de dirección IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Establece el intervalo del campo especificado en el control de dirección IP.|

## <a name="remarks"></a>Comentarios

Un control de dirección IP, un control similar a un control de edición, le permite escribir y manipular una dirección numérica en formato de protocolo de Internet (IP).

Este control (y, por `CIPAddressCtrl` lo tanto, la clase) solo está disponible para los programas que se ejecutan en Microsoft Internet Explorer 4,0 y versiones posteriores. También estarán disponibles en versiones futuras de Windows y Windows NT.

Para obtener más información general sobre el control de direcciones IP, consulte [controles de direcciones IP](/windows/win32/Controls/ip-address-controls) en el Windows SDK.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CIPAddressCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="cipaddressctrl"></a>  CIPAddressCtrl::CIPAddressCtrl

Crea un objeto `CIPAddressCtrl`.

```
CIPAddressCtrl();
```

##  <a name="clearaddress"></a>  CIPAddressCtrl::ClearAddress

Borra el contenido del control de dirección IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_CLEARADDRESS](/windows/win32/Controls/ipm-clearaddress), tal y como se describe en el Windows SDK.

##  <a name="create"></a>  CIPAddressCtrl::Create

Crea un control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el estilo WS_CHILD porque el control debe ser una ventana secundaria. Consulte [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK para obtener una lista de los estilos de Windows.

*rect*<br/>
Referencia al tamaño y la posición del control de dirección IP. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) .

*pParentWnd*<br/>
Puntero a la ventana primaria del control de dirección IP. No debe ser NULL.

*nID*<br/>
IDENTIFICADOR del control de dirección IP.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Un `CIPAddressCtrl` objeto se crea en dos pasos.

1. Llame al constructor, que crea el `CIPAddressCtrl` objeto.

1. Llame `Create`a, que crea el control de dirección IP.

Si desea utilizar estilos extendidos de Windows con el control, llame a [CreateEx](#createex) en lugar `Create`de a.

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

Llame a esta función para crear un control (una ventana secundaria) y asociarlo `CIPAddressCtrl` al objeto.

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
Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el estilo WS_CHILD porque el control debe ser una ventana secundaria. Consulte [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww) en el Windows SDK para obtener una lista de los estilos de Windows.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar los estilos extendidos de Windows, que especifica el **WS_EX_** de estilo extendido de Windows.

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

Recupera los valores de dirección de los cuatro campos en el control de dirección IP.

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
Una referencia al valor del campo 0 desde una dirección IP empaquetada.

*nField1*<br/>
Referencia al valor del campo 1 de una dirección IP empaquetada.

*nField2*<br/>
Referencia al valor del campo 2 de una dirección IP empaquetada.

*nField3*<br/>
Referencia al valor del campo 3 de una dirección IP empaquetada.

*dwAddress*<br/>
Referencia a la dirección de un valor DWORD que recibe la dirección IP. Vea la **sección Comentarios** para obtener una tabla que muestra cómo se rellena *dwAddress* .

### <a name="return-value"></a>Valor devuelto

El número de campos que no están en blanco en el control de dirección IP.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_GETADDRESS](/windows/win32/Controls/ipm-getaddress), tal y como se describe en el Windows SDK. En el primer prototipo anterior, los números de los campos 0 a 3 del control, que se leen de izquierda a derecha, respectivamente, rellenan los cuatro parámetros. En el segundo prototipo anterior, *dwAddress* se rellena como se indica a continuación.

|Campo|Bits que contiene el valor del campo|
|-----------|-------------------------------------|
|0|de 24 a 31|
|1|de 16 a 23|
|2|de 8 a 15|
|3|de 0 a 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

Determina si todos los campos del control de dirección IP están vacíos.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si todos los campos de control de dirección IP están vacíos; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_ISBLANK](/windows/win32/Controls/ipm-isblank), tal y como se describe en el Windows SDK.

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

Establece los valores de dirección de los cuatro campos en el control de dirección IP.

```
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
Valor del campo 1 de una dirección IP empaquetada.

*nField2*<br/>
El valor del campo 2 de una dirección IP empaquetada.

*nField3*<br/>
El valor del campo 3 de una dirección IP empaquetada.

*dwAddress*<br/>
Valor DWORD que contiene la nueva dirección IP. Vea la **sección Comentarios** para obtener una tabla que muestra cómo se rellena el valor DWORD.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETADDRESS](/windows/win32/Controls/ipm-setaddress), tal y como se describe en el Windows SDK. En el primer prototipo anterior, los números de los campos 0 a 3 del control, que se leen de izquierda a derecha, respectivamente, rellenan los cuatro parámetros. En el segundo prototipo anterior, *dwAddress* se rellena como se indica a continuación.

|Campo|Bits que contiene el valor del campo|
|-----------|-------------------------------------|
|0|de 24 a 31|
|1|de 16 a 23|
|2|de 8 a 15|
|3|de 0 a 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

Establece el foco de teclado en el campo especificado en el control de dirección IP.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parámetros

*nField*<br/>
Índice de campo basado en cero en el que se debe establecer el foco. Si este valor es mayor que el número de campos, el foco se establece en el primer campo en blanco. Si todos los campos no están en blanco, el foco se establece en el primer campo.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETFOCUS](/windows/win32/Controls/ipm-setfocus), tal y como se describe en el Windows SDK.

##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange

Establece el intervalo del campo especificado en el control de dirección IP.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parámetros

*nField*<br/>
Índice de campo basado en cero al que se aplicará el intervalo.

*nLower*<br/>
Referencia a un entero que recibe el límite inferior del campo especificado en este control de dirección IP.

*nUpper*<br/>
Referencia a un entero que recibe el límite superior del campo especificado en este control de dirección IP.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETRANGE](/windows/win32/Controls/ipm-setrange), tal y como se describe en el Windows SDK. Use los dos parámetros, *nLower* y *nUpper*, para indicar los límites inferior y superior del campo, en lugar del parámetro *wRange* que se usa con el mensaje de Win32.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
