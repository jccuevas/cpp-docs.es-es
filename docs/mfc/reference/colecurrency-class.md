---
title: Clase COleCurrency | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CURRENCY
- COleCurrency
dev_langs:
- C++
helpviewer_keywords:
- fixed-point numbers
- numbers, fixed-point
- CURRENCY
- COleCurrency class
ms.assetid: 3a36e345-303f-46fb-a57c-858274378a8d
caps.latest.revision: 24
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 38dbd45818f53430db37bb5807c255494c4a9896
ms.lasthandoff: 02/24/2017

---
# <a name="colecurrency-class"></a>Clase OLECurrency.
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
|[COleCurrency::Format](#format)|Genera una representación de cadena con formato de un `COleCurrency` objeto.|  
|[COleCurrency::GetStatus](#getstatus)|Obtiene el estado (validez) de este `COleCurrency` objeto.|  
|[COleCurrency::ParseCurrency](#parsecurrency)|Lee un **moneda** valor de una cadena y establece el valor de `COleCurrency`.|  
|[COleCurrency::SetCurrency](#setcurrency)|Establece el valor de este `COleCurrency` objeto.|  
|[COleCurrency::SetStatus](#setstatus)|Establece el estado (validez) de este `COleCurrency` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador =](#operator_eq)|Copia un `COleCurrency` valor.|  
|[operador +, -](#operator_plus_minus)|Agrega, resta y cambia el signo de `COleCurrency` valores.|  
|[operador +=, =](#operator_plus_minus_eq)|Agrega y resta un `COleCurrency` el valor de este `COleCurrency` objeto.|  
|[operador * /](#operator_star)|Escalas un `COleCurrency` valor mediante un valor entero.|  
|[operador * =, / =](#operator_star_div_eq)|Esta escala `COleCurrency` valor mediante un valor entero.|  
|[(operador)](#operator_stream)|Salidas de un `COleCurrency` valor `CArchive` o `CDumpContext`.|  
|[operador >>](#operator_stream)|Entradas un `COleCurrency` objeto `CArchive`.|  
|[operador de moneda](#operator_currency)|Convierte un `COleCurrency` valor en un **moneda**.|  
|[operador ==,<,></,><=,></=,>](#colecurrency_relational_operators)|Compara dos `COleCurrency` valores.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[COleCurrency::m_cur](#m_cur)|Contiene subyacente **moneda** para este `COleCurrency` objeto.|  
|[COleCurrency::m_status](#m_status)|Contiene el estado de este `COleCurrency` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 **COleCurrency** no tiene una clase base.  
  
 **MONEDA** se implementa como un valor entero de complemento de dos escalada de 10.000 de 8 bytes. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El **moneda** tipo de datos es muy útil para cálculos monetarios, o para los cálculos de punto fijo, donde la precisión es importante. Es uno de los tipos posibles de la `VARIANT` el tipo de datos de la automatización OLE.  
  
 **COleCurrency** también implementa algunas operaciones aritméticas básicas para este tipo de punto fijo. Se han seleccionado las operaciones compatibles para controlar los errores de redondeo que se producen durante los cálculos de punto fijo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `COleCurrency`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** afxdisp.h  
  
##  <a name="a-namecolecurrencya--colecurrencycolecurrency"></a><a name="colecurrency"></a>COleCurrency::COleCurrency  
 Construye un **COleCurrency** objeto.  
  
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
 `cySrc`  
 Un **moneda** valor que se copiará en el nuevo **COleCurrency** objeto.  
  
 `curSrc`  
 Existente **COleCurrency** objeto que se copiará en el nuevo **COleCurrency** objeto.  
  
 *varSrc*  
 Existente **VARIANT** estructura de datos (posiblemente una `COleVariant` objeto) se convierta en un valor de divisa ( `VT_CY`) y se copian en el nuevo **COleCurrency** objeto.  
  
 `nUnits`, `nFractionalUnits`  
 Indicar las unidades y la parte fraccionaria (en 1/10, miles) del valor que se copiará en la nueva **COleCurrency** objeto.  
  
### <a name="remarks"></a>Comentarios  
 Todos estos constructores crean nuevos **COleCurrency** objetos inicializados en el valor especificado. Muestra una breve descripción de cada uno de estos constructores. A menos que se indique lo contrario, el estado de la nueva **COleCurrency** elemento está establecido en válido.  
  
- Construcciones de COleCurrency() una **COleCurrency** objeto se inicializa en 0 (cero).  
  
- COleCurrency (`cySrc`) construye una **COleCurrency** objeto a partir de un [moneda](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) valor.  
  
- COleCurrency (`curSrc`) construye una **COleCurrency** objeto a partir de una **COleCurrency** objeto. El nuevo objeto tiene el mismo estado que el objeto de origen.  
  
- COleCurrency (`varSrc`) construye una **COleCurrency** objeto. Intenta convertir un [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) estructura o `COleVariant` objeto a una moneda ( `VT_CY`) valor. Si esta conversión se realiza correctamente, el valor convertido se copia en el nuevo **COleCurrency** objeto. Si no, es el valor de la **COleCurrency** objeto se establece en cero (0) y su estado a no válido.  
  
- `COleCurrency(`nUnits`, `'nFractionalUnits) construye una **COleCurrency** objeto de los componentes numéricos especificados. Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste correspondiente a las unidades. Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante los valores de tipo long con signo.  
  
 Para obtener más información, consulte el [moneda](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) y [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) entradas en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 Los ejemplos siguientes muestran los efectos de los constructores de parámetro cero y dos parámetros:  
  
 [!code-cpp[NVC_MFCOleContainer&#10;](../../mfc/codesnippet/cpp/colecurrency-class_1.cpp)]  
  
##  <a name="a-nameformata--colecurrencyformat"></a><a name="format"></a>COleCurrency::Format  
 Llame a esta función miembro para crear una representación con formato del valor de moneda.  
  
```  
CString Format(DWORD  dwFlags = 0, LCID  lcid = LANG_USER_DEFAULT) const; 
```  
  
### <a name="parameters"></a>Parámetros  
 `dwFlags`  
 Indica los marcadores para la configuración regional. La siguiente marca de solo es relevante para la moneda:  
  
- **LOCALE_NOUSEROVERRIDE** usar la configuración regional predeterminada del sistema, en lugar de configuración de usuario personalizada.  
  
 `lcid`  
 Indica el identificador de configuración regional para la conversión.  
  
### <a name="return-value"></a>Valor devuelto  
 Un `CString` que contiene el valor con formato de moneda.  
  
### <a name="remarks"></a>Comentarios  
 Da formato al valor con las especificaciones de idioma local (identificadores de configuración regional). Un símbolo de moneda no se incluye en el valor devuelto. Si el estado de este **COleCurrency** objeto es null, el valor devuelto es una cadena vacía. Si el estado no es válido, la cadena devuelta es especificada por el recurso de cadena **IDS_INVALID_CURRENCY**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#11;](../../mfc/codesnippet/cpp/colecurrency-class_2.cpp)]  
  
##  <a name="a-namegetstatusa--colecurrencygetstatus"></a><a name="getstatus"></a>COleCurrency::GetStatus  
 Llame a esta función miembro para obtener el estado (validez) de un determinado **COleCurrency** objeto.  
  
```  
CurrencyStatus GetStatus() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el estado de este **COleCurrency** valor.  
  
### <a name="remarks"></a>Comentarios  
 El valor devuelto se define mediante la `CurrencyStatus` tipo enumerado que se define dentro de la **COleCurrency** clase.  
  
 `enum CurrencyStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleCurrency::valid** indica que este **COleCurrency** objeto es válido.  
  
- **COleCurrency::invalid** indica que este **COleCurrency** objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleCurrency::null** indica que este **COleCurrency** objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
 El estado de un **COleCurrency** objeto no es válido en los casos siguientes:  
  
-   Si se establece su valor desde una **VARIANT** o `COleVariant` valor que no se pudo convertir en un valor monetario.  
  
-   Si este objeto ha sufrido un desbordamiento o subdesbordamiento durante una operación aritmética de asignación, por ejemplo `+=` o ** \* = **.  
  
-   Si se asignó un valor no válido para este objeto.  
  
-   Si el estado de este objeto se estableció explícitamente en no válido con [SetStatus](#setstatus).  
  
 Para obtener más información sobre las operaciones que puede establecer el estado no son válidos, vea las siguientes funciones miembro:  
  
- [OLECurrency.](#colecurrency)  
  
- [operador =](#operator_eq)  
  
- [operador +:](#operator_plus_minus)  
  
- [operador += y =](#operator_plus_minus_eq)  
  
- [operador * /](#operator_star)  
  
- [operador * = y / =](#operator_star_div_eq)  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#12;](../../mfc/codesnippet/cpp/colecurrency-class_3.cpp)]  
  
##  <a name="a-namemcura--colecurrencymcur"></a><a name="m_cur"></a>COleCurrency::m_cur  
 Subyacente [moneda](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) estructura de este **COleCurrency** objeto.  
  
### <a name="remarks"></a>Comentarios  
  
> [!CAUTION]
>  Cambie el valor en el **moneda** estructura accediendo el puntero devuelto por esta función cambiará el valor de esta **COleCurrency** objeto. No cambia el estado de este **COleCurrency** objeto.  
  
 Para obtener más información, consulte el [moneda](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) entrada en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
##  <a name="a-namemstatusa--colecurrencymstatus"></a><a name="m_status"></a>COleCurrency::m_status  
 El tipo de este miembro de datos es el tipo enumerado `CurrencyStatus`, que se define dentro de la **COleCurrency** clase.  
  
```  
enum CurrencyStatus{  
    valid = 0,  
    invalid = 1,  
    null = 2,  
};  
```  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleCurrency::valid** indica que este **COleCurrency** objeto es válido.  
  
- **COleCurrency::invalid** indica que este **COleCurrency** objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleCurrency::null** indica que este **COleCurrency** objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
 El estado de un **COleCurrency** objeto no es válido en los casos siguientes:  
  
-   Si se establece su valor desde una **VARIANT** o `COleVariant` valor que no se pudo convertir en un valor monetario.  
  
-   Si este objeto ha sufrido un desbordamiento o subdesbordamiento durante una operación aritmética de asignación, por ejemplo `+=` o ** \* = **.  
  
-   Si se asignó un valor no válido para este objeto.  
  
-   Si el estado de este objeto se estableció explícitamente en no válido con [SetStatus](#setstatus).  
  
 Para obtener más información sobre las operaciones que puede establecer el estado no son válidos, vea las siguientes funciones miembro:  
  
- [OLECurrency.](#colecurrency)  
  
- [operador =](#operator_eq)  
  
- [operador +, -](#operator_plus_minus)  
  
- [operador +=, =](#operator_plus_minus_eq)  
  
- [operador * /](#operator_star)  
  
- [operador * =, / =](#operator_star_div_eq)  
  
    > [!CAUTION]
    >  Este miembro de datos es para situaciones de programación avanzadas. Debe utilizar las funciones de miembro insertada [GetStatus](#getstatus) y [SetStatus](#setstatus). Consulte `SetStatus` para las precauciones adicionales con respecto a este miembro de datos se establece explícitamente.  
  
##  <a name="a-nameoperatoreqa--colecurrencyoperator-"></a><a name="operator_eq"></a>COleCurrency::operator =  
 Estos operadores de asignaciones sobrecargados copiar el valor de moneda de origen en esta **COleCurrency** objeto.  
  
```  
const COleCurrency& operator=(CURRENCY cySrc);  
const COleCurrency& operator=(const COleCurrency& curSrc);  
  const COleCurrency& operator=(const VARIANT& varSrc);
```  
  
### <a name="remarks"></a>Comentarios  
 A continuación se muestra una breve descripción de cada operador:  
  
- **operador = (** `cySrc` **)** el `CURRENCY` se copiará en el **COleCurrency** objeto y su estado se establece en válido.  
  
- **operador = (** `curSrc` **)** el valor y el estado del operando, existente **COleCurrency** objeto se copian en esta **COleCurrency** objeto.  
  
- **operador = (** *varSrc* **)** si la conversión de la `VARIANT` valor (o [COleVariant](../../mfc/reference/colevariant-class.md) objeto) a una moneda ( `VT_CY`) es correcta, el valor convertido se copia en esta **COleCurrency** objeto y su estado se establece en válido. Si la conversión no se realiza correctamente, el valor de la **COleCurrency** objeto se establece en 0 y su estado a no válido.  
  
 Para obtener más información, consulte el [moneda](http://msdn.microsoft.com/en-us/5e81273c-7289-45c7-93c0-32c1553f708e) y [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) entradas en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#15;](../../mfc/codesnippet/cpp/colecurrency-class_4.cpp)]  
  
##  <a name="a-nameoperatorplusminusa--colecurrencyoperator---"></a><a name="operator_plus_minus"></a>COleCurrency::operator +, -  
 Estos operadores permiten sumar y restar dos **COleCurrency** valores a y desde entre sí y para cambiar el signo de un **COleCurrency** valor.  
  
```  
COleCurrency operator+(const COleCurrency& cur) const;  
COleCurrency operator-(const COleCurrency& cur) const;  
COleCurrency operator-() const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si cualquiera de los operandos es null, el estado del resultante **COleCurrency** valor es null.  
  
 Si la operación aritmética desborda resultante **COleCurrency** valor no es válido.  
  
 Si el operando es válida y el otro es no null, el estado del resultante **COleCurrency** valor no es válido.  
  
 Para obtener más información sobre los valores de estado válido, null y no válidos, consulte el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&16;](../../mfc/codesnippet/cpp/colecurrency-class_5.cpp)]  
  
##  <a name="a-nameoperatorplusminuseqa--colecurrencyoperator---"></a><a name="operator_plus_minus_eq"></a>COleCurrency::operator +=, =  
 Le permiten agregar y sustraer un **COleCurrency** valor hacia y desde este **COleCurrency** objeto.  
  
```  
const COleCurrency& operator+=(const COleCurrency& cur);  
const COleCurrency& operator-=(const COleCurrency& cur);
```  
  
### <a name="remarks"></a>Comentarios  
 Si cualquiera de los operandos es null, el estado de este **COleCurrency** objeto está establecido en null.  
  
 Si la operación aritmética desborda el estado de este **COleCurrency** objeto se establece en no válido.  
  
 Si cualquiera de los operandos es válido y el otro no es null, el estado de este **COleCurrency** objeto se establece en no válido.  
  
 Para obtener más información sobre los valores de estado válido, null y no válidos, consulte el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#17;](../../mfc/codesnippet/cpp/colecurrency-class_6.cpp)]  
  
##  <a name="a-nameoperatorstara--colecurrencyoperator--and-"></a><a name="operator_star"></a>COleCurrency::operator * y /  
 Le permiten escalar una **COleCurrency** valor por un valor entero.  
  
```  
COleCurrency operator*(long nOperand) const;  
COleCurrency operator/(long nOperand) const;  
```  
  
### <a name="remarks"></a>Comentarios  
 Si el **COleCurrency** operando es null, el estado del resultante **COleCurrency** valor es null.  
  
 Si la operación aritmética desborda o subdesbordamientos, el estado del resultante **COleCurrency** valor no es válido.  
  
 Si el **COleCurrency** operando no es válido, el estado del resultante **COleCurrency** valor no es válido.  
  
 Para obtener más información sobre los valores de estado válido, null y no válidos, consulte el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#18;](../../mfc/codesnippet/cpp/colecurrency-class_7.cpp)]  
  
##  <a name="a-nameoperatorstardiveqa--colecurrencyoperator--"></a><a name="operator_star_div_eq"></a>COleCurrency::operator * =, / =  
 Le permiten escalar esto **COleCurrency** valor por un valor entero.  
  
```  
const COleCurrency& operator*=(long nOperand);  
const COleCurrency& operator/=(long nOperand);
```  
  
### <a name="remarks"></a>Comentarios  
 Si el **COleCurrency** operando es null, el estado de este **COleCurrency** objeto está establecido en null.  
  
 Si la operación aritmética desborda el estado de este **COleCurrency** objeto se establece en no válido.  
  
 Si el **COleCurrency** operando no es válido, el estado de este **COleCurrency** objeto se establece en no válido.  
  
 Para obtener más información sobre los valores de estado válido, null y no válidos, consulte el [m_status](#m_status) variable miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer Nº&19;](../../mfc/codesnippet/cpp/colecurrency-class_8.cpp)]  
  
##  <a name="a-nameoperatorstreama--colecurrencyoperator-ltlt-gtgt"></a><a name="operator_stream"></a>COleCurrency::operator &lt; &lt;,&gt;&gt;  
 Admite el volcado de diagnóstico y almacenar en un archivo.  
  
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
 La extracción ( ** >> **) operador admite la carga de un archivo.  
  
##  <a name="a-nameoperatorcurrencya--colecurrencyoperator-currency"></a><a name="operator_currency"></a>COleCurrency::operator DIVISA  
 Devuelve un `CURRENCY` estructura cuyo valor se copia desde este **COleCurrency** objeto.  
  
```  
operator CURRENCY() const; 
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="a-nameparsecurrencya--colecurrencyparsecurrency"></a><a name="parsecurrency"></a>COleCurrency::ParseCurrency  
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
 *lpszCurrency*  
 Puntero a la cadena terminada en null que se va a analizar.  
  
 `dwFlags`  
 Indica los marcadores para la configuración regional, posiblemente la marca siguiente:  
  
- **LOCALE_NOUSEROVERRIDE** usar la configuración regional predeterminada del sistema, en lugar de configuración de usuario personalizada.  
  
 `lcid`  
 Indica el identificador de configuración regional para la conversión.  
  
### <a name="return-value"></a>Valor devuelto  
 Distinto de cero si la cadena se convirtió correctamente en un valor de moneda, de lo contrario, 0.  
  
### <a name="remarks"></a>Comentarios  
 Usa las especificaciones de idioma local (identificadores de configuración regional) para el significado de los caracteres no numéricos en la cadena de origen.  
  
 Para obtener una explicación de los valores de identificador de configuración regional, consulte [compatibilidad con varios idiomas](http://msdn.microsoft.com/en-us/47dc5add-232c-4268-b977-43e12da81ede).  
  
 Si la cadena se convirtió correctamente en una moneda de valor, el valor de esta **COleCurrency** objeto se establece en ese valor y su estado a válido.  
  
 Si no se pudo convertir la cadena en un valor monetario o si se produjo un desbordamiento numérico, el estado de este **COleCurrency** objeto no es válido.  
  
 Si la conversión de cadena erróneas debido a errores de asignación de memoria, esta función produce un [CMemoryException](../../mfc/reference/cmemoryexception-class.md). En cualquier otro estado de error, esta función lanza una [COleException](../../mfc/reference/coleexception-class.md).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#13;](../../mfc/codesnippet/cpp/colecurrency-class_9.cpp)]  
  
##  <a name="a-namecolecurrencyrelationaloperatorsa--colecurrency-relational-operators"></a><a name="colecurrency_relational_operators"></a>Operadores relacionales de OLECurrency.  
 Comparar dos valores de moneda y devolver distinto de cero si la condición es true; en caso contrario, 0.  
  
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
>  El valor devuelto de las operaciones de ordenación ( ** < **, ** \< = **, ** > **, ** >= **) es indefinido si el estado de alguno de los operandos es null o no válido. Los operadores de igualdad ( `==`, `!=`) tenga en cuenta el estado de los operandos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#20;](../../mfc/codesnippet/cpp/colecurrency-class_10.cpp)]  
  
##  <a name="a-namesetcurrencya--colecurrencysetcurrency"></a><a name="setcurrency"></a>COleCurrency::SetCurrency  
 Llame a esta función miembro para definir las unidades y la parte fraccionaria de este **COleCurrency** objeto.  
  
```  
void SetCurrency(
    long nUnits,  
    long nFractionalUnits);
```  
  
### <a name="parameters"></a>Parámetros  
 `nUnits`, `nFractionalUnits`  
 Indicar las unidades y la parte fraccionaria (en 1/10, miles) del valor que se copiará en este **COleCurrency** objeto.  
  
### <a name="remarks"></a>Comentarios  
 Si el valor absoluto de la parte fraccionaria es mayor que 10.000, se realiza el ajuste correspondiente a las unidades, como se muestra en el tercero de los ejemplos siguientes.  
  
 Tenga en cuenta que las unidades y la parte fraccionaria se especifican mediante los valores de tipo long con signo. El cuarto de los ejemplos siguientes muestra qué sucede cuando los parámetros tienen signos diferentes.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_MFCOleContainer&#14;](../../mfc/codesnippet/cpp/colecurrency-class_11.cpp)]  
  
##  <a name="a-namesetstatusa--colecurrencysetstatus"></a><a name="setstatus"></a>COleCurrency::SetStatus  
 Llame a esta función miembro para establecer el estado (validez) de este **COleCurrency** objeto.  
  
```  
void SetStatus(CurrencyStatus  status  );
```  
  
### <a name="parameters"></a>Parámetros  
 *status*  
 El nuevo estado **COleCurrency** objeto.  
  
### <a name="remarks"></a>Comentarios  
 El *estado* el valor del parámetro se define mediante la `CurrencyStatus` tipo enumerado, que se define dentro de la **COleCurrency** clase.  
  
 `enum CurrencyStatus{`  
  
 `valid = 0,`  
  
 `invalid = 1,`  
  
 `null = 2,`  
  
 `};`  
  
 Para obtener una breve descripción de estos valores de estado, consulte la lista siguiente:  
  
- **COleCurrency::valid** indica que este **COleCurrency** objeto es válido.  
  
- **COleCurrency::invalid** indica que este **COleCurrency** objeto no es válido; es decir, su valor puede ser incorrecto.  
  
- **COleCurrency::null** indica que este **COleCurrency** objeto es null, es decir, que no se ha proporcionado ningún valor para este objeto. (Esto es "null" en el sentido de la base de datos de "no tener ningún valor," en lugar de C++ **NULL**.)  
  
    > [!CAUTION]
    >  Esta función es para situaciones de programación avanzadas. Esta función no modifica los datos de este objeto. Frecuentemente se utilizará para establecer el estado como null o no válido. Tenga en cuenta que el operador de asignación ( [operador =](#operator_eq)) y [SetCurrency](#setcurrency) establecer el estado del objeto basado en los valores de origen.  
  
## <a name="see-also"></a>Vea también  
 [Gráfico de jerarquía](../../mfc/hierarchy-chart.md)   
 [COleVariant (clase)](../../mfc/reference/colevariant-class.md)

