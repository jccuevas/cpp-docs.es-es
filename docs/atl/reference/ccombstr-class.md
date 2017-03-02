---
title: CComBSTR (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComBSTR
- CComBSTR
- ATL.CComBSTR
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: 21
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
ms.sourcegitcommit: 8cdedc5cfac9d49df812ae6fcfcc548201b1edb5
ms.openlocfilehash: e7b61a5826836e7d26a0d470631d7230f7b7be56
ms.lasthandoff: 02/24/2017

---
# <a name="ccombstr-class"></a>CComBSTR (clase)
Esta clase es un contenedor de `BSTR`s.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComBSTR
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComBSTR::CComBSTR](#ccombstr)|El constructor.|  
|[CComBSTR:: ~ CComBSTR](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComBSTR::Append](#append)|Anexa una cadena a `m_str`.|  
|[CComBSTR::AppendBSTR](#appendbstr)|Anexa un `BSTR` a `m_str`.|  
|[CComBSTR::AppendBytes](#appendbytes)|Anexa un número especificado de bytes a `m_str`.|  
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crea un `BSTR` desde el primer carácter de cada elemento de la matriz safearray y lo adjunta a la `CComBSTR` objeto.|  
|[CComBSTR::AssignBSTR](#assignbstr)|Asigna un `BSTR` a `m_str`.|  
|[CComBSTR::Attach](#attach)|Asocia un `BSTR` a la `CComBSTR` objeto.|  
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crea un safearray unidimensional de base cero, donde cada elemento de la matriz es un carácter de la `CComBSTR` objeto.|  
|[CComBSTR::ByteLength](#bytelength)|Devuelve la longitud de `m_str` en bytes.|  
|[CComBSTR::Copy](#copy)|Devuelve una copia de `m_str`.|  
|[CComBSTR::CopyTo](#copyto)|Devuelve una copia de `m_str` a través de un **[out]** parámetro|  
|[CComBSTR::Detach](#detach)|Desasocia `m_str` desde el `CComBSTR` objeto.|  
|[CComBSTR::Empty](#empty)|Libera `m_str`.|  
|[CComBSTR::Length](#length)|Devuelve la longitud de `m_str`.|  
|[CComBSTR::LoadString](#loadstring)|Carga un recurso de cadena.|  
|[CComBSTR::ReadFromStream](#readfromstream)|Carga un `BSTR` objeto de una secuencia.|  
|[CComBSTR::ToLower](#tolower)|Convierte la cadena a minúsculas.|  
|[CComBSTR::ToUpper](#toupper)|Convierte la cadena a mayúsculas.|  
|[CComBSTR::WriteToStream](#writetostream)|Guarda `m_str` en una secuencia.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](#operator_bstr)|Conversiones de un `CComBSTR` objeto a un `BSTR`.|  
|[¡CComBSTR::operator!](#operator_not)|Devuelve `true` o `false`, dependiendo de si `m_str`es `NULL`.|  
|[CComBSTR::operator! =](#operator_neq)|Compara una `CComBSTR` con una cadena.|  
|[CComBSTR::operator aspecto](#operator_amp)|Devuelve la dirección de `m_str`.|  
|[CComBSTR::operator +=](#operator_add_eq)|Anexa un `CComBSTR` al objeto.|  
|[CComBSTR::operator](#operator_lt)|Compara una `CComBSTR` con una cadena.|  
|[CComBSTR::operator =](#operator_eq)|Asigna un valor a `m_str`.|  
|[CComBSTR::operator ==](#operator_eq_eq)|Compara una `CComBSTR` con una cadena.|  
|[CComBSTR::operator >](#operator_gt)|Compara una `CComBSTR` con una cadena.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComBSTR::m_str](#m_str)|Contiene el `BSTR` asociados con el `CComBSTR` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 El `CComBSTR` clase es un contenedor de `BSTR`s, que son cadenas de longitud fija. La longitud se almacena como un entero en la ubicación de memoria antes de los datos en la cadena.  
  
 Un [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) está terminada en null después de la última cuenta carácter pero también puede contener caracteres nulos incrustados dentro de la cadena. La longitud de la cadena se determina por el número de caracteres, no el primer carácter nulo.  
  
> [!NOTE]
>  La `CComBSTR` clase proporciona un número de miembros (constructores, operadores de asignación y operadores de comparación) que toman cadenas ANSI o Unicode como argumentos. Las versiones ANSI de estas funciones son menos eficientes que sus equivalentes Unicode como cadenas Unicode temporales se crean a menudo internamente. Para mejorar la eficacia, utilice las versiones de Unicode siempre que sea posible.  
  
> [!NOTE]
>  Debido al comportamiento de búsqueda mejorada implementado en Visual Studio. NET, un código como `bstr = L"String2" + bstr;`, que puede haber compilado en versiones anteriores, en su lugar, se debería implementar como `bstr = CStringW(L"String2") + bstr`.  
  
 Para obtener una lista de precauciones al utilizar `CComBSTR`, consulte [programar con CComBSTR](../../atl/programming-with-ccombstr-atl.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-nameappenda--ccombstrappend"></a><a name="append"></a>CComBSTR::Append  
 Anexa una `lpsz` o `BSTR` miembro de `bstrSrc` a [m_str](#m_str).  
  
```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrSrc`  
 [in] Un `CComBSTR` objeto que se va a anexar.  
  
 *CH*  
 [in] Un carácter que se va a anexar.  
  
 `lpsz`  
 [in] Para anexar una cadena de caracteres terminadas en cero. Puede pasar una cadena Unicode a través de la **LPCOLESTR** sobrecarga o una cadena ANSI a través de la `LPCSTR` versión.  
  
 `nLen`  
 [in] El número de caracteres de `lpsz` para anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`éxito o cualquier propiedad estándar `HRESULT` valor de error.  
  
### <a name="remarks"></a>Comentarios  
 Una cadena ANSI se convertirán a Unicode antes de que se ha agregado.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#32;](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]  
  
##  <a name="a-nameappendbstra--ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::AppendBSTR  
 Anexa el texto especificado `BSTR` a [m_str](#m_str).  
  
```
HRESULT AppendBSTR(BSTR p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Un `BSTR` para anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`éxito o cualquier propiedad estándar `HRESULT` valor de error.  
  
### <a name="remarks"></a>Comentarios  
 No pase una cadena de caracteres anchos común a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&33;](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]  
  
##  <a name="a-nameappendbytesa--ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::AppendBytes  
 Anexa el número especificado de bytes a [m_str](#m_str) sin conversión.  
  
```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 [in] Puntero a una matriz de bytes que se va a anexar.  
  
 `p`  
 [in] El número de bytes que se va a anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`éxito o cualquier propiedad estándar `HRESULT` valor de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#34;](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]  
  
##  <a name="a-namearraytobstra--ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArrayToBSTR  
 Libera cualquier cadena existente en el `CComBSTR` objeto, a continuación, crea un `BSTR` desde el primer carácter de cada elemento de la matriz safearray y lo adjunta a la `CComBSTR` objeto.  
  
```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pSrc`  
 [in] Safearray que contiene los elementos utilizados para crear la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`éxito o cualquier propiedad estándar `HRESULT` valor de error.  
  
##  <a name="a-nameassignbstra--ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::AssignBSTR  
 Asigna un `BSTR` a [m_str](#m_str).  
  
```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrSrc`  
 [in] Un `BSTR` para asignar a la corriente `CComBSTR` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`éxito o cualquier propiedad estándar `HRESULT` valor de error.  
  
##  <a name="a-nameattacha--ccombstrattach"></a><a name="attach"></a>CComBSTR::Attach  
 Asocia un `BSTR` a la `CComBSTR` objeto estableciendo la [m_str](#m_str) miembro *src*.  
  
```
void Attach(BSTR src) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *src*  
 [in] El `BSTR` adjuntar el objeto.  
  
### <a name="remarks"></a>Comentarios  
 No pase una cadena de caracteres anchos común a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.  
  
> [!NOTE]
>  Este método producirá una aserción si `m_str` no es **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#35;](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="a-namebstrtoarraya--ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR::BSTRToArray  
 Crea un safearray unidimensional de base cero, donde cada elemento de la matriz es un carácter de la `CComBSTR` objeto.  
  
```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ppArray`  
 [out] Puntero a la matriz safearray utilizado para almacenar los resultados de la función.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`éxito o cualquier propiedad estándar `HRESULT` valor de error.  
  
##  <a name="a-namebytelengtha--ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR::ByteLength  
 Devuelve el número de bytes de `m_str`, excepto el carácter nulo de terminación.  
  
```
unsigned int ByteLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la [m_str](#m_str) miembro en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve 0 si `m_str` es **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#36;](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]  
  
##  <a name="a-nameccombstra--ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR::CComBSTR  
 El constructor. El constructor predeterminado establece la [m_str](#m_str) miembro **NULL**.  
  
```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);  
CComBSTR(REFGUID  guid);  
CComBSTR(int nSize);  
CComBSTR(int nSize, LPCOLESTR sz);  
CComBSTR(int nSize, LPCSTR sz);  
CComBSTR(LPCOLESTR pSrc);  
CComBSTR(LPCSTR pSrc);  
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="parameters"></a>Parámetros  
 `nSize`  
 [in] El número de caracteres que se deben copiar de `sz` o el tamaño inicial en caracteres para `CComBSTR`.  
  
 `sz`  
 [in] Cadena que se va a copiar. Especifica la versión Unicode un **LPCOLESTR**; la versión ANSI especifica un `LPCSTR`.  
  
 `pSrc`  
 [in] Cadena que se va a copiar. Especifica la versión Unicode un **LPCOLESTR**; la versión ANSI especifica un `LPCSTR`.  
  
 *src*  
 [in] Objeto `CComBSTR`.  
  
 `guid`  
 [in] Una referencia a un **GUID** estructura.  
  
### <a name="remarks"></a>Comentarios  
 El constructor de copia establece `m_str` a una copia de la `BSTR` miembro de *src*. El **REFGUID** constructor convierte el **GUID** en una cadena mediante **StringFromGUID2** y almacena el resultado.  
  
 Los otros constructores establecen `m_str` en una copia de la cadena especificada. Si se pasa un valor para `nSize`, solo se copiarán `nSize` caracteres, seguidos de un carácter nulo.  
  
 `CComBSTR` admite la semántica de transferencia de recursos. Puede utilizar el constructor de movimiento (el constructor que toma una referencia rvalue ( `&&`) para crear un nuevo objeto que usa los mismos datos subyacentes, como el antiguo objeto pasar como argumento, sin la sobrecarga de copiar el objeto.  
  
 El destructor libera la cadena a la que apunta `m_str`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#37;](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]  
  
##  <a name="a-namedtora--ccombstrccombstr"></a><a name="dtor"></a>CComBSTR:: ~ CComBSTR  
 Destructor.  
  
```
~CComBSTR();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera la cadena a la que apunta `m_str`.  
  
##  <a name="a-namecopya--ccombstrcopy"></a><a name="copy"></a>CComBSTR::Copy  
 Asigna y devuelve una copia de `m_str`.  
  
```
BSTR Copy() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia de la [m_str](#m_str) miembro. If `m_str` is **NULL**, returns **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#38;](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]  
  
##  <a name="a-namecopytoa--ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::CopyTo  
 Asigna y devuelve una copia de [m_str](#m_str) a través del parámetro.  
  
```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pbstr*  
 [out] La dirección de un `BSTR` en el que se va a devolver la cadena asignada por este método.  
  
 `pvarDest`  
 [out] La dirección de un **VARIANT** para devolver la cadena asignada por este método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un estándar `HRESULT` valor que indica el éxito o fracaso de la copia.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a este método, el **VARIANT** señala `pvarDest` será del tipo `VT_BSTR`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#39;](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]  
  
##  <a name="a-namedetacha--ccombstrdetach"></a><a name="detach"></a>CComBSTR::Detach  
 Desasocia [m_str](#m_str) desde el `CComBSTR` objeto y establece `m_str` a **NULL**.  
  
```
BSTR Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `BSTR` asociados con el `CComBSTR` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&40;](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]  
  
##  <a name="a-nameemptya--ccombstrempty"></a><a name="empty"></a>CComBSTR::Empty  
 Libera el [m_str](#m_str) miembro.  
  
```
void Empty() throw();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities nº&41;](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]  
  
##  <a name="a-namelengtha--ccombstrlength"></a><a name="length"></a>CComBSTR::Length  
 Devuelve el número de caracteres de `m_str`, excepto el carácter nulo de terminación.  
  
```
unsigned int Length() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la [m_str](#m_str) miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#42;](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]  
  
##  <a name="a-nameloadstringa--ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::LoadString  
 Carga un recurso de cadena especificado por `nID` y lo almacena en este objeto.  
  
```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 Consulte [LoadString](http://msdn.microsoft.com/library/windows/desktop/ms647486) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la cadena se ha cargado correctamente; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 La primera función carga el recurso desde el módulo identificado por el usuario a través de la `hInst` parámetro. La segunda función carga el recurso desde el módulo de recursos asociado con la [CComModule](../../atl/reference/ccommodule-class.md)-derivadas objeto usado en este proyecto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#43;](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]  
  
##  <a name="a-namemstra--ccombstrmstr"></a><a name="m_str"></a>CComBSTR::m_str  
 Contiene el `BSTR` asociados con el `CComBSTR` objeto.  
  
```
BSTR m_str;
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#49;](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]  
  
##  <a name="a-nameoperatorbstra--ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::operator BSTR  
 Conversiones de un `CComBSTR` objeto a un `BSTR`.  
  
```  
operator BSTR() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Le permite pasar `CComBSTR` objetos a las funciones que tienen **[in] BSTR** parámetros.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CComBSTR::m_str](#m_str).  
  
##  <a name="a-nameoperatornota--ccombstroperator-"></a><a name="operator_not"></a>¡CComBSTR::operator!  
 Comprueba si `BSTR` cadena es NULL.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la [m_str](#m_str) miembro es **NULL**; en caso contrario, **false**.  
  
### <a name="remarks"></a>Comentarios  
 Este operador sólo comprueba el valor NULL, no de una cadena vacía.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#35;](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="a-nameoperatorneqa--ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::operator! =  
 Devuelve el valor contrario lógico de [operador ==](#operator_eq_eq).  
  
```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrSrc`  
 [in] Objeto `CComBSTR`.  
  
 `pszSrc`  
 [in] Una cadena terminada en cero.  
  
 `nNull`  
 [in] Debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si no es igual que el elemento está comparando el `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 `CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. El operador de comparación final sólo compara la cadena contenida en **NULL**.  
  
##  <a name="a-nameoperatorampa--ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::operator&amp;  
 Devuelve la dirección de la `BSTR` almacenado en el [m_str](#m_str) miembro.  
  
```
BSTR* operator&() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 `CComBstr operator &`tiene una aserción especial asociado para ayudar a identificar pérdidas de memoria. El programa producirá una aserción cuando el `m_str` se inicializa el miembro. Esta aserción se creó para identificar las situaciones donde los programadores utilizan la `& operator` para asignar un nuevo valor a `m_str` miembro sin liberar la primera asignación de `m_str`. Si `m_str` es igual a NULL, el programa asume que m_str no se ha asignado todavía. En este caso, el programa no producirá una aserción.  
  
 Esta aserción no está habilitada de forma predeterminada. Definir `ATL_CCOMBSTR_ADDRESS_OF_ASSERT` para habilitar esta aserción.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities nº&46;](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities&#47;](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]  
  
##  <a name="a-nameoperatoraddeqa--ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::operator +=  
 Anexa una cadena a la `CComBSTR` objeto.  
  
```
CComBSTR& operator+= (const CComBSTR& bstrSrc);  
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrSrc`  
 [in] Un `CComBSTR` objeto que se va a anexar.  
  
 `pszSrc`  
 [in] Una cadena terminada en cero para anexar.  
  
### <a name="remarks"></a>Comentarios  
 `CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario. El **LPCOLESTR** comparación se realiza utilizando `memcmp` en los datos sin procesar de cada cadena. El `LPCSTR` comparación se realiza de la misma manera cuando copie de Unicode de un archivo temporal de `pszSrc` se ha creado. El operador de comparación final sólo compara la cadena contenida en **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&48;](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]  
  
##  <a name="a-nameoperatorlta--ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::operator&lt;  
 Compara una `CComBSTR` con una cadena.  
  
```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el elemento que se va a comparar es menor que el `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación se realiza mediante la configuración regional predeterminada del usuario.  
  
##  <a name="a-nameoperatoreqa--ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::operator =  
 Establece la [m_str](#m_str) miembro a una copia de `pSrc` o a una copia de la `BSTR` miembro de *src*. El operador de asignación de desplazamiento mueve `src` sin copiarlo.   
  
```
CComBSTR& operator= (const CComBSTR& src);  
CComBSTR& operator= (LPCOLESTR pSrc);  
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="remarks"></a>Comentarios  
 El `pSrc` parámetro especifica un **LPCOLESTR** para las versiones de Unicode o `LPCSTR` para versiones ANSI.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CComBSTR::Copy](#copy).  
  
##  <a name="a-nameoperatoreqeqa--ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::operator ==  
 Compara una `CComBSTR` con una cadena. `CComBSTR`s se comparan textualmente en el contexto de la configuración regional predeterminada del usuario.  
  
```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrSrc`  
 [in] Objeto `CComBSTR`.  
  
 `pszSrc`  
 [in] Una cadena terminada en cero.  
  
 `nNull`  
 [in] Debe ser **NULL**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el elemento de comparación es igual a la `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 El operador de comparación final sólo compara la cadena contenida en **NULL**.  
  
##  <a name="a-nameoperatorgta--ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::operator&gt;  
 Compara una `CComBSTR` con una cadena.  
  
```
bool operator>(const CComBSTR& bstrSrc) const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si es mayor que el elemento está comparando el `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación se realiza mediante la configuración regional predeterminada del usuario.  
  
##  <a name="a-namereadfromstreama--ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR::ReadFromStream  
 Establece la [m_str](#m_str) miembro a la `BSTR` contenidos en la secuencia especificada.  
  
```
HRESULT ReadFromStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Un puntero a la [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfaz en la secuencia que contiene los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 **ReadToStream** requiere que el contenido de la secuencia en la posición actual para que sea compatible con el formato de datos que se escribe mediante una llamada a [WriteToStream](#writetostream).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#44;](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]  
  
##  <a name="a-nametolowera--ccombstrtolower"></a><a name="tolower"></a>CComBSTR::ToLower  
 Convierte la cadena a minúsculas.  
  
```
HRESULT ToLower() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Consulte **CharLowerBuff** para obtener más información sobre cómo se realiza la conversión.  
  
##  <a name="a-nametouppera--ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::ToUpper  
 Convierte la cadena a mayúsculas.  
  
```
HRESULT ToUpper() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Consulte **CharUpperBuff** para obtener más información sobre cómo se realiza la conversión.  
  
##  <a name="a-namewritetostreama--ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::WriteToStream  
 Guarda el [m_str](#m_str) miembro en una secuencia.  
  
```
HRESULT WriteToStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pStream`  
 [in] Un puntero a la [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfaz en una secuencia.  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Puede volver a crear una cadena BSTR del contenido de la secuencia utilizando el [ReadFromStream](#readfromstream) (función).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities nº&45;](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Macros de conversión de cadenas MFC y ATL](http://msdn.microsoft.com/library/8f53659e-0464-4424-97db-6b8453c49863)

