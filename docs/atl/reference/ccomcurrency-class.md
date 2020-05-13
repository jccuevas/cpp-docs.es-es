---
title: Clase CComCurrency
ms.date: 11/04/2016
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
ms.openlocfilehash: 541944e03e9caf6cba15612cf9e7cbbd239555ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327940"
---
# <a name="ccomcurrency-class"></a>Clase CComCurrency

`CComCurrency` tiene métodos y operadores para crear y administrar un objeto CURRENCY.

## <a name="syntax"></a>Sintaxis

```
class CComCurrency
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|El constructor para un objeto `CComCurrency`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Devuelve la dirección de un miembro de datos `m_currency`.|
|[CComCurrency::GetFraction](#getfraction)|Llame a este método para devolver el componente de fracción de un objeto `CComCurrency`.|
|[CComCurrency::GetInteger](#getinteger)|Llame a este método para devolver el componente entero de un objeto `CComCurrency`.|
|[CComCurrency::Round](#round)|Llame a este método para redondear un objeto `CComCurrency` al valor entero más cercano.|
|[CComCurrency::SetFraction](#setfraction)|Llame a este método para establecer el componente de fracción de un objeto `CComCurrency`.|
|[CComCurrency::SetInteger](#setinteger)|Llame a este método para establecer el componente entero de un objeto `CComCurrency`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCurrency::operador -](#operator_-)|Este operador se usa para restar en un objeto `CComCurrency`.|
|[CComCurrency::operador !-](#operator_neq)|Compara dos objetos `CComCurrency` para determinar si no son iguales.|
|[CComCurrency::operador *](#operator_star)|Este operador se usa para multiplicar en un objeto `CComCurrency`.|
|[CComCurrency::operador *-](#operator_star_eq)|Este operador se usa para multiplicar en un objeto `CComCurrency` y asignarle el resultado.|
|[CComCurrency::operador /](#operator_div)|Este operador se usa para dividir en un objeto `CComCurrency`.|
|[CComCurrency::operator /=](#operator_div_eq)|Este operador se utiliza para dividir en un objeto `CComCurrency` y asignarle el resultado.|
|[CComCurrency::operador +](#operator_add)|Este operador se usa para sumar en un objeto `CComCurrency`.|
|[CComCurrency::operador +o](#operator_add_eq)|Este operador se usa para sumar en un objeto `CComCurrency` y asignar el resultado al objeto actual.|
|[CComCurrency::operator <](#operator_lt)|Este operador compara dos objetos `CComCurrency` para determinar el menor.|
|[CComCurrency::operador <?](#operator_lt_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el menor.|
|[CComCurrency::operador ?](#operator_eq)|El operador asigna el objeto `CComCurrency` a un nuevo valor.|
|[CComCurrency::operador --](#operator_-_eq)|Este operador se usa para restar en un objeto `CComCurrency` y asignarle el resultado.|
|[CComCurrency::operador ?](#operator_eq_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales.|
|[CComCurrency::operator >](#operator_gt)|Este operador compara dos objetos `CComCurrency` para determinar el mayor.|
|[CComCurrency::operador >?](#operator_gt_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el mayor.|
|[CComCurrency::operator CURRENCY](#operator_currency)|Convierte un objeto CURRENCY.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|La variable CURRENCY creada por la instancia de clase.|

## <a name="remarks"></a>Observaciones

`CComCurrency` es un contenedor para el tipo de datos CURRENCY. CURRENCY se implementa como un valor entero de 8 bytes de dos complementos escalado por 10.000. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El tipo de datos CURRENCY es muy útil para cálculos monetarios o para los cálculos de punto fijo, donde la precisión es importante.

El `CComCurrency` contenedor implementa operaciones aritméticas, de asignación y de comparación para este tipo de punto fijo. Las aplicaciones compatibles se han seleccionado para controlar los errores de redondeo que se pueden producir durante los cálculos de punto fijo.

El objeto `CComCurrency` da acceso a los números situados a ambos lados del separador decimal en forma de dos componentes: un componente de número entero que almacena el valor situado a la izquierda del separador decimal y un componente de fracción que almacena el valor situado a la derecha del separador decimal. El componente de fracción se almacena internamente como un valor entero entre -9.999 (CY_MIN_FRACTION) y +9.999 (CY_MAX_FRACTION). El método [CComCurrency::GetFraction](#getfraction) devuelve un valor escalado por un factor de 10000 (CY_SCALE).

Al especificar los componentes enteros `CComCurrency` y fraccionarios de un objeto, recuerde que el componente fraccionario es un número en el intervalo de 0 a 9999. Esto es importante cuando se trata de una divisa como el dólar estadounidense, que expresa cantidades con solo dos dígitos después del separador decimal. Aunque no se muestren los últimos dos dígitos, se deben tener en cuenta.

|Value|Posibles asignaciones CComCurrency|
|-----------|---------------------------------------|
|$10.50|CComCurrency(10,5000) *o* CComCurrency(10.50)|
|$10.05|CComCurrency(10,500) *o* CComCurrency(10.05)|

Los valores CY_MIN_FRACTION, CY_MAX_FRACTION y CY_SCALE se definen en atlcur.h.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcur.h

## <a name="ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CComCurrency::CComCurrency

El constructor.

```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);
CComCurrency(USHORT usSrc);
CComCurrency(CHAR cSrc);
CComCurrency(DOUBLE dSrc);
CComCurrency(FLOAT fSrc);
CComCurrency(LONG lSrc);
CComCurrency(SHORT sSrc);
CComCurrency(BYTE bSrc);
CComCurrency(LONGLONG nInteger, SHORT nFraction);
explicit CComCurrency(LPDISPATCH pDispSrc);
explicit CComCurrency(const VARIANT& varSrc);
explicit CComCurrency(LPCWSTR szSrc);
explicit CComCurrency(LPCSTR szSrc);
```

### <a name="parameters"></a>Parámetros

*curSrc*<br/>
Objeto `CComCurrency` existente.

*cySrc*<br/>
Variable de tipo CURRENCY.

*bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*<br/>
El valor inicial dado `m_currency`a la variable miembro .

*Csrc*<br/>
Carácter que contiene el valor `m_currency`inicial dado a la variable miembro .

*nEntero*, *nFracción*<br/>
Los componentes enteros y fraccionarios del valor monetario inicial. Consulte la información general de [CComCurrency](../../atl/reference/ccomcurrency-class.md) para obtener más información.

*pDispSrc*<br/>
Un `IDispatch` puntero.

*varSrc*<br/>
Variable de tipo VARIANT. La configuración regional del subproceso actual se utiliza para realizar la conversión.

*szSrc*<br/>
Cadena Unicode o ANSI que contiene el valor inicial. La configuración regional del subproceso actual se utiliza para realizar la conversión.

### <a name="remarks"></a>Observaciones

El constructor establece el valor inicial de [CComCurrency::m_currency](#m_currency)y acepta una amplia gama de tipos de datos, incluidos `CComCurrency` enteros, cadenas, números de punto flotante, variables CURRENCY y otros objetos. Si no se `m_currency` proporciona ningún valor, se establece en 0.

En caso de error, como un desbordamiento, los constructores que carecen `AtlThrow` de una especificación de excepción vacía (**throw()**) llaman con un HRESULT que describe el error.

Cuando utilice valores de punto flotante o doble `CComCurrency(10.50)` para asignar `CComCurrency(10,5000)` un `CComCurrency(10,50)`valor, tenga en cuenta que es equivalente y no .

## <a name="ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CComCurrency::GetCurrencyPtr

Devuelve la dirección de un miembro de datos `m_currency`.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección `m_currency` de un miembro de datos

## <a name="ccomcurrencygetfraction"></a><a name="getfraction"></a>CComCurrency::GetFraction

Llame a este método para devolver `CComCurrency` el componente fraccionario del objeto.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el componente fraccionario del `m_currency` miembro de datos.

### <a name="remarks"></a>Observaciones

El componente fraccionario es un valor entero de 4 dígitos entre -9999 (CY_MIN_FRACTION) y +9999 (CY_MAX_FRACTION). `GetFraction`devuelve este valor escalado en 10000 (CY_SCALE). Los valores de CY_MIN_FRACTION, CY_MAX_FRACTION y CY_SCALE se definen en atlcur.h.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

## <a name="ccomcurrencygetinteger"></a><a name="getinteger"></a>CComCurrency::GetInteger

Llame a este método para `CComCurrency` obtener el componente entero de un objeto.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el componente `m_currency` entero del miembro de datos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

## <a name="ccomcurrencym_currency"></a><a name="m_currency"></a>CComCurrency::m_currency

El miembro de datos CURRENCY.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Observaciones

Este miembro contiene la moneda a la que se accede y se manipula mediante los métodos de esta clase.

## <a name="ccomcurrencyoperator--"></a><a name="operator_-"></a>CComCurrency::operador -

Este operador se usa para restar en un objeto `CComCurrency`.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` .

### <a name="return-value"></a>Valor devuelto

Devuelve `CComCurrency` un objeto que representa el resultado de la resta. En caso de error, como un desbordamiento, `AtlThrow` este operador llama con un HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_neq"></a>CComCurrency::operador !-

Este operador compara dos objetos para la desigualdad.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el elemento que `CComCurrency` se compara no es igual al objeto; de lo contrario, FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star"></a>CComCurrency::operador *

Este operador se usa para multiplicar en un objeto `CComCurrency`.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
El multiplicador.

*Cur*<br/>
El `CComCurrency` objeto utilizado como multiplicador.

### <a name="return-value"></a>Valor devuelto

Devuelve `CComCurrency` un objeto que representa el resultado de la multiplicación. En caso de error, como un desbordamiento, `AtlThrow` este operador llama con un HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CComCurrency::operator\*=

Este operador se usa para multiplicar en un objeto `CComCurrency` y asignarle el resultado.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
El multiplicador.

*Cur*<br/>
El `CComCurrency` objeto utilizado como multiplicador.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CComCurrency` objeto actualizado. En caso de error, como un desbordamiento, `AtlThrow` este operador llama con un HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div"></a>CComCurrency::operador /

Este operador se usa para dividir en un objeto `CComCurrency`.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
Divisor.

### <a name="return-value"></a>Valor devuelto

Devuelve `CComCurrency` un objeto que representa el resultado de la división. Si el divisor es 0, se producirá un error de aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CComCurrency::operador /o

Este operador se utiliza para dividir en un objeto `CComCurrency` y asignarle el resultado.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
Divisor.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CComCurrency` objeto actualizado. Si el divisor es 0, se producirá un error de aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add"></a>CComCurrency::operador +

Este operador se usa para sumar en un objeto `CComCurrency`.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` que se va a agregar al objeto original.

### <a name="return-value"></a>Valor devuelto

Devuelve `CComCurrency` un objeto que representa el resultado de la adición. En caso de error, como un desbordamiento, `AtlThrow` este operador llama con un HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CComCurrency::operador +o

Este operador se usa para sumar en un objeto `CComCurrency` y asignar el resultado al objeto actual.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CComCurrency` objeto actualizado. En caso de error, como un desbordamiento, `AtlThrow` este operador llama con un HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CComCurrency::operator&lt;

Este operador compara dos objetos `CComCurrency` para determinar el menor.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor que el segundo, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CComCurrency::operator&lt;=

Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el menor.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor o igual que el segundo, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq"></a>CComCurrency::operador ?

El operador asigna el objeto `CComCurrency` a un nuevo valor.

```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```

### <a name="parameters"></a>Parámetros

*curSrc*<br/>
Objeto `CComCurrency` .

*cySrc*<br/>
Variable de tipo CURRENCY.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
El valor numérico que `CComCurrency` se va a asignar al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el `CComCurrency` objeto actualizado. En caso de error, como un desbordamiento, `AtlThrow` este operador llama con un HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

## <a name="ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CComCurrency::operador --

Este operador se usa para restar en un objeto `CComCurrency` y asignarle el resultado.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` .

### <a name="return-value"></a>Valor devuelto

Devuelve el `CComCurrency` objeto actualizado. En caso de error, como un desbordamiento, `AtlThrow` este operador llama con un HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CComCurrency::operador ?

Este operador compara dos objetos `CComCurrency` para determinar si son iguales.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
El objeto `CComCurrency` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si los objetos son `m_currency` iguales (es decir, los miembros de datos, tanto enteros como fraccionarios, en ambos objetos tienen el mismo valor), FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CComCurrency::operator&gt;

Este operador compara dos objetos `CComCurrency` para determinar el mayor.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que el segundo, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CComCurrency::operator&gt;=

Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el mayor.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*Cur*<br/>
Objeto `CComCurrency` .

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor o igual que el segundo, FALSE en caso contrario.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

## <a name="ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CComCurrency::operator CURRENCY

Estos operadores se `CComCurrency` utilizan para convertir un objeto a un tipo de datos CURRENCY.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a un objeto CURRENCY.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

## <a name="ccomcurrencyround"></a><a name="round"></a>CComCurrency::Round

Llame a este método para redondear la moneda a un número especificado de decimales.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parámetros

*nDecimals*<br/>
El número de `m_currency` dígitos a los que se redondeará, en el rango de 0 a 4.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

## <a name="ccomcurrencysetfraction"></a><a name="setfraction"></a>CComCurrency::SetFraction

Llame a este método para establecer el componente de fracción de un objeto `CComCurrency`.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parámetros

*nFracción*<br/>
El valor que se asignará al `m_currency` componente fraccionario del miembro de datos. El signo del componente fraccionario debe ser el mismo que el componente entero y el valor debe estar en el intervalo -9999 (CY_MIN_FRACTION) a +9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

## <a name="ccomcurrencysetinteger"></a><a name="setinteger"></a>CComCurrency::SetInteger

Llame a este método para establecer el componente entero de un objeto `CComCurrency`.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parámetros

*nEntero*<br/>
El valor que se asignará al `m_currency` componente entero del miembro de datos. El signo del componente entero debe coincidir con el signo del componente fraccionario existente.

*nInteger* debe estar en el intervalo CY_MIN_INTEGER a CY_MAX_INTEGER inclusive. Estos valores se definen en atlcur.h.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Consulte también

[Clase COleCurrency](../../mfc/reference/colecurrency-class.md)<br/>
[Moneda](/windows/win32/api/wtypes/ns-wtypes-cy~r1)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
