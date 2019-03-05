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
ms.openlocfilehash: e569829c100a581e24b5ce05df2f90ac7088024b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266300"
---
# <a name="cipaddressctrl-class"></a>CIPAddressCtrl (clase)

Proporciona la funcionalidad del control de dirección IP común de Windows.

## <a name="syntax"></a>Sintaxis

```
class CIPAddressCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CIPAddressCtrl::CIPAddressCtrl](#cipaddressctrl)|Construye un objeto `CIPAddressCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CIPAddressCtrl::ClearAddress](#clearaddress)|Borra el contenido del Control de dirección IP.|
|[CIPAddressCtrl::Create](#create)|Crea un Control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.|
|[CIPAddressCtrl::CreateEx](#createex)|Crea un control de dirección IP con los estilos extendidos de Windows especificados y lo asocia a un `CIPAddressCtrl` objeto.|
|[CIPAddressCtrl::GetAddress](#getaddress)|Recupera los valores de dirección para los cuatro campos en el Control de dirección IP.|
|[CIPAddressCtrl::IsBlank](#isblank)|Determina si el Control de dirección IP de todos los campos están vacíos.|
|[CIPAddressCtrl::SetAddress](#setaddress)|Establece los valores de dirección para los cuatro campos en el Control de dirección IP.|
|[CIPAddressCtrl::SetFieldFocus](#setfieldfocus)|Establece el foco del teclado en el campo especificado en el Control de dirección IP.|
|[CIPAddressCtrl::SetFieldRange](#setfieldrange)|Establece el intervalo en el campo especificado en el Control de dirección IP.|

## <a name="remarks"></a>Comentarios

Un control de dirección IP, un control similar a un control de edición, le permite escribir y manipular una dirección numérica en formato de protocolo de Internet (IP).

Este control (y, por tanto, la `CIPAddressCtrl` clase) solo está disponible para programas que se ejecutan en Microsoft Internet Explorer 4.0 y versiones posteriores. También estarán disponibles en versiones futuras de Windows y Windows NT.

Para obtener información general sobre el Control de dirección IP, consulte [controles de dirección IP](/windows/desktop/Controls/ip-address-controls) en el SDK de Windows.

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

Borra el contenido del Control de dirección IP.

```
void ClearAddress();
```

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_CLEARADDRESS](/windows/desktop/Controls/ipm-clearaddress), tal y como se describe en el SDK de Windows.

##  <a name="create"></a>  CIPAddressCtrl::Create

Crea un Control de dirección IP y lo adjunta a un `CIPAddressCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el estilo WS_CHILD porque el control debe ser una ventana secundaria. Consulte [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) en el SDK de Windows para obtener una lista de los estilos de windows.

*rect*<br/>
Referencia al tamaño y la posición del Control de dirección IP. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura.

*pParentWnd*<br/>
Un puntero a la ventana primaria del Control de dirección IP. No debe ser NULL.

*nID*<br/>
Identificador. del Control de dirección IP

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la inicialización se realizó correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Construir un `CIPAddressCtrl` objeto en dos pasos.

1. Llame al constructor, que crea el `CIPAddressCtrl` objeto.

1. Llamar a `Create`, que crea el Control de dirección IP.

Si desea usar los estilos extendidos de windows con el control, llame a [CreateEx](#createex) en lugar de `Create`.

##  <a name="createex"></a>  CIPAddressCtrl::CreateEx

Llame a esta función para crear un control (una ventana secundaria) y asócielo con el `CIPAddressCtrl` objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de los estilos extendidos de Windows, consulte el *dwExStyle* parámetro [CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) en el SDK de Windows.

*dwStyle*<br/>
Estilo del control de dirección IP. Aplicar una combinación de estilos de ventana. Debe incluir el estilo WS_CHILD porque el control debe ser una ventana secundaria. Consulte [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) en el SDK de Windows para obtener una lista de los estilos de windows.

*rect*<br/>
Una referencia a un [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) estructura que describe el tamaño y posición de la ventana que se creará, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Un puntero a la ventana que es primario del control.

*nID*<br/>
Identificador de ventana secundaria. del control

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar estilos extendidos de Windows, especificados por el prólogo de estilo extendido de Windows **WS_EX_**.

##  <a name="getaddress"></a>  CIPAddressCtrl::GetAddress

Recupera los valores de dirección para los cuatro campos en el Control de dirección IP.

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
Una referencia al valor del campo 1 desde una dirección IP empaquetada.

*nField2*<br/>
Una referencia al valor del campo 2 desde una dirección IP empaquetada.

*nField3*<br/>
Una referencia al valor del campo 3 desde una dirección IP empaquetada.

*dwAddress*<br/>
Una referencia a la dirección de un valor DWORD que recibe la dirección IP. Consulte **comentarios** para una tabla que muestra cómo *dwAddress* se rellena.

### <a name="return-value"></a>Valor devuelto

El número de campos en blanco en el Control de dirección IP.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_GETADDRESS](/windows/desktop/Controls/ipm-getaddress), tal y como se describe en el SDK de Windows. En el primer prototipo, los números de 0 a 3 del control, de los campos de lectura de izquierda a derecha, respectivamente, rellene los cuatro parámetros. En el segundo prototipo anterior, *dwAddress* se rellena como sigue.

|Campo|Que contiene el valor del campo de bits|
|-----------|-------------------------------------|
|0|24 a 31|
|1|16 a 23|
|2|8 a 15|
|3|de 0 a 7|

##  <a name="isblank"></a>  CIPAddressCtrl::IsBlank

Determina si el Control de dirección IP de todos los campos están vacíos.

```
BOOL IsBlank() const;
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si todos los campos de Control de dirección IP están vacíos; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_ISBLANK](/windows/desktop/Controls/ipm-isblank), tal y como se describe en el SDK de Windows.

##  <a name="setaddress"></a>  CIPAddressCtrl::SetAddress

Establece los valores de dirección para los cuatro campos en el Control de dirección IP.

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
El valor del campo 0 desde una dirección IP empaquetado.

*nField1*<br/>
El valor del campo 1 desde una dirección IP empaquetado.

*nField2*<br/>
El valor del campo 2 desde una dirección IP empaquetado.

*nField3*<br/>
El valor del campo 3 desde una dirección IP empaquetado.

*dwAddress*<br/>
Un valor DWORD que contiene la nueva dirección IP. Consulte **comentarios** para una tabla que muestra cómo se rellena el valor DWORD.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETADDRESS](/windows/desktop/Controls/ipm-setaddress), tal y como se describe en el SDK de Windows. En el primer prototipo, los números de 0 a 3 del control, de los campos de lectura de izquierda a derecha, respectivamente, rellene los cuatro parámetros. En el segundo prototipo anterior, *dwAddress* se rellena como sigue.

|Campo|Que contiene el valor del campo de bits|
|-----------|-------------------------------------|
|0|24 a 31|
|1|16 a 23|
|2|8 a 15|
|3|de 0 a 7|

##  <a name="setfieldfocus"></a>  CIPAddressCtrl::SetFieldFocus

Establece el foco del teclado en el campo especificado en el Control de dirección IP.

```
void SetFieldFocus(WORD nField);
```

### <a name="parameters"></a>Parámetros

*nField*<br/>
Índice del campo de base cero en el que se debe establecer el foco. Si este valor es mayor que el número de campos, se establece el foco al primer campo en blanco. Si todos los campos están en blanco, se establece el foco al primer campo.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETFOCUS](/windows/desktop/Controls/ipm-setfocus), tal y como se describe en el SDK de Windows.

##  <a name="setfieldrange"></a>  CIPAddressCtrl::SetFieldRange

Establece el intervalo en el campo especificado en el Control de dirección IP.

```
void SetFieldRange(
    int nField,
    BYTE nLower,
    BYTE nUpper);
```

### <a name="parameters"></a>Parámetros

*nField*<br/>
Índice del campo de base cero al que se aplicará el intervalo.

*nLower*<br/>
Una referencia a un entero que recibir el límite inferior del campo especificado en este Control de dirección IP.

*nUpper*<br/>
Una referencia a un entero que recibir el límite superior del campo especificado en este Control de dirección IP.

### <a name="remarks"></a>Comentarios

Esta función miembro implementa el comportamiento del mensaje de Win32 [IPM_SETRANGE](/windows/desktop/Controls/ipm-setrange), tal y como se describe en el SDK de Windows. Use los dos parámetros, *nLower* y *nUpper*para indicar los límites superiores e inferiores del campo, en lugar de la *wRange* parámetro utilizado con el mensaje de Win32.

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
