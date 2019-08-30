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
ms.openlocfilehash: a23bc489fce00d9ba0be6a3aa71468b469bf54c8
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177407"
---
# <a name="colecurrency-class"></a>Clase COleCurrency

Encapsula el tipo de datos `CURRENCY` de la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleCurrency
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Construye un objeto `COleCurrency`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleCurrency::Format](#format)|Genera una representación de cadena con formato `COleCurrency` de un objeto.|
|[COleCurrency::GetStatus](#getstatus)|Obtiene el estado (validez) de este `COleCurrency` objeto.|
|[COleCurrency::ParseCurrency](#parsecurrency)|Lee un valor de moneda de una cadena y establece el valor `COleCurrency`de.|
|[COleCurrency::SetCurrency](#setcurrency)|Establece el valor de este `COleCurrency` objeto.|
|[COleCurrency::SetStatus](#setstatus)|Establece el estado (validez) de este `COleCurrency` objeto.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[operador =](#operator_eq)|Copia un `COleCurrency` valor.|
|[operador +,-](#operator_plus_minus)|Suma, resta y cambia el signo de `COleCurrency` los valores.|
|[operator +=, -=](#operator_plus_minus_eq)|Agrega y resta un `COleCurrency` valor de este `COleCurrency` objeto.|
|[operator */](#operator_star)|Escala un `COleCurrency` valor por un valor entero.|
|[operator *=, /=](#operator_star_div_eq)|Escala este `COleCurrency` valor por un valor entero.|
|[operador < <](#operator_stream)|Devuelve un `COleCurrency` valor a `CArchive` o `CDumpContext`.|
|[operador > >](#operator_stream)|Escribe un `COleCurrency` objeto de `CArchive`.|
|[operador CURRENCY](#operator_currency)|Convierte un `COleCurrency` valor en una moneda.|
|[operador = =, <, < =, etc.](#colecurrency_relational_operators)|Compara dos `COleCurrency` valores.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Contiene la moneda subyacente de este `COleCurrency` objeto.|
|[COleCurrency::m_status](#m_status)|Contiene el estado de este `COleCurrency` objeto.|

## <a name="remarks"></a>Comentarios

`COleCurrency`no tiene una clase base.

CURRENCY se implementa como un valor entero del complemento de dos bytes de 8 bytes escalado por 10.000. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El tipo de datos CURRENCY es sumamente útil para los cálculos que implican a Money o para cualquier cálculo de punto fijo en el que la precisión sea importante. Es uno de los tipos posibles para el tipo `VARIANT` de datos de la automatización OLE.

`COleCurrency`también implementa algunas operaciones aritméticas básicas para este tipo de punto fijo. Las operaciones admitidas se han seleccionado para controlar los errores de redondeo que se producen durante los cálculos de punto fijo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleCurrency`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="colecurrency"></a>  COleCurrency::COleCurrency

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
Valor de moneda que se va a copiar en `COleCurrency` el nuevo objeto.

*curSrc*<br/>
Objeto existente `COleCurrency` que se va a copiar en el `COleCurrency` nuevo objeto.

*varSrc*<br/>
Una estructura `VARIANT` de datos existente (posiblemente `COleVariant` un objeto) que se va a convertir en un valor de divisa (VT_CY) y `COleCurrency` copiarse en el nuevo objeto.

*nUnits*, *nFractionalUnits* indican las unidades y la parte fraccionaria (en 1/10000) del valor que se va a copiar en el `COleCurrency` nuevo objeto.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleCurrency` objetos inicializados en el valor especificado. A continuación se muestra una breve descripción de cada uno de estos constructores. A menos que se indique lo contrario, el `COleCurrency` estado del nuevo elemento se establece en Valid.

- COleCurrency () crea un `COleCurrency` objeto inicializado en 0 (cero).

- COleCurrency (`cySrc`) crea un `COleCurrency` objeto a partir de un valor de [moneda](/windows/win32/api/wtypes/ns-wtypes-cy) .

- COleCurrency (`curSrc`) crea un `COleCurrency` objeto a partir de un `COleCurrency` objeto existente. El nuevo objeto tiene el mismo estado que el objeto de origen.

- COleCurrency (`varSrc`) crea un `COleCurrency` objeto. Intenta convertir una estructura [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) u `COleVariant` objeto en un valor Currency (VT_CY). Si esta conversión se realiza correctamente, el valor convertido se copia en el `COleCurrency` nuevo objeto. Si no es así, el valor del `COleCurrency` objeto se establece en cero (0) y su estado en no válido.

- `COleCurrency(`nUnits`, `nFractionalUnits`) Constructs a `COleCurrency a partir de los componentes numéricos especificados. Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste adecuado en las unidades. Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante valores Long con signo.

Para obtener más información, consulte las entradas [Currency](/windows/win32/api/wtypes/ns-wtypes-cy) y [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

### <a name="example"></a>Ejemplo

En los ejemplos siguientes se muestran los efectos de los constructores de cero y dos parámetros:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="format"></a>  COleCurrency::Format

Llame a esta función miembro para crear una representación con formato del valor de moneda.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indica marcas para la configuración regional. Solo la marca siguiente es relevante para la moneda:

- LOCALE_NOUSEROVERRIDE usa la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

*lcid*<br/>
Indica el identificador de configuración regional que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

`CString` Que contiene el valor de moneda con formato.

### <a name="remarks"></a>Comentarios

Da formato al valor mediante las especificaciones de idioma local (ID. de configuración regional). Un símbolo de moneda no se incluye en el valor devuelto. Si el estado de este `COleCurrency` objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena devuelta se especifica mediante el recurso de cadena IDS_INVALID_CURRENCY.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="getstatus"></a>  COleCurrency::GetStatus

Llame a esta función miembro para obtener el estado (validez) de un `COleCurrency` objeto determinado.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado de este `COleCurrency` valor.

### <a name="remarks"></a>Comentarios

El valor devuelto se define mediante `CurrencyStatus` el tipo enumerado que se define en `COleCurrency` la clase.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

  - `COleCurrency::valid`Indica que este `COleCurrency` objeto es válido.

  - `COleCurrency::invalid`Indica que este `COleCurrency` objeto no es válido; es decir, su valor puede ser incorrecto.

  - `COleCurrency::null`Indica que este `COleCurrency` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Es "null" en el sentido de la base de datos "sin ningún valor", en lugar C++ de NULL).

El estado de un `COleCurrency` objeto no es válido en los casos siguientes:

- Si su valor se establece a partir de una `COleVariant` variante o un valor que no se pudo convertir en un valor de moneda.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante una operación de asignación aritmética, por `+=` ejemplo **\* =** , o.

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido mediante [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que pueden establecer el estado en no válido, vea las siguientes funciones miembro:

- [COleCurrency](#colecurrency)

- [operador =](#operator_eq)

- [operador +-](#operator_plus_minus)

- [operador + = y-=](#operator_plus_minus_eq)

- [operator * /](#operator_star)

- [operador * = y/=](#operator_star_div_eq)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

##  <a name="m_cur"></a>  COleCurrency::m_cur

La estructura de [moneda](/windows/win32/api/wtypes/ns-wtypes-cy) subyacente de `COleCurrency` este objeto.

### <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Al cambiar el valor de `CURRENCY` la estructura a la que accede el puntero devuelto por esta función, cambiará `COleCurrency` el valor de este objeto. No cambia el estado de este `COleCurrency` objeto.

Para obtener más información, vea la entrada de [moneda](/windows/win32/api/wtypes/ns-wtypes-cy) en el Windows SDK.

##  <a name="m_status"></a>  COleCurrency::m_status

El tipo de este miembro de datos es el tipo `CurrencyStatus`enumerado, que se define en la `COleCurrency` clase.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Comentarios

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid`Indica que este `COleCurrency` objeto es válido.

- `COleCurrency::invalid`Indica que este `COleCurrency` objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null`Indica que este `COleCurrency` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Es "null" en el sentido de la base de datos "sin ningún valor", en lugar C++ de NULL).

El estado de un `COleCurrency` objeto no es válido en los casos siguientes:

- Si su valor se establece a partir de una `COleVariant` variante o un valor que no se pudo convertir en un valor de moneda.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante una operación de asignación aritmética, por `+=` ejemplo **\* =** , o.

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido mediante [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que pueden establecer el estado en no válido, vea las siguientes funciones miembro:

- [COleCurrency](#colecurrency)

- [operador =](#operator_eq)

- [operador +,-](#operator_plus_minus)

- [operator +=, -=](#operator_plus_minus_eq)

- [operator */](#operator_star)

- [operator *=, /=](#operator_star_div_eq)

> [!CAUTION]
>  Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones miembro en línea [getStatus](#getstatus) y [SetStatus](#setstatus). Vea `SetStatus` para obtener más precauciones relacionadas con la configuración explícita de este miembro de datos.

##  <a name="operator_eq"></a>COleCurrency:: Operator =

Estos operadores de asignación sobrecargados copian el valor de moneda `COleCurrency` de origen en este objeto.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Comentarios

A continuación se muestra una breve descripción de cada operador:

- **Operator = (** `cySrc` **)** el `CURRENCY` valor se copia en el `COleCurrency` objeto y su estado se establece en Valid.

- **Operator = (** `curSrc` **)** el valor y el estado del operando, un `COleCurrency` objeto existente se copia en `COleCurrency` este objeto.

- **Operator = (** *varSrc* **)** Si la conversión `VARIANT` del valor (o objeto [COleVariant](../../mfc/reference/colevariant-class.md) ) en una moneda ( `VT_CY`) es correcta, el valor convertido se copia en este `COleCurrency` objeto y su estado se establece en válido. Si la conversión no se realiza correctamente, el valor del `COleCurrency` objeto se establece en 0 y su estado en no válido.

Para obtener más información, consulte las entradas [Currency](/windows/win32/api/wtypes/ns-wtypes-cy) y [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="operator_plus_minus"></a>COleCurrency:: Operator +,-

Estos operadores permiten agregar y sustraer dos `COleCurrency` valores entre sí y cambiar el signo de un `COleCurrency` valor.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Comentarios

Si alguno de los operandos es null, el estado del valor resultante `COleCurrency` es NULL.

Si la operación aritmética se desborda, el valor resultante `COleCurrency` no es válido.

Si el operando no es válido y el otro no es null, el estado del `COleCurrency` valor resultante no es válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, vea la variable miembro [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="operator_plus_minus_eq"></a>COleCurrency:: Operator + =,-=

Permite agregar y restar un `COleCurrency` valor a y desde este `COleCurrency` objeto.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Comentarios

Si alguno de los operandos es null, el estado de este `COleCurrency` objeto se establece en NULL.

Si la operación aritmética se desborda, el estado de este `COleCurrency` objeto se establece en no válido.

Si alguno de los operandos no es válido y el otro no es null, el estado de este `COleCurrency` objeto se establece en no válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, vea la variable miembro [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="operator_star"></a>COleCurrency:: Operator \* y/

Permite escalar un `COleCurrency` valor mediante un valor entero.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Comentarios

Si el `COleCurrency` operando es null, el estado del valor `COleCurrency` resultante es NULL.

Si la operación aritmética desborda o subdesbordamiento, el estado del valor resultante `COleCurrency` no es válido.

Si el `COleCurrency` operando no es válido, el estado del `COleCurrency` valor resultante no es válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, vea la variable miembro [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="operator_star_div_eq"></a>COleCurrency:: Operator \*=,/=

Permite escalar este `COleCurrency` valor mediante un valor entero.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Comentarios

Si el `COleCurrency` operando es null, el estado de `COleCurrency` este objeto se establece en NULL.

Si la operación aritmética se desborda, el estado de este `COleCurrency` objeto se establece en no válido.

Si el `COleCurrency` operando no es válido, el estado `COleCurrency` de este objeto se establece en no válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, vea la variable miembro [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="operator_stream"></a>COleCurrency:: Operator &lt;, &lt;&gt;&gt;

Admite el volcado y el almacenamiento de diagnósticos en un archivo.

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

### <a name="remarks"></a>Comentarios

El operador de **>>** extracción () permite cargar desde un archivo.

##  <a name="operator_currency"></a>COleCurrency:: Operator CURRENCY

Devuelve una `CURRENCY` estructura cuyo valor se copia desde este `COleCurrency` objeto.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Comentarios

##  <a name="parsecurrency"></a>  COleCurrency::ParseCurrency

Llame a esta función miembro para analizar una cadena y leer un valor de moneda.

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
Indica marcas para la configuración regional, posiblemente la marca siguiente:

- LOCALE_NOUSEROVERRIDE usa la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

*lcid*<br/>
Indica el identificador de configuración regional que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la cadena se convirtió correctamente en un valor de moneda; de lo contrario, es 0.

### <a name="remarks"></a>Comentarios

Utiliza especificaciones de idioma local (ID. de configuración regional) para el significado de caracteres no numéricos en la cadena de origen.

Para obtener una explicación de los valores de ID. de configuración regional, consulte [compatibilidad con varios idiomas](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Si la cadena se convirtió correctamente en un valor de moneda, el valor `COleCurrency` de este objeto se establece en ese valor y su estado en válido.

Si la cadena no se pudo convertir en un valor de moneda o si se produjo un desbordamiento numérico, el estado de `COleCurrency` este objeto no es válido.

Si se produjo un error en la conversión de cadena debido a errores de asignación de memoria, esta función produce [CMemoryException](../../mfc/reference/cmemoryexception-class.md). En cualquier otro estado de error, esta función produce [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency_relational_operators"></a>Operadores relacionales COleCurrency

Compara dos valores de moneda y devuelve un valor distinto de cero si la condición es verdadera. de lo contrario, es 0.

```
BOOL operator==(const COleCurrency& cur) const;
BOOL operator!=(const COleCurrency& cur) const;
BOOL operator<(const COleCurrency& cur) const;
BOOL operator>(const COleCurrency& cur) const;
BOOL operator<=(const COleCurrency& cur) const;
BOOL operator>=(const COleCurrency& cur) const;
```

### <a name="remarks"></a>Comentarios

> [!NOTE]
>  El valor devuelto de las operaciones de **<** ordenación **>** ( **>=** , **\< =** ,,) es indefinido si el estado de cualquiera de los operandos es null o no es válido. Los operadores de igualdad `==`( `!=`,) tienen en cuenta el estado de los operandos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="setcurrency"></a>  COleCurrency::SetCurrency

Llame a esta función miembro para establecer las unidades y la parte fraccionaria `COleCurrency` de este objeto.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parámetros

*nUnits*, *nFractionalUnits* indican las unidades y la parte fraccionaria (en 1/10000) del valor que se va a copiar en `COleCurrency` este objeto.

### <a name="remarks"></a>Comentarios

Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste adecuado en las unidades, tal y como se muestra en el tercer ejemplo siguiente.

Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante valores Long con signo. En el cuarto de los ejemplos siguientes se muestra lo que sucede cuando los parámetros tienen signos diferentes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="setstatus"></a>  COleCurrency::SetStatus

Llame a esta función miembro para establecer el estado (validez) de `COleCurrency` este objeto.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parámetros

*status*<br/>
Nuevo estado de este `COleCurrency` objeto.

### <a name="remarks"></a>Comentarios

El valor del parámetro status se define `CurrencyStatus` mediante el tipo enumerado, que se define `COleCurrency` en la clase.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid`Indica que este `COleCurrency` objeto es válido.

- `COleCurrency::invalid`Indica que este `COleCurrency` objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null`Indica que este `COleCurrency` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Es "null" en el sentido de la base de datos "sin ningún valor", en lugar C++ de NULL).

> [!CAUTION]
>  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Se suele usar para establecer el estado en null o no válido. Tenga en cuenta que el operador de asignación ( [Operator =](#operator_eq)) y [SetCurrency](#setcurrency) establecen el estado en del objeto basándose en los valores de origen.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleVariant (clase)](../../mfc/reference/colevariant-class.md)
