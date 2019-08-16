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
ms.openlocfilehash: 11463b7113876abdf0743b9f8c7df373fadd99ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497288"
---
# <a name="ccomcurrency-class"></a>Clase CComCurrency

`CComCurrency` tiene métodos y operadores para crear y administrar un objeto CURRENCY.

## <a name="syntax"></a>Sintaxis

```
class CComCurrency
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|El constructor para un objeto `CComCurrency`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Devuelve la dirección de un miembro de datos `m_currency`.|
|[CComCurrency::GetFraction](#getfraction)|Llame a este método para devolver el componente de fracción de un objeto `CComCurrency`.|
|[CComCurrency::GetInteger](#getinteger)|Llame a este método para devolver el componente entero de un objeto `CComCurrency`.|
|[CComCurrency::Round](#round)|Llame a este método para redondear un objeto `CComCurrency` al valor entero más cercano.|
|[CComCurrency::SetFraction](#setfraction)|Llame a este método para establecer el componente de fracción de un objeto `CComCurrency`.|
|[CComCurrency::SetInteger](#setinteger)|Llame a este método para establecer el componente entero de un objeto `CComCurrency`.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCurrency:: Operator-](#operator_-)|Este operador se usa para restar en un objeto `CComCurrency`.|
|[CComCurrency:: Operator! =](#operator_neq)|Compara dos objetos `CComCurrency` para determinar si no son iguales.|
|[CComCurrency:: Operator *](#operator_star)|Este operador se usa para multiplicar en un objeto `CComCurrency`.|
|[CComCurrency::operator *=](#operator_star_eq)|Este operador se usa para multiplicar en un objeto `CComCurrency` y asignarle el resultado.|
|[CComCurrency::operator /](#operator_div)|Este operador se usa para dividir en un objeto `CComCurrency`.|
|[CComCurrency::operator /=](#operator_div_eq)|Este operador se utiliza para dividir en un objeto `CComCurrency` y asignarle el resultado.|
|[CComCurrency:: Operator +](#operator_add)|Este operador se usa para sumar en un objeto `CComCurrency`.|
|[CComCurrency::operator +=](#operator_add_eq)|Este operador se usa para sumar en un objeto `CComCurrency` y asignar el resultado al objeto actual.|
|[CComCurrency:: Operator <](#operator_lt)|Este operador compara dos objetos `CComCurrency` para determinar el menor.|
|[CComCurrency:: Operator < =](#operator_lt_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el menor.|
|[CComCurrency::operator =](#operator_eq)|El operador asigna el objeto `CComCurrency` a un nuevo valor.|
|[CComCurrency:: Operator-=](#operator_-_eq)|Este operador se usa para restar en un objeto `CComCurrency` y asignarle el resultado.|
|[CComCurrency::operator ==](#operator_eq_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales.|
|[CComCurrency:: Operator >](#operator_gt)|Este operador compara dos objetos `CComCurrency` para determinar el mayor.|
|[CComCurrency:: Operator > =](#operator_gt_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el mayor.|
|[CComCurrency:: Operator CURRENCY](#operator_currency)|Convierte un objeto CURRENCY.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|La variable de moneda creada por la instancia de clase.|

## <a name="remarks"></a>Comentarios

`CComCurrency`es un contenedor para el tipo de datos CURRENCY. CURRENCY se implementa como un valor entero del complemento de dos bytes de 8 bytes escalado por 10.000. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El tipo de datos CURRENCY es muy útil para los cálculos que afectan a Money, o para los cálculos de punto fijo en los que la precisión es importante.

El `CComCurrency` contenedor implementa operaciones aritméticas, de asignación y de comparación para este tipo de punto fijo. Las aplicaciones compatibles se han seleccionado para controlar los errores de redondeo que se pueden producir durante los cálculos de punto fijo.

El objeto `CComCurrency` da acceso a los números situados a ambos lados del separador decimal en forma de dos componentes: un componente de número entero que almacena el valor situado a la izquierda del separador decimal y un componente de fracción que almacena el valor situado a la derecha del separador decimal. El componente fraccionario se almacena internamente como un valor entero entre-9999 (CY_MIN_FRACTION) y + 9999 (CY_MAX_FRACTION). El método [CComCurrency:: GetFraction](#getfraction) devuelve un valor escalado por un factor de 10000 (CY_SCALE).

Al especificar los componentes enteros y fraccionarios de un `CComCurrency` objeto, recuerde que el componente fraccionario es un número comprendido entre 0 y 9999. Esto es importante cuando se trata de una divisa como el dólar estadounidense, que expresa cantidades con solo dos dígitos después del separador decimal. Aunque no se muestren los últimos dos dígitos, se deben tener en cuenta.

|Valor|Posibles asignaciones CComCurrency|
|-----------|---------------------------------------|
|$10.50|CComCurrency (10, 5000) *o* CComCurrency (10,50)|
|$10.05|CComCurrency (10500) *o* CComCurrency (10.05)|

Los valores CY_MIN_FRACTION, CY_MAX_FRACTION y CY_SCALE se definen en atlcur. h.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcur. h

##  <a name="ccomcurrency"></a>  CComCurrency::CComCurrency

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
Valor inicial asignado a la variable `m_currency`de miembro.

*cSrc*<br/>
Carácter que contiene el valor inicial dado a la variable `m_currency`miembro.

*nInteger*, *nFraction*<br/>
Los componentes enteros y fraccionarios del valor monetario inicial. Vea la información general de [CComCurrency](../../atl/reference/ccomcurrency-class.md) para obtener más información.

*pDispSrc*<br/>
Un `IDispatch` puntero.

*varSrc*<br/>
Variable de tipo VARIANT. La configuración regional del subproceso actual se usa para realizar la conversión.

*szSrc*<br/>
Cadena Unicode o ANSI que contiene el valor inicial. La configuración regional del subproceso actual se usa para realizar la conversión.

### <a name="remarks"></a>Comentarios

El constructor establece el valor inicial de [CComCurrency:: m_currency](#m_currency)y acepta una amplia gama de tipos de datos, incluidos enteros, cadenas, números de punto flotante, variables de moneda y otros `CComCurrency` objetos. Si no se proporciona ningún valor `m_currency` , se establece en 0.

En caso de que se produzca un error, como un desbordamiento, los constructores que carecen de una llamada `AtlThrow` de especificación de excepción (**Throw ()** ) vacía con un HRESULT que describe el error.

Al usar valores de punto flotante o valores Double para asignar un valor, tenga `CComCurrency(10.50)` en cuenta que `CComCurrency(10,5000)` es equivalente `CComCurrency(10,50)`a y no a.

##  <a name="getcurrencyptr"></a>  CComCurrency::GetCurrencyPtr

Devuelve la dirección de un miembro de datos `m_currency`.

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve la dirección de un `m_currency` miembro de datos.

##  <a name="getfraction"></a>  CComCurrency::GetFraction

Llame a este método para devolver el componente fraccionario del `CComCurrency` objeto.

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el componente fraccionario del miembro de `m_currency` datos.

### <a name="remarks"></a>Comentarios

El componente fraccionario es un valor entero de 4 dígitos entre-9999 (CY_MIN_FRACTION) y + 9999 (CY_MAX_FRACTION). `GetFraction`devuelve este valor escalado por 10000 (CY_SCALE). Los valores de CY_MIN_FRACTION, CY_MAX_FRACTION y CY_SCALE se definen en atlcur. h.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

##  <a name="getinteger"></a>  CComCurrency::GetInteger

Llame a este método para obtener el componente entero de un `CComCurrency` objeto.

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el componente entero del miembro de `m_currency` datos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

##  <a name="m_currency"></a>  CComCurrency::m_currency

El miembro de datos CURRENCY.

```
CURRENCY m_currency;
```

### <a name="remarks"></a>Comentarios

Este miembro contiene la moneda a la que tienen acceso y manipulan los métodos de esta clase.

##  <a name="operator_-"></a>CComCurrency:: Operator-

Este operador se usa para restar en un objeto `CComCurrency`.

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CComCurrency` objeto que representa el resultado de la resta. En caso de que se produzca un error, como un desbordamiento, este operador `AtlThrow` llama a con un valor HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

##  <a name="operator_neq"></a>CComCurrency:: Operator! =

Este operador compara dos objetos para determinar si no son iguales.

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency` que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si el elemento que se va a comparar no es `CComCurrency` igual al objeto; de lo contrario, es false.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

##  <a name="operator_star"></a>CComCurrency:: Operator *

Este operador se usa para multiplicar en un objeto `CComCurrency`.

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
Multiplicador.

*cur*<br/>
`CComCurrency` Objeto utilizado como multiplicador.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CComCurrency` objeto que representa el resultado de la multiplicación. En caso de que se produzca un error, como un desbordamiento, este operador `AtlThrow` llama a con un valor HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

##  <a name="operator_star_eq"></a>CComCurrency:: Operator\*=

Este operador se usa para multiplicar en un objeto `CComCurrency` y asignarle el resultado.

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
Multiplicador.

*cur*<br/>
`CComCurrency` Objeto utilizado como multiplicador.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CComCurrency` actualizado. En caso de que se produzca un error, como un desbordamiento, este operador `AtlThrow` llama a con un valor HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

##  <a name="operator_div"></a>  CComCurrency::operator /

Este operador se usa para dividir en un objeto `CComCurrency`.

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
Divisor.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CComCurrency` objeto que representa el resultado de la división. Si el divisor es 0, se producirá un error de aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

##  <a name="operator_div_eq"></a>  CComCurrency::operator /=

Este operador se utiliza para dividir en un objeto `CComCurrency` y asignarle el resultado.

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>Parámetros

*nOperand*<br/>
Divisor.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CComCurrency` actualizado. Si el divisor es 0, se producirá un error de aserción.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

##  <a name="operator_add"></a>CComCurrency:: Operator +

Este operador se usa para sumar en un objeto `CComCurrency`.

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
`CComCurrency` Objeto que se va a agregar al objeto original.

### <a name="return-value"></a>Valor devuelto

Devuelve un `CComCurrency` objeto que representa el resultado de la suma. En caso de que se produzca un error, como un desbordamiento, este operador `AtlThrow` llama a con un valor HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

##  <a name="operator_add_eq"></a>CComCurrency:: Operator + =

Este operador se usa para sumar en un objeto `CComCurrency` y asignar el resultado al objeto actual.

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CComCurrency` actualizado. En caso de que se produzca un error, como un desbordamiento, este operador `AtlThrow` llama a con un valor HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

##  <a name="operator_lt"></a>CComCurrency:: Operator&lt;

Este operador compara dos objetos `CComCurrency` para determinar el menor.

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor que el segundo; de lo contrario, devuelve FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

##  <a name="operator_lt_eq"></a>CComCurrency:: Operator&lt;=

Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el menor.

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es menor o igual que el segundo; de lo contrario, devuelve FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

##  <a name="operator_eq"></a>CComCurrency:: Operator =

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
Objeto `CComCurrency`.

*cySrc*<br/>
Variable de tipo CURRENCY.

*sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc*, *ulSrc*, *dSrc*<br/>
Valor numérico que se va a asignar `CComCurrency` al objeto.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CComCurrency` actualizado. En caso de que se produzca un error, como un desbordamiento, este operador `AtlThrow` llama a con un valor HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

##  <a name="operator_-_eq"></a>CComCurrency:: Operator-=

Este operador se usa para restar en un objeto `CComCurrency` y asignarle el resultado.

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve el objeto `CComCurrency` actualizado. En caso de que se produzca un error, como un desbordamiento, este operador `AtlThrow` llama a con un valor HRESULT que describe el error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

##  <a name="operator_eq_eq"></a>CComCurrency:: Operator = =

Este operador compara dos objetos `CComCurrency` para determinar si son iguales.

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
`CComCurrency` Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los objetos son iguales (es decir, los `m_currency` miembros de datos, tanto enteros como fraccionarios, en ambos objetos tienen el mismo valor); en caso contrario, false.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

##  <a name="operator_gt"></a>CComCurrency:: Operator&gt;

Este operador compara dos objetos `CComCurrency` para determinar el mayor.

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor que el segundo; de lo contrario, devuelve FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

##  <a name="operator_gt_eq"></a>CComCurrency:: Operator&gt;=

Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el mayor.

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>Parámetros

*cur*<br/>
Objeto `CComCurrency`.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si el primer objeto es mayor o igual que el segundo; de lo contrario, devuelve FALSE.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

##  <a name="operator_currency"></a>CComCurrency:: Operator CURRENCY

Estos operadores se utilizan para convertir un `CComCurrency` objeto en un tipo de datos de moneda.

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve una referencia a un objeto CURRENCY.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

##  <a name="round"></a>  CComCurrency::Round

Llame a este método para redondear la moneda a un número especificado de posiciones decimales.

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>Parámetros

*nDecimals*<br/>
Número de dígitos a los que `m_currency` se va a redondear, en el intervalo comprendido entre 0 y 4.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

##  <a name="setfraction"></a>  CComCurrency::SetFraction

Llame a este método para establecer el componente de fracción de un objeto `CComCurrency`.

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>Parámetros

*nFraction*<br/>
Valor que se va a asignar al componente fraccionario del miembro de `m_currency` datos. El signo del componente fraccionario debe ser el mismo que el componente entero y el valor debe estar comprendido entre-9999 (CY_MIN_FRACTION) y + 9999 (CY_MAX_FRACTION).

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

##  <a name="setinteger"></a>  CComCurrency::SetInteger

Llame a este método para establecer el componente entero de un objeto `CComCurrency`.

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>Parámetros

*nInteger*<br/>
Valor que se va a asignar al componente entero del miembro de `m_currency` datos. El signo del componente entero debe coincidir con el signo del componente fraccionario existente.

*nInteger* debe estar en el intervalo comprendido entre CY_MIN_INTEGER y CY_MAX_INTEGER, ambos inclusive. Estos valores se definen en atlcur. h.

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>Vea también

[COleCurrency (clase)](../../mfc/reference/colecurrency-class.md)<br/>
[MONETARIA](/windows/win32/api/wtypes/ns-wtypes-cy)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
