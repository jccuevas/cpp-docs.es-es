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
ms.openlocfilehash: 1e32d75599f51ba277180341df60762a02a82fe5
ms.sourcegitcommit: eff68e4e82be292a5664616b16a526df3e9d1cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80150934"
---
# <a name="colecurrency-class"></a>Clase COleCurrency

Encapsula el tipo de datos `CURRENCY` de la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleCurrency
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCurrency:: COleCurrency](#colecurrency)|Construye un objeto `COleCurrency`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCurrency:: Format](#format)|Genera una representación de cadena con formato de un objeto `COleCurrency`.|
|[COleCurrency:: GetStatus](#getstatus)|Obtiene el estado (validez) de este objeto `COleCurrency`.|
|[COleCurrency::P arseCurrency](#parsecurrency)|Lee un valor de divisa de una cadena y establece el valor de `COleCurrency`.|
|[COleCurrency:: SetCurrency](#setcurrency)|Establece el valor de este objeto `COleCurrency`.|
|[COleCurrency:: SetStatus](#setstatus)|Establece el estado (validez) de este objeto `COleCurrency`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[operador =](#operator_eq)|Copia un valor de `COleCurrency`.|
|[operador +,-](#operator_plus_minus)|Suma, resta y cambia el signo de los valores de `COleCurrency`.|
|[operador + =,-=](#operator_plus_minus_eq)|Agrega y resta un valor `COleCurrency` de este objeto `COleCurrency`.|
|[operador */](#operator_star)|Escala un valor de `COleCurrency` por un valor entero.|
|[operador * =,/=](#operator_star_div_eq)|Escala este valor de `COleCurrency` por un valor entero.|
|[operador < <](#operator_stream)|Devuelve un valor `COleCurrency` a `CArchive` o `CDumpContext`.|
|[operador > >](#operator_stream)|Escribe un objeto de `COleCurrency` de `CArchive`.|
|[operador CURRENCY](#operator_currency)|Convierte un valor de `COleCurrency` en una moneda.|
|[operador = =, <, < =, etc.](#colecurrency_relational_operators)|Compara dos valores de `COleCurrency`.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[COleCurrency:: m_cur](#m_cur)|Contiene la moneda subyacente de este objeto `COleCurrency`.|
|[COleCurrency:: m_status](#m_status)|Contiene el estado de este objeto `COleCurrency`.|

## <a name="remarks"></a>Observaciones

`COleCurrency` no tiene una clase base.

CURRENCY se implementa como un valor entero del complemento de dos bytes de 8 bytes escalado por 10.000. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El tipo de datos CURRENCY es sumamente útil para los cálculos que implican a Money o para cualquier cálculo de punto fijo en el que la precisión sea importante. Es uno de los tipos posibles para el tipo de datos `VARIANT` de la automatización OLE.

`COleCurrency` también implementa algunas operaciones aritméticas básicas para este tipo de punto fijo. Las operaciones admitidas se han seleccionado para controlar los errores de redondeo que se producen durante los cálculos de punto fijo.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`COleCurrency`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxdisp.h

##  <a name="colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency:: COleCurrency

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
Valor de moneda que se va a copiar en el nuevo objeto de `COleCurrency`.

*curSrc*<br/>
Objeto de `COleCurrency` existente que se va a copiar en el nuevo objeto `COleCurrency`.

*varSrc*<br/>
Una estructura de datos de `VARIANT` existente (posiblemente un objeto `COleVariant`) que se va a convertir en un valor de divisa (VT_CY) y copiarse en el nuevo objeto `COleCurrency`.

*nUnits*, *nFractionalUnits* indican las unidades y la parte fraccionaria (en 1/10000) del valor que se va a copiar en el nuevo objeto de `COleCurrency`.

### <a name="remarks"></a>Observaciones

Todos estos constructores crean nuevos objetos `COleCurrency` inicializados en el valor especificado. A continuación se muestra una breve descripción de cada uno de estos constructores. A menos que se indique lo contrario, el estado del nuevo elemento de `COleCurrency` se establece en Valid.

- COleCurrency () crea un objeto `COleCurrency` inicializado en 0 (cero).

- COleCurrency (`cySrc`) construye un objeto `COleCurrency` a partir de un valor de [moneda](/windows/win32/api/wtypes/ns-wtypes-cy~r1) .

- COleCurrency (`curSrc`) construye un objeto `COleCurrency` a partir de un objeto `COleCurrency` existente. El nuevo objeto tiene el mismo estado que el objeto de origen.

- COleCurrency (`varSrc`) construye un objeto `COleCurrency`. Intenta convertir una estructura de [variante](/windows/win32/api/oaidl/ns-oaidl-variant) o un objeto de `COleVariant` en un valor de moneda (VT_CY). Si esta conversión se realiza correctamente, el valor convertido se copia en el nuevo objeto `COleCurrency`. Si no es así, el valor del objeto `COleCurrency` se establece en cero (0) y su estado en no válido.

- COleCurrency (`nUnits`, `nFractionalUnits`) construye un objeto `COleCurrency` a partir de los componentes numéricos especificados. Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste adecuado en las unidades. Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante valores Long con signo.

Para obtener más información, consulte las entradas [Currency](/windows/win32/api/wtypes/ns-wtypes-cy~r1) y [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

### <a name="example"></a>Ejemplo

En los ejemplos siguientes se muestran los efectos de los constructores de cero y dos parámetros:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="colecurrencyformat"></a><a name="format"></a>COleCurrency:: Format

Llame a esta función miembro para crear una representación con formato del valor de moneda.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indica marcas para la configuración regional. Solo la marca siguiente es relevante para la moneda:

- LOCALE_NOUSEROVERRIDE usar la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

*lcid*<br/>
Indica el identificador de configuración regional que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

`CString` que contiene el valor de moneda con formato.

### <a name="remarks"></a>Observaciones

Da formato al valor mediante las especificaciones de idioma local (ID. de configuración regional). Un símbolo de moneda no se incluye en el valor devuelto. Si el estado de este objeto `COleCurrency` es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena devuelta se especifica mediante el recurso de cadena IDS_INVALID_CURRENCY.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency:: GetStatus

Llame a esta función miembro para obtener el estado (validez) de un objeto de `COleCurrency` determinado.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado de este `COleCurrency` valor.

### <a name="remarks"></a>Observaciones

El valor devuelto se define mediante el `CurrencyStatus` tipo enumerado que se define dentro de la clase `COleCurrency`.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

  - `COleCurrency::valid` indica que este objeto `COleCurrency` es válido.

  - `COleCurrency::invalid` indica que este objeto `COleCurrency` no es válido; es decir, su valor puede ser incorrecto.

  - `COleCurrency::null` indica que este objeto `COleCurrency` es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Es "null" en el sentido de la base de datos "sin ningún valor", en lugar C++ de NULL).

El estado de un objeto `COleCurrency` no es válido en los casos siguientes:

- Si su valor se establece desde un valor VARIANT o `COleVariant` que no se pudo convertir en un valor de moneda.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante una operación de asignación aritmética, por ejemplo `+=` o **\*=** .

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido mediante [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que pueden establecer el estado en no válido, vea las siguientes funciones miembro:

- [COleCurrency](#colecurrency)

- [operador =](#operator_eq)

- [operador +-](#operator_plus_minus)

- [operador + = y-=](#operator_plus_minus_eq)

- [operador */](#operator_star)

- [operador * = y/=](#operator_star_div_eq)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

##  <a name="colecurrencym_cur"></a><a name="m_cur"></a>COleCurrency:: m_cur

La estructura de [moneda](/windows/win32/api/wtypes/ns-wtypes-cy~r1) subyacente para este objeto `COleCurrency`.

### <a name="remarks"></a>Observaciones

> [!CAUTION]
>  Al cambiar el valor de la estructura `CURRENCY` a la que accede el puntero devuelto por esta función, cambiará el valor de este objeto `COleCurrency`. No cambia el estado de este objeto `COleCurrency`.

Para obtener más información, vea la entrada de [moneda](/windows/win32/api/wtypes/ns-wtypes-cy~r1) en el Windows SDK.

##  <a name="colecurrencym_status"></a><a name="m_status"></a>COleCurrency:: m_status

El tipo de este miembro de datos es el tipo enumerado `CurrencyStatus`, que se define dentro de la clase `COleCurrency`.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Observaciones

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid` indica que este objeto `COleCurrency` es válido.

- `COleCurrency::invalid` indica que este objeto `COleCurrency` no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null` indica que este objeto `COleCurrency` es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Es "null" en el sentido de la base de datos "sin ningún valor", en lugar C++ de NULL).

El estado de un objeto `COleCurrency` no es válido en los casos siguientes:

- Si su valor se establece desde un valor VARIANT o `COleVariant` que no se pudo convertir en un valor de moneda.

- Si este objeto ha experimentado un desbordamiento o subdesbordamiento durante una operación de asignación aritmética, por ejemplo `+=` o **\*=** .

- Si se asignó un valor no válido a este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido mediante [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que pueden establecer el estado en no válido, vea las siguientes funciones miembro:

- [COleCurrency](#colecurrency)

- [operador =](#operator_eq)

- [operador +,-](#operator_plus_minus)

- [operador + =,-=](#operator_plus_minus_eq)

- [operador */](#operator_star)

- [operador * =,/=](#operator_star_div_eq)

> [!CAUTION]
>  Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones miembro en línea [getStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para obtener más precauciones con respecto a la configuración explícita de este miembro de datos.

##  <a name="colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency:: Operator =

Estos operadores de asignación sobrecargados copian el valor de moneda de origen en este objeto `COleCurrency`.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Observaciones

A continuación se muestra una breve descripción de cada operador:

- **Operator = (** `cySrc` **)** El valor `CURRENCY` se copia en el objeto `COleCurrency` y su estado se establece en Valid.

- **Operator = (** `curSrc` **)** El valor y el estado del operando, un objeto de `COleCurrency` existente se copia en este objeto `COleCurrency`.

- **Operator = (** *varSrc* **)** Si la conversión del valor `VARIANT` (o el objeto [COleVariant](../../mfc/reference/colevariant-class.md) ) en una moneda (`VT_CY`) se realiza correctamente, el valor convertido se copia en este objeto `COleCurrency` y su estado se establece en Valid. Si la conversión no se realiza correctamente, el valor del objeto `COleCurrency` se establece en 0 y su estado en no válido.

Para obtener más información, consulte las entradas [Currency](/windows/win32/api/wtypes/ns-wtypes-cy~r1) y [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency:: Operator +,-

Estos operadores permiten agregar y sustraer dos valores `COleCurrency` entre sí y cambiar el signo de un valor `COleCurrency`.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Observaciones

Si alguno de los operandos es null, el estado del valor de `COleCurrency` resultante es NULL.

Si la operación aritmética se desborda, el valor de `COleCurrency` resultante no es válido.

Si el operando no es válido y el otro no es null, el estado del valor de `COleCurrency` resultante no es válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, consulte la variable miembro de [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency:: Operator + =,-=

Permite agregar y restar un valor `COleCurrency` a este objeto `COleCurrency` y desde este.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Observaciones

Si alguno de los operandos es null, el estado de este objeto `COleCurrency` se establece en NULL.

Si se desborda la operación aritmética, el estado de este objeto `COleCurrency` está establecido en no válido.

Si alguno de los operandos no es válido y el otro no es null, el estado de este objeto `COleCurrency` está establecido en no válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, consulte la variable miembro de [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency:: Operator \* y/

Permite escalar un valor `COleCurrency` mediante un valor entero.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Observaciones

Si el operando `COleCurrency` es null, el estado del valor de `COleCurrency` resultante es NULL.

Si la operación aritmética desborda o subdesbordamiento, el estado del valor de `COleCurrency` resultante no es válido.

Si el operando `COleCurrency` no es válido, el estado del valor de `COleCurrency` resultante no es válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, consulte la variable miembro de [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency:: Operator \*=,/=

Permite escalar este valor `COleCurrency` mediante un valor entero.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Observaciones

Si el operando `COleCurrency` es null, el estado de este objeto `COleCurrency` se establece en NULL.

Si se desborda la operación aritmética, el estado de este objeto `COleCurrency` está establecido en no válido.

Si el operando `COleCurrency` no es válido, el estado de este objeto `COleCurrency` se establece en no válido.

Para obtener más información sobre los valores válidos, no válidos y de estado null, consulte la variable miembro de [m_status](#m_status) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency:: Operator &lt;&lt;, &gt;&gt;

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

### <a name="remarks"></a>Observaciones

El operador de extracción ( **>>** ) admite la carga desde un archivo.

##  <a name="colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency:: Operator CURRENCY

Devuelve una estructura de `CURRENCY` cuyo valor se copia de este objeto `COleCurrency`.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Observaciones

##  <a name="colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::P arseCurrency

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

- LOCALE_NOUSEROVERRIDE usar la configuración regional predeterminada del sistema, en lugar de la configuración de usuario personalizada.

*lcid*<br/>
Indica el identificador de configuración regional que se va a usar para la conversión.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la cadena se convirtió correctamente en un valor de moneda; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Utiliza especificaciones de idioma local (ID. de configuración regional) para el significado de caracteres no numéricos en la cadena de origen.

Para obtener una explicación de los valores de ID. de configuración regional, consulte [compatibilidad con varios idiomas](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Si la cadena se convirtió correctamente en un valor de moneda, el valor de este objeto `COleCurrency` se establece en ese valor y su estado en válido.

Si la cadena no se pudo convertir en un valor de moneda o si se produjo un desbordamiento numérico, el estado de este objeto `COleCurrency` no es válido.

Si se produjo un error en la conversión de cadena debido a errores de asignación de memoria, esta función produce [CMemoryException](../../mfc/reference/cmemoryexception-class.md). En cualquier otro estado de error, esta función produce [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Operadores relacionales COleCurrency

Compara dos valores de moneda y devuelve un valor distinto de cero si la condición es verdadera. de lo contrario, es 0.

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
>  El valor devuelto de las operaciones de ordenación ( **<** , **\<=** , **>** , **>=** ) es indefinido si el estado de cualquiera de los operandos es null o no es válido. Los operadores de igualdad (`==`, `!=`) tienen en cuenta el estado de los operandos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency:: SetCurrency

Llame a esta función miembro para establecer las unidades y la parte fraccionaria de este objeto `COleCurrency`.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parámetros

*nUnits*, *nFractionalUnits* indican las unidades y la parte fraccionaria (en 1/10000) del valor que se va a copiar en este objeto `COleCurrency`.

### <a name="remarks"></a>Observaciones

Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste adecuado en las unidades, tal y como se muestra en el tercer ejemplo siguiente.

Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante valores Long con signo. En el cuarto de los ejemplos siguientes se muestra lo que sucede cuando los parámetros tienen signos diferentes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency:: SetStatus

Llame a esta función miembro para establecer el estado (validez) de este objeto `COleCurrency`.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parámetros

*status*<br/>
Nuevo estado de este objeto `COleCurrency`.

### <a name="remarks"></a>Observaciones

El valor del parámetro *status* se define mediante el `CurrencyStatus` tipo enumerado, que se define dentro de la clase `COleCurrency`.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid` indica que este objeto `COleCurrency` es válido.

- `COleCurrency::invalid` indica que este objeto `COleCurrency` no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null` indica que este objeto `COleCurrency` es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Es "null" en el sentido de la base de datos "sin ningún valor", en lugar C++ de NULL).

> [!CAUTION]
>  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Se suele usar para establecer el estado en null o no válido. Tenga en cuenta que el operador de asignación ( [Operator =](#operator_eq)) y [SetCurrency](#setcurrency) establecen el estado en del objeto basándose en los valores de origen.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleVariant (clase)](../../mfc/reference/colevariant-class.md)
