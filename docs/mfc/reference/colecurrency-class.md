---
title: COleCurrency (clase)
ms.date: 11/04/2016
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
ms.openlocfilehash: d831353c72c40ab4f35b64046ab5d5236aa9644a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50553496"
---
# <a name="colecurrency-class"></a>COleCurrency (clase)

Encapsula el tipo de datos `CURRENCY` de la automatización OLE.

## <a name="syntax"></a>Sintaxis

```
class COleCurrency
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[COleCurrency::COleCurrency](#colecurrency)|Construye un objeto `COleCurrency`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[COleCurrency::Format](#format)|Genera una representación de cadena con formato de un `COleCurrency` objeto.|
|[COleCurrency::GetStatus](#getstatus)|Obtiene el estado (validez) de este `COleCurrency` objeto.|
|[COleCurrency::ParseCurrency](#parsecurrency)|Lee un valor de moneda de una cadena y establece el valor de `COleCurrency`.|
|[COleCurrency::SetCurrency](#setcurrency)|Establece el valor de este `COleCurrency` objeto.|
|[COleCurrency::SetStatus](#setstatus)|Establece el estado (validez) de este `COleCurrency` objeto.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[operador =](#operator_eq)|Copia un `COleCurrency` valor.|
|[operador +, -](#operator_plus_minus)|Agrega, resta y cambia el signo de `COleCurrency` valores.|
|[operador +=, =](#operator_plus_minus_eq)|Se agrega y se resta un `COleCurrency` valor de este `COleCurrency` objeto.|
|[operador * /](#operator_star)|Escala un `COleCurrency` valor por un valor entero.|
|[operador * =, / =](#operator_star_div_eq)|Esto escala `COleCurrency` valor por un valor entero.|
|[operador <<](#operator_stream)|Salidas un `COleCurrency` valor `CArchive` o `CDumpContext`.|
|[operador >>](#operator_stream)|Entradas un `COleCurrency` objeto `CArchive`.|
|[operador de moneda](#operator_currency)|Convierte un `COleCurrency` valor a la moneda.|
|[operador ==, <, < =, etcetera.](#colecurrency_relational_operators)|Compara dos `COleCurrency` valores.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[COleCurrency::m_cur](#m_cur)|Contiene la moneda subyacente de este `COleCurrency` objeto.|
|[COleCurrency::m_status](#m_status)|Contiene el estado de este `COleCurrency` objeto.|

## <a name="remarks"></a>Comentarios

`COleCurrency` no tiene una clase base.

DIVISA se implementa como un valor de entero de dos complementos escalado por 10.000 de 8 bytes. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El tipo de datos de moneda es muy útil para cálculos monetarios o para los cálculos de punto fijo, donde la precisión es importante. Es uno de los posibles tipos para el `VARIANT` tipo de datos de la automatización OLE.

`COleCurrency` También implementa algunas operaciones aritméticas básicas para este tipo de punto fijo. Las operaciones admitidas se han seleccionado para controlar los errores de redondeo que se producen durante los cálculos de punto fijo.

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
Un valor de moneda que se copiará en el nuevo `COleCurrency` objeto.

*curSrc*<br/>
Existente `COleCurrency` objeto que se copiará en el nuevo `COleCurrency` objeto.

*varSrc*<br/>
Existente `VARIANT` estructura de datos (posiblemente un `COleVariant` objeto) que se convertirá en un valor de moneda (VT_CY) y copiar en el nuevo `COleCurrency` objeto.

*nUnits*, *nFractionalUnits* indicar las unidades y la parte fraccionaria (de 1/10 de millar) del valor que se copiará en el nuevo `COleCurrency` objeto.

### <a name="remarks"></a>Comentarios

Todos estos constructores crean nuevos `COleCurrency` objetos inicializados en el valor especificado. Una breve descripción de cada uno de estos constructores sigue. A menos que se indique lo contrario, el estado de la nueva `COleCurrency` elemento está establecido en válido.

- Construcciones de COleCurrency() un `COleCurrency` objeto inicializado en 0 (cero).

- COleCurrency (`cySrc`) construye un `COleCurrency` objeto desde un [moneda](/windows/desktop/api/wtypes/ns-wtypes-tagcy) valor.

- COleCurrency (`curSrc`) construye un `COleCurrency` objeto a partir de una máquina `COleCurrency` objeto. El nuevo objeto tiene el mismo estado que el objeto de origen.

- COleCurrency (`varSrc`) construye un `COleCurrency` objeto. Intenta convertir un [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) estructura o `COleVariant` objeto como un valor de divisa (VT_CY). Si esta conversión se realiza correctamente, el valor convertido se copia en el nuevo `COleCurrency` objeto. Si no, es el valor de la `COleCurrency` objeto se establece en cero (0) y su estado a no válido.

- `COleCurrency(`nUnits`, `nFractionalUnits`) Constructs a `COleCurrency' objeto de los componentes numéricos especificados. Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste adecuado a las unidades. Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante los valores de tipo long con signo.

Para obtener más información, consulte el [moneda](/windows/desktop/api/wtypes/ns-wtypes-tagcy) y [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) entradas en el SDK de Windows.

### <a name="example"></a>Ejemplo

Los ejemplos siguientes muestran los efectos de los constructores de parámetro de cero y dos parámetros:

[!code-cpp[NVC_MFCOleContainer#10](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]

##  <a name="format"></a>  COleCurrency::Format

Llame a esta función miembro para crear una representación con formato del valor de moneda.

```
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const;
```

### <a name="parameters"></a>Parámetros

*dwFlags*<br/>
Indica los marcadores para la configuración regional. Solo la marca siguiente es relevante para la moneda:

- LOCALE_NOUSEROVERRIDE usar la configuración regional predeterminada del sistema, en lugar de configuración de usuario personalizada.

*lcid*<br/>
Indica el identificador de configuración regional que se usará para la conversión.

### <a name="return-value"></a>Valor devuelto

Un `CString` que contiene el valor de moneda con formato.

### <a name="remarks"></a>Comentarios

Da formato al valor con las especificaciones de idioma local (identificadores de configuración regional). Un símbolo de moneda no se incluye en el valor devuelto. Si el estado de este `COleCurrency` objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, se especifica la cadena devuelta por el recurso de cadena IDS_INVALID_CURRENCY.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#11](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]

##  <a name="getstatus"></a>  COleCurrency::GetStatus

Llame a esta función miembro para obtener el estado (validez) de un determinado `COleCurrency` objeto.

```
CurrencyStatus GetStatus() const;
```

### <a name="return-value"></a>Valor devuelto

Devuelve el estado de este `COleCurrency` valor.

### <a name="remarks"></a>Comentarios

El valor devuelto se define mediante el `CurrencyStatus` tipo enumerado que se define dentro el `COleCurrency` clase.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

  - `COleCurrency::valid` Indica que este `COleCurrency` objeto es válido.

  - `COleCurrency::invalid` Indica que este `COleCurrency` objeto no es válido; es decir, su valor puede ser incorrecto.

  - `COleCurrency::null` Indica que este `COleCurrency` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de NULL de C++).

El estado de un `COleCurrency` objeto no es válido en los casos siguientes:

- Si se establece su valor de una variante o `COleVariant` valor que no se pudo convertir en un valor de moneda.

- Si este objeto ha sufrido un desbordamiento o subdesbordamiento durante una operación aritmética de asignación, por ejemplo `+=` o **\* =**.

- Si se le asignó un valor no válido para este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido con [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que puede establecer el estado como no válidos, vea las funciones miembro siguientes:

- [COleCurrency](#colecurrency)

- [operador =](#operator_eq)

- [operador + -](#operator_plus_minus)

- [operador += y =](#operator_plus_minus_eq)

- [operador * /](#operator_star)

- [operador * = y / =](#operator_star_div_eq)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#12](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]

##  <a name="m_cur"></a>  COleCurrency::m_cur

Subyacente [moneda](/windows/desktop/api/wtypes/ns-wtypes-tagcy) estructura para este `COleCurrency` objeto.

### <a name="remarks"></a>Comentarios

> [!CAUTION]
>  Cambia el valor en el `CURRENCY` estructura accediendo el puntero devuelto por esta función cambiará el valor de esta `COleCurrency` objeto. No cambia el estado de este `COleCurrency` objeto.

Para obtener más información, consulte el [moneda](/windows/desktop/api/wtypes/ns-wtypes-tagcy) entrada en el SDK de Windows.

##  <a name="m_status"></a>  COleCurrency::m_status

El tipo de este miembro de datos es el tipo enumerado `CurrencyStatus`, que se define dentro de la `COleCurrency` clase.

```
enum CurrencyStatus{
    valid = 0,
    invalid = 1,
    null = 2,
};
```

### <a name="remarks"></a>Comentarios

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid` Indica que este `COleCurrency` objeto es válido.

- `COleCurrency::invalid` Indica que este `COleCurrency` objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null` Indica que este `COleCurrency` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de NULL de C++).

El estado de un `COleCurrency` objeto no es válido en los casos siguientes:

- Si se establece su valor de una variante o `COleVariant` valor que no se pudo convertir en un valor de moneda.

- Si este objeto ha sufrido un desbordamiento o subdesbordamiento durante una operación aritmética de asignación, por ejemplo `+=` o **\* =**.

- Si se le asignó un valor no válido para este objeto.

- Si el estado de este objeto se estableció explícitamente en no válido con [SetStatus](#setstatus).

Para obtener más información sobre las operaciones que puede establecer el estado como no válidos, vea las funciones miembro siguientes:

- [COleCurrency](#colecurrency)

- [operador =](#operator_eq)

- [operador +, -](#operator_plus_minus)

- [operador +=, =](#operator_plus_minus_eq)

- [operador * /](#operator_star)

- [operador * =, / =](#operator_star_div_eq)

> [!CAUTION]
>  Este miembro de datos es para situaciones de programación avanzadas. Debe usar las funciones de miembro insertada [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para las precauciones adicionales con respecto a este miembro de datos se establece explícitamente.

##  <a name="operator_eq"></a>  COleCurrency::operator =

Estos operadores de asignaciones sobrecargados copian el valor de moneda de origen en este `COleCurrency` objeto.

```
const COleCurrency& operator=(CURRENCY cySrc);
const COleCurrency& operator=(const COleCurrency& curSrc);
  const COleCurrency& operator=(const VARIANT& varSrc);
```

### <a name="remarks"></a>Comentarios

A continuación se muestra una breve descripción de cada operador:

- **operador = (** `cySrc` **)** el `CURRENCY` valor se copia en el `COleCurrency` objeto y su estado se establece en válido.

- **operador = (** `curSrc` **)** el valor y el estado del operando, existente `COleCurrency` objeto se copian en esta `COleCurrency` objeto.

- **operador = (** *varSrc* **)** si la conversión de la `VARIANT` valor (o [COleVariant](../../mfc/reference/colevariant-class.md) objeto) a una moneda ( `VT_CY`) es es correcto, el valor convertido se copia en esta `COleCurrency` objeto y su estado se establece en válido. Si la conversión no se realiza correctamente, el valor de la `COleCurrency` objeto se establece en 0 y su estado a no válido.

Para obtener más información, consulte el [moneda](/windows/desktop/api/wtypes/ns-wtypes-tagcy) y [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) entradas en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#15](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]

##  <a name="operator_plus_minus"></a>  COleCurrency::operator +, -

Estos operadores permiten sumar y restar dos `COleCurrency` valores a y entre sí y para cambiar el signo de un `COleCurrency` valor.

```
COleCurrency operator+(const COleCurrency& cur) const;
COleCurrency operator-(const COleCurrency& cur) const;
COleCurrency operator-() const;
```

### <a name="remarks"></a>Comentarios

Si cualquiera de los operandos es null, el estado del resultante `COleCurrency` valor es null.

Si la operación aritmética desborda resultante `COleCurrency` valor no es válido.

Si el operando es válido y el otro no es nulo, el estado del resultante `COleCurrency` valor no es válido.

Para obtener más información sobre los valores de estado válido, null y no válidos, vea el [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#16](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]

##  <a name="operator_plus_minus_eq"></a>  COleCurrency::operator +=, =

Permiten sumar y restar un `COleCurrency` valor hacia y desde este `COleCurrency` objeto.

```
const COleCurrency& operator+=(const COleCurrency& cur);
const COleCurrency& operator-=(const COleCurrency& cur);
```

### <a name="remarks"></a>Comentarios

Si cualquiera de los operandos es null, el estado de este `COleCurrency` objeto está establecido en null.

Si la operación aritmética desborda el estado de este `COleCurrency` objeto está establecido en no válido.

Si cualquiera de los operandos no es válido y el otro no es null, el estado de este `COleCurrency` objeto está establecido en no válido.

Para obtener más información sobre los valores de estado válido, null y no válidos, vea el [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#17](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]

##  <a name="operator_star"></a>  COleCurrency::operator \* y /

Le permiten escalar un `COleCurrency` valor por un valor entero.

```
COleCurrency operator*(long nOperand) const;
COleCurrency operator/(long nOperand) const;
```

### <a name="remarks"></a>Comentarios

Si el `COleCurrency` operando es null, el estado del resultante `COleCurrency` valor es null.

Si la operación aritmética desborda o subdesbordamientos, el estado del resultante `COleCurrency` valor no es válido.

Si el `COleCurrency` operando no es válido, el estado del resultante `COleCurrency` valor no es válido.

Para obtener más información sobre los valores de estado válido, null y no válidos, vea el [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#18](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]

##  <a name="operator_star_div_eq"></a>  COleCurrency::operator \*=, / =

Le permiten escalar esto `COleCurrency` valor por un valor entero.

```
const COleCurrency& operator*=(long nOperand);
const COleCurrency& operator/=(long nOperand);
```

### <a name="remarks"></a>Comentarios

Si el `COleCurrency` operando es null, el estado de este `COleCurrency` objeto está establecido en null.

Si la operación aritmética desborda el estado de este `COleCurrency` objeto está establecido en no válido.

Si el `COleCurrency` operando no es válido, el estado de este `COleCurrency` objeto está establecido en no válido.

Para obtener más información sobre los valores de estado válido, null y no válidos, vea el [m_status](#m_status) variable miembro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#19](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]

##  <a name="operator_stream"></a>  COleCurrency::operator &lt; &lt;, &gt;&gt;

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

### <a name="remarks"></a>Comentarios

La extracción ( **>>**) operador puede cargar desde un archivo.

##  <a name="operator_currency"></a>  COleCurrency::operator moneda

Devuelve un `CURRENCY` estructura cuyo valor se copia desde este `COleCurrency` objeto.

```
operator CURRENCY() const;
```

### <a name="remarks"></a>Comentarios

##  <a name="parsecurrency"></a>  COleCurrency::ParseCurrency

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
Un puntero a la cadena terminada en null que se analizará.

*dwFlags*<br/>
Indica los marcadores para la configuración regional, posiblemente la marca siguiente:

- LOCALE_NOUSEROVERRIDE usar la configuración regional predeterminada del sistema, en lugar de configuración de usuario personalizada.

*lcid*<br/>
Indica el identificador de configuración regional que se usará para la conversión.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena se convirtió correctamente en un valor de moneda, de lo contrario, 0.

### <a name="remarks"></a>Comentarios

Usa las especificaciones de idioma local (identificadores de configuración regional) para el significado de los caracteres no numéricos en la cadena de origen.

Para obtener una explicación de los valores de Id. de configuración regional, consulte [que admiten varios idiomas](/previous-versions/windows/desktop/automat/supporting-multiple-national-languages).

Si la cadena se convirtió correctamente en una moneda de valor, el valor de esta `COleCurrency` objeto se establece en ese valor y su estado a válido.

Si no se pudo convertir la cadena en un valor de moneda, o si se ha producido un desbordamiento numérico, el estado de este `COleCurrency` objeto no es válido.

Si se produjo un error en la conversión de cadena debido a errores de asignación de memoria, esta función genera un [CMemoryException](../../mfc/reference/cmemoryexception-class.md). En cualquier otro estado de error, esta función genera un [COleException](../../mfc/reference/coleexception-class.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#13](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]

##  <a name="colecurrency_relational_operators"></a>  Operadores relacionales COleCurrency

Comparar dos valores de moneda y devolver distinto de cero si la condición es true; en caso contrario, es 0.

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
>  El valor devuelto de las operaciones de ordenación ( **<**, **\< =**, **>**, **>=**) es indefinido si el estado de alguno de los operandos es null o no es válido. Los operadores de igualdad ( `==`, `!=`) tenga en cuenta el estado de los operandos.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#20](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]

##  <a name="setcurrency"></a>  COleCurrency::SetCurrency

Llame a esta función miembro para establecer las unidades y la parte fraccionaria de este `COleCurrency` objeto.

```
void SetCurrency(
    long nUnits,
    long nFractionalUnits);
```

### <a name="parameters"></a>Parámetros

*nUnits*, *nFractionalUnits* indicar las unidades y la parte fraccionaria (de 1/10 de millar) del valor que se copiará en esto `COleCurrency` objeto.

### <a name="remarks"></a>Comentarios

Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste correspondiente a las unidades, como se muestra en el tercero de los ejemplos siguientes.

Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante los valores de tipo long con signo. El cuarto de los ejemplos siguientes muestra lo que sucede cuando los parámetros tienen signos diferentes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCOleContainer#14](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]

##  <a name="setstatus"></a>  COleCurrency::SetStatus

Llame a esta función miembro para establecer el estado (validez) de este `COleCurrency` objeto.

```
void SetStatus(CurrencyStatus  status  );
```

### <a name="parameters"></a>Parámetros

*status*<br/>
El estado nueva para esta `COleCurrency` objeto.

### <a name="remarks"></a>Comentarios

El *estado* el valor del parámetro se define mediante el `CurrencyStatus` tipo enumerado, que se define dentro de la `COleCurrency` clase.

```
enum CurrencyStatus {
    valid = 0,
    invalid = 1,
    null = 2
    };
```

Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:

- `COleCurrency::valid` Indica que este `COleCurrency` objeto es válido.

- `COleCurrency::invalid` Indica que este `COleCurrency` objeto no es válido; es decir, su valor puede ser incorrecto.

- `COleCurrency::null` Indica que este `COleCurrency` objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de NULL de C++).

> [!CAUTION]
>  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Más a menudo se utilizará para establecer el estado como null o no válido. Tenga en cuenta que el operador de asignación ( [operador =](#operator_eq)) y [SetCurrency](#setcurrency) establecer el estado como del objeto basado en los valores de origen.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[COleVariant (clase)](../../mfc/reference/colevariant-class.md)
