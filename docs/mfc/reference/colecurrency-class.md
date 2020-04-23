---
title: Clase COleCurrency
ms.date: 08/29/2019
f1_keywords:
- COleCurrency
- AFXDISP/COleCurrency
- AFXDISP/COleCurrency::COleCurrency
- AFXDISP/COleCurrency::Format
- AFXDISP/COleCurrency::GetStatus
- AFXDISP/COleCurrency::ParseCurrency
- AFXDISP/COleCurrency::SetCurrency
- AFXDISP/COleCurrency::SetStatus
- AFXDISP/COleCurrency::m_cur
- AFXDISP/COleCurrency::m_status
helpviewer_keywords:
- COleCurrency [MFC], COleCurrency
- COleCurrency [MFC], Format
- COleCurrency [MFC], GetStatus
- COleCurrency [MFC], ParseCurrency
- COleCurrency [MFC], SetCurrency
- COleCurrency [MFC], SetStatus
- COleCurrency [MFC], m_cur
- COleCurrency [MFC], m_status
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
ms.openlocfilehash: cc69143101c5d00d4f9a689bd02abdd9596e5b53
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753924"
---
# <a name="colecurrency-class"></a>Clase COleCurrency

Encapsula el tipo de datos `CURRENCY` de la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleCurrency
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Construye un objeto `COleCurrency`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCurrency::Formato](#format)|Genera una representación de `COleCurrency` cadena con formato de un objeto.|
|[COleCurrency::GetStatus](#getstatus)|Obtiene el estado (validez) `COleCurrency` de este objeto.|
|[COleCurrency::ParseCurrency](#parsecurrency)|Lee un valor CURRENCY de una cadena `COleCurrency`y establece el valor de .|
|[COleCurrency::SetCurrency](#setcurrency)|Establece el valor `COleCurrency` de este objeto.|
|[COleCurrency::SetStatus](#setstatus)|Establece el status (validez) para este `COleCurrency` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operador a la operadora de la red](#operator_eq)|Copia `COleCurrency` un valor.|
|[operador +, -](#operator_plus_minus)|Agrega, resta y cambia `COleCurrency` el signo de los valores.|
|[operador +, -](#operator_plus_minus_eq)|Agrega y resta `COleCurrency` un `COleCurrency` valor de este objeto.|
|[operador */](#operator_star)|Escala un `COleCurrency` valor por un valor entero.|
|[operador *, /o](#operator_star_div_eq)|Escala este `COleCurrency` valor por un valor entero.|
|[operador <<](#operator_stream)|Genera un `COleCurrency` valor `CArchive` `CDumpContext`a o .|
|[operador >>](#operator_stream)|Indade `COleCurrency` `CArchive`un objeto desde .|
|[operador CURRENCY](#operator_currency)|Convierte un `COleCurrency` valor en un CURRENCY.|
|[operador, <, <, etc.](#colecurrency_relational_operators)|Compara dos `COleCurrency` valores.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Contiene el CURRENCY subyacente `COleCurrency` para este objeto.|
|[COleCurrency::m_status](#m_status)|Contiene el estado `COleCurrency` de este objeto.|

## <a name="remarks"></a>Observaciones

`COleCurrency`no tiene una clase base.

CURRENCY se implementa como un valor entero de 8 bytes y dos de complemento escalado en 10.000. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El tipo de datos CURRENCY es extremadamente útil para los cálculos que implican dinero, o para cualquier cálculo de punto fijo donde la precisión es importante. Es uno de los tipos `VARIANT` posibles para el tipo de datos de automatización OLE.

`COleCurrency`también implementa algunas operaciones aritméticas básicas para este tipo de punto fijo. Las operaciones admitidas se han seleccionado para controlar los errores de redondeo que se producen durante los cálculos de punto fijo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleCurrency`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

## <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::COleCurrency

Construye un objeto `COleCurrency`.

```
COleCurrency();
COleCurrency(CURRENCY cySrc);
COleCurrency(const COleCurrency& curSrc);
COleCurrency(const VARIANT& varSrc);

COleCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parámetros

*cySrc*<br/>
Un valor CURRENCY que se `COleCurrency` va a copiar en el nuevo objeto.

*curSrc*<br/>
Objeto `COleCurrency` existente que se va `COleCurrency` a copiar en el nuevo objeto.

*varSrc*<br/>
Estructura `VARIANT` de datos existente `COleVariant` (posiblemente un objeto) que se convertirá en `COleCurrency` un valor de moneda (VT_CY) y se copie en el nuevo objeto.

*nUnits*, *nFractionalUnits* Indica las unidades y la parte fraccionaria (en 1/10.000) del valor que se va a copiar en el nuevo `COleCurrency` objeto.

### <a name="remarks"></a>Observaciones

Todos estos constructores `COleCurrency` crean nuevos objetos inicializados en el valor especificado. A continuación se ofrece una breve descripción de cada uno de estos constructores. A menos que se indique `COleCurrency` lo contrario, el estado del nuevo elemento se establece en válido.

- COleCurrency() Construye `COleCurrency` un objeto inicializado en 0 (cero).

- COleCurrency(`cySrc`) Construye `COleCurrency` un objeto a partir de un valor [CURRENCY.](/windows/win32/api/wtypes/ns-wtypes-cy~r1)

- COleCurrency(`curSrc`) Construye `COleCurrency` un objeto `COleCurrency` a partir de un objeto existente. El nuevo objeto tiene el mismo estado que el objeto de origen.

- COleCurrency(`varSrc`) Construye `COleCurrency` un objeto. Intenta convertir [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) una estructura `COleVariant` o objeto VARIANT en un valor de moneda (VT_CY). Si esta conversión se realiza correctamente, el `COleCurrency` valor convertido se copia en el nuevo objeto. Si no es así, `COleCurrency` el valor del objeto se establece en cero (0) y su estado en no válido.

- COleCurrency(`nUnits` `nFractionalUnits`, ) `COleCurrency` Construye un objeto a partir de los componentes numéricos especificados. Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste adecuado en las unidades. Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante valores largos firmados.

Para obtener más información, consulte las entradas [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) y [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

### <a name="example"></a>Ejemplo

En los ejemplos siguientes se muestran los efectos de los constructores de parámetrocero y dos parámetros:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

## <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency::Formato

Llame a esta función miembro para crear una representación con formato del valor de moneda.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indica las marcas para la configuración regional. Sólo el siguiente indicador es relevante para la moneda:

- LOCALE_NOUSEROVERRIDE Utilice la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

*lcid*<br/>
Indica el ID de configuración regional que se usará para la conversión.

### <a name="return-value"></a>Valor devuelto

A `CString` que contiene el valor de moneda con formato.

### <a name="remarks"></a>Observaciones

Da formato al valor mediante las especificaciones de idioma local (id de configuración regional). Un símbolo de moneda no se incluye en el valor devuelto. Si el estado `COleCurrency` de este objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena de retorno se especifica mediante el IDS_INVALID_CURRENCY de recursos de cadena.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

## <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency::GetStatus

Llame a esta función miembro para obtener `COleCurrency` el estado (validez) de un objeto determinado.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado `COleCurrency` de este valor.

### <a name="remarks"></a>Observaciones

El valor devuelto se `CurrencyStatus` define mediante el tipo `COleCurrency` enumerado que se define dentro de la clase.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid`Indica que `COleCurrency` este objeto es válido.

- `COleCurrency::invalid`Indica que `COleCurrency` este objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null`Indica que `COleCurrency` este objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de base de datos de "no tener valor", a diferencia de C++ NULL.)

El estado `COleCurrency` de un objeto no es válido en los siguientes casos:

- Si su valor se establece `COleVariant` a partir de un VARIANT o un valor que no se ha podido convertir a un valor de moneda.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento `+=` durante ** \* **una operación de asignación aritmética, por ejemplo o .

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido mediante [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que pueden establecer el estado en no válido, consulte las siguientes funciones miembro:

- [COleCurrency](#colecurrency)

- [operador a la operadora de la red](#operator_eq)

- [operador + -](#operator_plus_minus)

- [operador +a y -](#operator_plus_minus_eq)

- [operador * /](#operator_star)

- [operador *- y /o](#operator_star_div_eq)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

## <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency::m_cur

La estructura [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) subyacente `COleCurrency` para este objeto.

### <a name="remarks"></a>Observaciones

> [!CAUTION]
> Cambiar el valor `CURRENCY` de la estructura a la que tiene `COleCurrency` acceso el puntero devuelto por esta función cambiará el valor de este objeto. No cambia el estado `COleCurrency` de este objeto.

Para obtener más información, consulte la entrada [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) en el Windows SDK.

## <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency::m_status

El tipo de este miembro de `CurrencyStatus`datos es el `COleCurrency` tipo enumerado, que se define dentro de la clase.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Observaciones

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid`Indica que `COleCurrency` este objeto es válido.

- `COleCurrency::invalid`Indica que `COleCurrency` este objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null`Indica que `COleCurrency` este objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de base de datos de "no tener valor", a diferencia de C++ NULL.)

El estado `COleCurrency` de un objeto no es válido en los siguientes casos:

- Si su valor se establece `COleVariant` a partir de un VARIANT o un valor que no se ha podido convertir a un valor de moneda.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento `+=` durante ** \* **una operación de asignación aritmética, por ejemplo o .

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido mediante [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que pueden establecer el estado en no válido, consulte las siguientes funciones miembro:

- [COleCurrency](#colecurrency)

- [operador a la operadora de la red](#operator_eq)

- [operador +, -](#operator_plus_minus)

- [operador +, -](#operator_plus_minus_eq)

- [operador */](#operator_star)

- [operador *, /o](#operator_star_div_eq)

> [!CAUTION]
> Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones miembro en línea [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para obtener más precauciones con respecto a la configuración explícita de este miembro de datos.

## <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency::operador ?

Estos operadores de asignación sobrecargados `COleCurrency` copian el valor de la moneda de origen en este objeto.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Observaciones

A continuación se ofrece una breve descripción de cada operador:

- **Operador (** `cySrc` **)** El `CURRENCY` valor se copia `COleCurrency` en el objeto y su estado se establece en válido.

- **Operador (** `curSrc` **)** El valor y el estado `COleCurrency` del operando, un `COleCurrency` objeto existente se copian en este objeto.

- **operador (** *varSrc* **)** Si la conversión `VARIANT` del valor (o [cOleVariant](../../mfc/reference/colevariant-class.md) objeto) a una moneda ( `VT_CY` `COleCurrency` ) es correcta, el valor convertido se copia en este objeto y su estado se establece en válido. Si la conversión no se `COleCurrency` realiza correctamente, el valor del objeto se establece en 0 y su estado no es válido.

Para obtener más información, consulte las entradas [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1) y [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency::operador +, -

Estos operadores le permiten `COleCurrency` agregar y restar dos valores entre `COleCurrency` sí y cambiar el signo de un valor.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Observaciones

Si cualquiera de los operandos es null, el estado del valor resultante `COleCurrency` es null.

Si la operación aritmética se desborda, el valor resultante `COleCurrency` no es válido.

Si el operando no es válido y el otro `COleCurrency` no es null, el estado del valor resultante no es válido.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

## <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency::operador +-, -

Permite agregar y restar un `COleCurrency` valor `COleCurrency` a y desde este objeto.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Observaciones

Si cualquiera de los operandos es `COleCurrency` null, el estado de este objeto se establece en null.

Si la operación aritmética `COleCurrency` se desborda, el estado de este objeto se establece en no válido.

Si cualquiera de los operandos no es válido y `COleCurrency` el otro no es null, el estado de este objeto se establece en no válido.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

## <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency::operator \* y /

Permite escalar un `COleCurrency` valor por un valor integral.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Observaciones

Si `COleCurrency` el operando es null, `COleCurrency` el estado del valor resultante es null.

Si la operación aritmética se desborda o fluye de bajo nivel, el estado del valor resultante `COleCurrency` no es válido.

Si `COleCurrency` el operando no es válido, el estado del valor resultante `COleCurrency` no es válido.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

## <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency::operador, \*/?

Permite escalar este `COleCurrency` valor por un valor integral.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Observaciones

Si `COleCurrency` el operando es null, `COleCurrency` el estado de este objeto se establece en null.

Si la operación aritmética `COleCurrency` se desborda, el estado de este objeto se establece en no válido.

Si `COleCurrency` el operando no es `COleCurrency` válido, el estado de este objeto se establece en no válido.

Para obtener más información sobre los valores de estado válidos, no válidos y nulos, vea la [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

## <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency::operador &lt; &lt;,&gt;&gt;

Admite el volcado de diagnóstico y el almacenamiento en un archivo.

```
friend CDumpContext& operator<<(
    CDumpContext& dc,
    COleCurrency curSrc);

friend CArchive& operator<<(
    CArchive& ar,
    COleCurrency curSrc);

friend CArchive& operator>>(
    CArchive& ar,
    COleCurrency& curSrc);
```

### <a name="remarks"></a>Observaciones

El operador **>>** de extracción ( ) admite la carga desde un archivo.

## <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency::operador CURRENCY

Devuelve `CURRENCY` una estructura cuyo valor `COleCurrency` se copia de este objeto.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Observaciones

## <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::ParseCurrency

Llame a esta función miembro para analizar una cadena para leer un valor de moneda.

```
BOOL ParseCurrency(
    LPCTSTR lpszCurrency,
    DWORD dwFlags = 0,
    LCID lcid = LANG_USER_DEFAULT);

throw(CMemoryException*);
throw(COleException*);
```

### <a name="parameters"></a>Parámetros

*lpszCurrency*<br/>
Puntero a la cadena terminada en null que se va a analizar.

*dwFlags*<br/>
Indica los indicadores para la configuración regional, posiblemente el siguiente indicador:

- LOCALE_NOUSEROVERRIDE Utilice la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

*lcid*<br/>
Indica el ID de configuración regional que se usará para la conversión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena se convirtió correctamente a un valor de moneda, de lo contrario 0.

### <a name="remarks"></a>Observaciones

Utiliza especificaciones de idioma local (identificadores de configuración regional) para el significado de caracteres no numéricos en la cadena de origen.

Para obtener una explicación de los valores de ID de configuración regional, consulte Compatibilidad con [varios idiomas](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Si la cadena se convirtió correctamente en un `COleCurrency` valor de moneda, el valor de este objeto se establece en ese valor y su estado en válido.

Si la cadena no se pudo convertir a un valor de moneda `COleCurrency` o si hubo un desbordamiento numérico, el estado de este objeto no es válido.

Si se produjo un error en la conversión de cadena debido a errores de asignación de memoria, esta función produce una [excepción CMemoryException](../../mfc/reference/cmemoryexception-class.md). En cualquier otro estado de error, esta función produce una [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

## <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Operadores relacionales de COleCurrency

Compare dos valores de moneda y devuelva distinto de cero si la condición es true; de lo contrario 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Observaciones

> [!NOTE]
> El valor devuelto de **<** las ** \< ** **>** operaciones de ordenación ( , , , **>=**) es indefinido si el estado de cualquiera de los operandos es nulo o no válido. Los operadores `==`de `!=`igualdad ( , ) tienen en cuenta el estado de los operandos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

## <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency::SetCurrency

Llame a esta función miembro para establecer `COleCurrency` las unidades y la parte fraccionaria de este objeto.

```cpp
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parámetros

*nUnits*, *nFractionalUnits* Indica las unidades y la parte fraccionaria (en 1/10.000) del valor que se va a copiar en este `COleCurrency` objeto.

### <a name="remarks"></a>Observaciones

Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste adecuado a las unidades, como se muestra en el tercero de los ejemplos siguientes.

Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante valores largos firmados. El cuarto de los ejemplos siguientes muestra lo que sucede cuando los parámetros tienen signos diferentes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

## <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency::SetStatus

Llame a esta función miembro para establecer `COleCurrency` el estado (validez) de este objeto.

```cpp
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parámetros

*status*<br/>
El nuevo estado `COleCurrency` de este objeto.

### <a name="remarks"></a>Observaciones

El *status* valor del parámetro `CurrencyStatus` status se define mediante el `COleCurrency` tipo enumerado, que se define dentro de la clase.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid`Indica que `COleCurrency` este objeto es válido.

- `COleCurrency::invalid`Indica que `COleCurrency` este objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null`Indica que `COleCurrency` este objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de base de datos de "no tener valor", a diferencia de C++ NULL.)

> [!CAUTION]
> Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Se usará más a menudo para establecer el estado en null o invalid. Tenga en cuenta que el operador de asignación ( [operator )](#operator_eq)y [SetCurrency](#setcurrency) establecen el estado en del objeto en función de los valores de origen.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleVariant (clase)](../../mfc/reference/colevariant-class.md)
