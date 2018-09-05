---
title: CComCurrency (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b556e724e75bb6eabc832893350126a27ad511a
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678439"
---
# <a name="ccomcurrency-class"></a>CComCurrency (clase)
`CComCurrency` tiene métodos y operadores para crear y administrar un objeto CURRENCY.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComCurrency
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::CComCurrency](#ccomcurrency)|El constructor para un objeto `CComCurrency`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::GetCurrencyPtr](#getcurrencyptr)|Devuelve la dirección de un miembro de datos `m_currency`.|  
|[CComCurrency:: Getfraction](#getfraction)|Llame a este método para devolver el componente de fracción de un objeto `CComCurrency`.|  
|[CComCurrency::GetInteger](#getinteger)|Llame a este método para devolver el componente entero de un objeto `CComCurrency`.|  
|[CComCurrency::Round](#round)|Llame a este método para redondear un objeto `CComCurrency` al valor entero más cercano.|  
|[CComCurrency::SetFraction](#setfraction)|Llame a este método para establecer el componente de fracción de un objeto `CComCurrency`.|  
|[CComCurrency::SetInteger](#setinteger)|Llame a este método para establecer el componente entero de un objeto `CComCurrency`.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::operator-](#operator_-)|Este operador se usa para restar en un objeto `CComCurrency`.|  
|[CComCurrency::operator! =](#operator_neq)|Compara dos objetos `CComCurrency` para determinar si no son iguales.|  
|[CComCurrency::operator *](#operator_star)|Este operador se usa para multiplicar en un objeto `CComCurrency`.|  
|[CComCurrency::operator * =](#operator_star_eq)|Este operador se usa para multiplicar en un objeto `CComCurrency` y asignarle el resultado.|  
|[CComCurrency::operator /](#operator_div)|Este operador se usa para dividir en un objeto `CComCurrency`.|  
|[CComCurrency::operator / =](#operator_div_eq)|Este operador se utiliza para dividir en un objeto `CComCurrency` y asignarle el resultado.|  
|[CComCurrency::operator +](#operator_add)|Este operador se usa para sumar en un objeto `CComCurrency`.|  
|[CComCurrency::operator +=](#operator_add_eq)|Este operador se usa para sumar en un objeto `CComCurrency` y asignar el resultado al objeto actual.|  
|[CComCurrency::operator <](#operator_lt)|Este operador compara dos objetos `CComCurrency` para determinar el menor.|  
|[CComCurrency::operator < =](#operator_lt_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el menor.|  
|[CComCurrency::operator =](#operator_eq)|El operador asigna el objeto `CComCurrency` a un nuevo valor.|  
|[CComCurrency::operator =](#operator_-_eq)|Este operador se usa para restar en un objeto `CComCurrency` y asignarle el resultado.|  
|[CComCurrency::operator ==](#operator_eq_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales.|  
|[CComCurrency::operator >](#operator_gt)|Este operador compara dos objetos `CComCurrency` para determinar el mayor.|  
|[CComCurrency::operator > =](#operator_gt_eq)|Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el mayor.|  
|[CComCurrency::operator moneda](#operator_currency)|Convierte un objeto de moneda.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCurrency::m_currency](#m_currency)|La variable de moneda creada por la instancia de clase.|  
  
## <a name="remarks"></a>Comentarios  
 `CComCurrency` es un contenedor para el tipo de datos de moneda. DIVISA se implementa como un valor entero de 8 bytes de dos complementos escalado por 10.000. Esto proporciona un número de punto fijo con 15 dígitos a la izquierda del separador decimal y cuatro dígitos a la derecha. El tipo de datos de moneda es muy útil para cálculos monetarios o para los cálculos de punto fijo, donde la precisión es importante.  
  
 El `CComCurrency` contenedor implementa operaciones aritméticas, asignación y comparación para este tipo de punto fijo. Las aplicaciones compatibles se han seleccionado para controlar los errores de redondeo que se pueden producir durante los cálculos de punto fijo.  
  
 El objeto `CComCurrency` da acceso a los números situados a ambos lados del separador decimal en forma de dos componentes: un componente de número entero que almacena el valor situado a la izquierda del separador decimal y un componente de fracción que almacena el valor situado a la derecha del separador decimal. El componente de fracción se almacena internamente como un valor entero entre -9999 (CY_MIN_FRACTION) y + 9.999 (CY_MAX_FRACTION). El método [CComCurrency:: Getfraction](#getfraction) devuelve un valor escalado por un factor de 10.000 (CY_SCALE).  
  
 Al especificar los enteros y fraccionarios componentes de un `CComCurrency` de objetos, recuerde que el componente de fracción es un número en el intervalo de 0 a 9999. Esto es importante cuando se trata de una divisa como el dólar estadounidense, que expresa cantidades con solo dos dígitos después del separador decimal. Aunque no se muestren los últimos dos dígitos, se deben tener en cuenta.  
  
|Valor|Posibles asignaciones CComCurrency|  
|-----------|---------------------------------------|  
|$10.50|CComCurrency (10,5000) *o* CComCurrency (10.50)|  
|$10.05|CComCurrency(10,500) *o* CComCurrency(10.05)|  
  
 Los valores CY_MIN_FRACTION, CY_MAX_FRACTION y CY_SCALE se definen en atlcur.h.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcur.h  
  
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
 *curSrc*  
 Objeto `CComCurrency` existente.  
  
 *cySrc*  
 Una variable de tipo moneda.  
  
 *bSrc*, *dSrc*, *fSrc*, *lSrc*, *sSrc*, *ulSrc, usSrc*  
 El valor inicial dado a la variable miembro `m_currency`.  
  
 *cSrc*  
 Un carácter que contiene el valor inicial dado a la variable miembro `m_currency`.  
  
 *nInteger*, *nFraction*  
 El entero y los componentes fraccionarios del valor monetario inicial. Consulte la [CComCurrency](../../atl/reference/ccomcurrency-class.md) información general para obtener más información.  
  
 *pDispSrc*  
 Un `IDispatch` puntero.  
  
 *varSrc*  
 Una variable de tipo VARIANT. La configuración regional del subproceso actual se usa para realizar la conversión.  
  
 *szSrc*  
 Una cadena ANSI o Unicode que contiene el valor inicial. La configuración regional del subproceso actual se usa para realizar la conversión.  
  
### <a name="remarks"></a>Comentarios  
 El constructor establece el valor inicial de [CComCurrency::m_currency](#m_currency)y acepta una amplia gama de tipos de datos, incluidos los números enteros, cadenas, números de punto flotante, variables de moneda y otros `CComCurrency` objetos. Si se proporciona ningún valor, `m_currency` se establece en 0.  
  
 Si se produce un error, como un desbordamiento, los constructores que carecen de una especificación de excepción vacía (**throw()**) llame a `AtlThrow` con un valor HRESULT que describe el error.  
  
 Cuando se usan valores de punto flotante o dobles para asignar un valor, tenga en cuenta que `CComCurrency(10.50)` es equivalente a `CComCurrency(10,5000)` y no `CComCurrency(10,50)`.  
  
##  <a name="getcurrencyptr"></a>  CComCurrency::GetCurrencyPtr  
 Devuelve la dirección de un miembro de datos `m_currency`.  
  
```
CURRENCY* GetCurrencyPtr() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la dirección de un `m_currency` miembro de datos  
  
##  <a name="getfraction"></a>  CComCurrency:: Getfraction  
 Llamar a este método para devolver el componente de fracción de la `CComCurrency` objeto.  
  
```
SHORT GetFraction() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el componente de fracción de la `m_currency` miembro de datos.  
  
### <a name="remarks"></a>Comentarios  
 El componente de fracción es un valor entero de 4 dígitos entre -9999 (CY_MIN_FRACTION) y + 9.999 (CY_MAX_FRACTION). `GetFraction` Devuelve este valor con escala de 10.000 (CY_SCALE). Los valores de CY_MIN_FRACTION, CY_MAX_FRACTION y CY_SCALE se definen en atlcur.h.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]  
  
##  <a name="getinteger"></a>  CComCurrency::GetInteger  
 Llame a este método para obtener el componente entero de un `CComCurrency` objeto.  
  
```
LONGLONG GetInteger() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el componente entero de la `m_currency` miembro de datos.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]  
  
##  <a name="m_currency"></a>  CComCurrency::m_currency  
 El miembro de datos de moneda.  
  
```
CURRENCY m_currency;
```  
  
### <a name="remarks"></a>Comentarios  
 Este miembro contiene la moneda acceder y manipular los métodos de esta clase.  
  
##  <a name="operator_-"></a>  CComCurrency::operator-  
 Este operador se usa para restar en un objeto `CComCurrency`.  
  
```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Un objeto `CComCurrency`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CComCurrency` objeto que representa el resultado de la resta. Si se produce un error, como un desbordamiento, llama este operador `AtlThrow` con un valor HRESULT que describe el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]  
  
##  <a name="operator_neq"></a>  CComCurrency::operator! =  
 Este operador compara dos objetos no son iguales.  
  
```
bool operator!= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Objeto `CComCurrency` que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el elemento que se compara no es igual a la `CComCurrency` objeto; en caso contrario, FALSE.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]  
  
##  <a name="operator_star"></a>  CComCurrency::operator *  
 Este operador se usa para multiplicar en un objeto `CComCurrency`.  
  
```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *nOperand*  
 Multiplicador.  
  
 *cur*  
 La `CComCurrency` objeto usado como multiplicador.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CComCurrency` objeto que representa el resultado de la multiplicación. Si se produce un error, como un desbordamiento, llama este operador `AtlThrow` con un valor HRESULT que describe el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]  
  
##  <a name="operator_star_eq"></a>  CComCurrency::operator \*=  
 Este operador se usa para multiplicar en un objeto `CComCurrency` y asignarle el resultado.  
  
```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parámetros  
 *nOperand*  
 Multiplicador.  
  
 *cur*  
 La `CComCurrency` objeto usado como multiplicador.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CComCurrency` objeto. Si se produce un error, como un desbordamiento, llama este operador `AtlThrow` con un valor HRESULT que describe el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]  
  
##  <a name="operator_div"></a>  CComCurrency::operator /  
 Este operador se usa para dividir en un objeto `CComCurrency`.  
  
```
CComCurrency operator/(long nOperand) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *nOperand*  
 Divisor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CComCurrency` objeto que representa el resultado de la división. Si el divisor es 0, se producirá un error de aserción.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]  
  
##  <a name="operator_div_eq"></a>  CComCurrency::operator / =  
 Este operador se utiliza para dividir en un objeto `CComCurrency` y asignarle el resultado.  
  
```
const CComCurrency& operator/= (long nOperand);
```  
  
### <a name="parameters"></a>Parámetros  
 *nOperand*  
 Divisor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CComCurrency` objeto. Si el divisor es 0, se producirá un error de aserción.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]  
  
##  <a name="operator_add"></a>  CComCurrency::operator +  
 Este operador se usa para sumar en un objeto `CComCurrency`.  
  
```
CComCurrency operator+(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 La `CComCurrency` objeto que se agrega al objeto original.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un `CComCurrency` objeto que representa el resultado de la suma. Si se produce un error, como un desbordamiento, llama este operador `AtlThrow` con un valor HRESULT que describe el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]  
  
##  <a name="operator_add_eq"></a>  CComCurrency::operator +=  
 Este operador se usa para sumar en un objeto `CComCurrency` y asignar el resultado al objeto actual.  
  
```
const CComCurrency& operator+= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Objeto `CComCurrency`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CComCurrency` objeto. Si se produce un error, como un desbordamiento, llama este operador `AtlThrow` con un valor HRESULT que describe el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]  
  
##  <a name="operator_lt"></a>  CComCurrency::operator &lt;  
 Este operador compara dos objetos `CComCurrency` para determinar el menor.  
  
```
bool operator<(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Un objeto `CComCurrency`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el primer objeto es menor que el segundo, FALSE en caso contrario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]  
  
##  <a name="operator_lt_eq"></a>  CComCurrency::operator &lt;=  
 Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el menor.  
  
```
bool operator<= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Un objeto `CComCurrency`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el primer objeto es menor o igual que el segundo, FALSE en caso contrario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]  
  
##  <a name="operator_eq"></a>  CComCurrency::operator =  
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
 *curSrc*  
 Un objeto `CComCurrency`.  
  
 *cySrc*  
 Una variable de tipo moneda.  
  
 *sSrc*, *fSrc*, *lSrc*, *bSrc*, *usSrc*, *dSrc*, *cSrc* , *ulSrc*, *dSrc*  
 Valor numérico que se asigna a la `CComCurrency` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CComCurrency` objeto. Si se produce un error, como un desbordamiento, llama este operador `AtlThrow` con un valor HRESULT que describe el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]  
  
##  <a name="operator_-_eq"></a>  CComCurrency::operator =  
 Este operador se usa para restar en un objeto `CComCurrency` y asignarle el resultado.  
  
```
const CComCurrency& operator-= (const CComCurrency& cur);
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Un objeto `CComCurrency`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el texto actualizado `CComCurrency` objeto. Si se produce un error, como un desbordamiento, llama este operador `AtlThrow` con un valor HRESULT que describe el error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]  
  
##  <a name="operator_eq_eq"></a>  CComCurrency::operator ==  
 Este operador compara dos objetos `CComCurrency` para determinar si son iguales.  
  
```
bool operator== (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 La `CComCurrency` objeto que se va a comparar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si los objetos son iguales (es decir, el `m_currency` los miembros de datos, tanto enteros y fraccionarios, tanto en objetos tienen el mismo valor), FALSE en caso contrario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]  
  
##  <a name="operator_gt"></a>  CComCurrency::operator &gt;  
 Este operador compara dos objetos `CComCurrency` para determinar el mayor.  
  
```
bool operator>(const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Un objeto `CComCurrency`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el primer objeto es mayor que el segundo, FALSE en caso contrario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]  
  
##  <a name="operator_gt_eq"></a>  CComCurrency::operator &gt;=  
 Este operador compara dos objetos `CComCurrency` para determinar si son iguales o cuál es el mayor.  
  
```
bool operator>= (const CComCurrency& cur) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *cur*  
 Un objeto `CComCurrency`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el primer objeto es mayor o igual que el segundo, FALSE en caso contrario.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]  
  
##  <a name="operator_currency"></a>  CComCurrency::operator moneda  
 Estos operadores se utilizan para convertir un `CComCurrency` objeto a un tipo de datos de moneda.  
  
```  
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a un objeto de moneda.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]  
  
##  <a name="round"></a>  CComCurrency::Round  
 Llame a este método para redondear la moneda en un número especificado de posiciones decimales.  
  
```
HRESULT Roundint nDecimals);
```  
  
### <a name="parameters"></a>Parámetros  
 *nDecimals*  
 El número de dígitos a la que `m_currency` se redondeará, en el intervalo de 0 a 4.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]  
  
##  <a name="setfraction"></a>  CComCurrency::SetFraction  
 Llame a este método para establecer el componente de fracción de un objeto `CComCurrency`.  
  
```
HRESULT SetFraction(SHORT nFraction);
```  
  
### <a name="parameters"></a>Parámetros  
 *nFraction*  
 El valor que se asignará al componente de fracción de la `m_currency` miembro de datos. El signo de que el componente de fracción debe ser el mismo que el componente entero y el valor debe estar en el intervalo de -9999 (CY_MIN_FRACTION) a + 9.999 (CY_MAX_FRACTION).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]  
  
##  <a name="setinteger"></a>  CComCurrency::SetInteger  
 Llame a este método para establecer el componente entero de un objeto `CComCurrency`.  
  
```
HRESULT SetInteger(LONGLONG nInteger);
```  
  
### <a name="parameters"></a>Parámetros  
 *nInteger*  
 El valor que se asignará al componente entero de la `m_currency` miembro de datos. El inicio de sesión del componente entero debe coincidir con el signo de que el componente de fracción existente.  
  
 *nInteger* debe estar en el intervalo CY_MIN_INTEGER a CY_MAX_INTEGER inclusive. Estos valores se definen en atlcur.h.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [COleCurrency (clase)](../../mfc/reference/colecurrency-class.md)   
 [MONEDA](/windows/desktop/api/wtypes/ns-wtypes-tagcy)   
 [Información general de clases](../../atl/atl-class-overview.md)
