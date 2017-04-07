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
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 4c7ab8630a4793f0363567fa00cecb8a3bc19e3b
ms.lasthandoff: 03/31/2017

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
|[CComBSTR::Append](#append)|Anexa una cadena para `m_str`.|  
|[CComBSTR::AppendBSTR](#appendbstr)|Anexa un `BSTR` a `m_str`.|  
|[CComBSTR::AppendBytes](#appendbytes)|Anexa un número especificado de bytes que se `m_str`.|  
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Crea un `BSTR` desde el primer carácter de cada elemento de la matriz safearray y lo adjunta a la `CComBSTR` objeto.|  
|[CComBSTR::AssignBSTR](#assignbstr)|Asigna un `BSTR` a `m_str`.|  
|[CComBSTR::Attach](#attach)|Asocia un `BSTR` a la `CComBSTR` objeto.|  
|[CComBSTR::BSTRToArray](#bstrtoarray)|Crea una matriz unidimensional safearray basado en cero donde cada elemento de la matriz es un carácter de la `CComBSTR` objeto.|  
|[CComBSTR::ByteLength](#bytelength)|Devuelve la longitud de `m_str` en bytes.|  
|[CComBSTR::Copy](#copy)|Devuelve una copia de `m_str`.|  
|[CComBSTR::CopyTo](#copyto)|Devuelve una copia de `m_str` a través de un **[out]** parámetro|  
|[CComBSTR::Detach](#detach)|Desasocia `m_str` desde el `CComBSTR` objeto.|  
|[CComBSTR::Empty](#empty)|Libera `m_str`.|  
|[CComBSTR::Length](#length)|Devuelve la longitud de `m_str`.|  
|[CComBSTR::LoadString](#loadstring)|Carga un recurso de cadena.|  
|[CComBSTR::ReadFromStream](#readfromstream)|Carga un `BSTR` objeto desde una secuencia.|  
|[CComBSTR::ToLower](#tolower)|Convierte la cadena a minúsculas.|  
|[CComBSTR::ToUpper](#toupper)|Convierte la cadena a mayúsculas.|  
|[CComBSTR::WriteToStream](#writetostream)|Guarda `m_str` en una secuencia.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](#operator_bstr)|Conversiones de un `CComBSTR` el objeto a un `BSTR`.|  
|[¡CComBSTR::operator!](#operator_not)|Devuelve `true` o `false`, dependiendo de si `m_str`es `NULL`.|  
|[CComBSTR::operator! =](#operator_neq)|Compara una `CComBSTR` con una cadena.|  
|[CComBSTR::operator siguiente](#operator_amp)|Devuelve la dirección de `m_str`.|  
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
 El `CComBSTR` clase es un contenedor de `BSTR`s, que son cadenas de longitud fija. La longitud se almacena como un entero en la ubicación de memoria que precede a los datos de la cadena.  
  
 A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) está terminada en null después de la última cuenta carácter pero también puede contener caracteres nulos incrustados dentro de la cadena. La longitud de cadena viene determinada por el número de caracteres, no el primer carácter nulo.  
  
> [!NOTE]
>  La `CComBSTR` clase proporciona un número de miembros (constructores, operadores de asignación y operadores de comparación) que toman cadenas ANSI o Unicode como argumentos. Las versiones ANSI de estas funciones son menos eficientes que sus equivalentes de Unicode como cadenas Unicode temporales a menudo se crean internamente. Para mejorar la eficacia, utilice las versiones de Unicode siempre que sea posible.  
  
> [!NOTE]
>  Debido al comportamiento de búsqueda mejorada que se implementa en Visual Studio. NET, un código como `bstr = L"String2" + bstr;`, que puede haber compilado en versiones anteriores, en su lugar, se debería implementar como `bstr = CStringW(L"String2") + bstr`.  
  
 Para obtener una lista de advertencias al utilizar `CComBSTR`, consulte [programar con CComBSTR](../../atl/programming-with-ccombstr-atl.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="append"></a>CComBSTR::Append  
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
 [in] Una cadena de caracteres terminadas en cero que se anexará. Puede pasar una cadena de Unicode a través de la **LPCOLESTR** sobrecarga o una cadena ANSI a través de la `LPCSTR` versión.  
  
 `nLen`  
 [in] El número de caracteres de `lpsz` para anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`resultado correcto o la norma `HRESULT` valor de error.  
  
### <a name="remarks"></a>Comentarios  
 Una cadena ANSI se convertirá a Unicode antes de que se va a anexar.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]  
  
##  <a name="appendbstr"></a>CComBSTR::AppendBSTR  
 Anexa el texto especificado `BSTR` a [m_str](#m_str).  
  
```
HRESULT AppendBSTR(BSTR p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Un `BSTR` para anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`resultado correcto o la norma `HRESULT` valor de error.  
  
### <a name="remarks"></a>Comentarios  
 No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº 33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]  
  
##  <a name="appendbytes"></a>CComBSTR::AppendBytes  
 Anexa el número especificado de bytes a [m_str](#m_str) sin realizar ninguna conversión.  
  
```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpsz`  
 [in] Un puntero a una matriz de bytes que se va a anexar.  
  
 `p`  
 [in] El número de bytes que se va a anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`resultado correcto o la norma `HRESULT` valor de error.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]  
  
##  <a name="arraytobstr"></a>CComBSTR::ArrayToBSTR  
 Libera cualquier cadena existente que se mantienen en la `CComBSTR` objeto, a continuación, crea un `BSTR` desde el primer carácter de cada elemento de la matriz safearray y lo adjunta a la `CComBSTR` objeto.  
  
```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pSrc`  
 [in] Safearray que contiene los elementos utilizados para crear la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`resultado correcto o la norma `HRESULT` valor de error.  
  
##  <a name="assignbstr"></a>CComBSTR::AssignBSTR  
 Asigna un `BSTR` a [m_str](#m_str).  
  
```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrSrc`  
 [in] A `BSTR` para asignar a la corriente `CComBSTR` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`resultado correcto o la norma `HRESULT` valor de error.  
  
##  <a name="attach"></a>CComBSTR::Attach  
 Asocia un `BSTR` a la `CComBSTR` objeto estableciendo la [m_str](#m_str) miembro *src*.  
  
```
void Attach(BSTR src) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *src*  
 [in] El `BSTR` para adjuntar al objeto.  
  
### <a name="remarks"></a>Comentarios  
 No pase una cadena de caracteres anchos normal a este método. El compilador no puede detectar el error y se producirán errores de tiempo de ejecución.  
  
> [!NOTE]
>  Este método producirá una aserción si `m_str` no es **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="bstrtoarray"></a>CComBSTR::BSTRToArray  
 Crea una matriz unidimensional safearray basado en cero donde cada elemento de la matriz es un carácter de la `CComBSTR` objeto.  
  
```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `ppArray`  
 [out] Puntero a la matriz safearray utilizado para almacenar los resultados de la función.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`resultado correcto o la norma `HRESULT` valor de error.  
  
##  <a name="bytelength"></a>CComBSTR::ByteLength  
 Devuelve el número de bytes en `m_str`, sin incluir el carácter nulo de terminación.  
  
```
unsigned int ByteLength() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la [m_str](#m_str) miembro en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Devuelve 0 si `m_str` es **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]  
  
##  <a name="ccombstr"></a>CComBSTR::CComBSTR  
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
 [in] Cadena que se va a copiar. La versión Unicode especifica un **LPCOLESTR**; la versión ANSI un `LPCSTR`.  
  
 `pSrc`  
 [in] Cadena que se va a copiar. La versión Unicode especifica un **LPCOLESTR**; la versión ANSI un `LPCSTR`.  
  
 *src*  
 [in] Objeto `CComBSTR`.  
  
 `guid`  
 [in] Una referencia a un **GUID** estructura.  
  
### <a name="remarks"></a>Comentarios  
 El constructor de copia establece `m_str` a una copia de la `BSTR` miembro de *src*. El **REFGUID** constructor convierte el **GUID** en una cadena mediante **StringFromGUID2** y almacena el resultado.  
  
 Los otros constructores establecen `m_str` en una copia de la cadena especificada. Si se pasa un valor para `nSize`, solo se copiarán `nSize` caracteres, seguidos de un carácter nulo.  
  
 `CComBSTR` admite la semántica de transferencia de recursos. Puede usar el constructor de movimiento (el constructor que toma una referencia rvalue ( `&&`) para crear un objeto nuevo que utiliza los mismos datos subyacentes que el objeto antiguo se pasa como argumento, sin la sobrecarga de copiar el objeto.  
  
 El destructor libera la cadena a la que apunta `m_str`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]  
  
##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR  
 Destructor.  
  
```
~CComBSTR();
```  
  
### <a name="remarks"></a>Comentarios  
 El destructor libera la cadena a la que apunta `m_str`.  
  
##  <a name="copy"></a>CComBSTR::Copy  
 Asigna y devuelve una copia de `m_str`.  
  
```
BSTR Copy() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una copia de la [m_str](#m_str) miembro. If `m_str` is **NULL**, returns **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]  
  
##  <a name="copyto"></a>CComBSTR::CopyTo  
 Asigna y devuelve una copia de [m_str](#m_str) a través del parámetro.  
  
```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *pbstr*  
 [out] La dirección de un `BSTR` en el que se va a devolver la cadena asignada por este método.  
  
 `pvarDest`  
 [out] La dirección de un **VARIANT** en el que se va a devolver la cadena asignada por este método.  
  
### <a name="return-value"></a>Valor devuelto  
 Un estándar `HRESULT` valor que indica el éxito o fracaso de la copia.  
  
### <a name="remarks"></a>Comentarios  
 Después de llamar a este método, el **VARIANT** señalada por `pvarDest` será del tipo `VT_BSTR`.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]  
  
##  <a name="detach"></a>CComBSTR::Detach  
 Desasocia [m_str](#m_str) desde el `CComBSTR` objeto y conjuntos de `m_str` a **NULL**.  
  
```
BSTR Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El `BSTR` asociados con el `CComBSTR` objeto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº 40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]  
  
##  <a name="empty"></a>CComBSTR::Empty  
 Libera la [m_str](#m_str) miembro.  
  
```
void Empty() throw();
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]  
  
##  <a name="length"></a>CComBSTR::Length  
 Devuelve el número de caracteres de `m_str`, sin incluir el carácter nulo de terminación.  
  
```
unsigned int Length() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La longitud de la [m_str](#m_str) miembro.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]  
  
##  <a name="loadstring"></a>CComBSTR::LoadString  
 Carga un recurso de cadena especificado por `nID` y lo almacena en este objeto.  
  
```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 Vea [LoadString](http://msdn.microsoft.com/library/windows/desktop/ms647486) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la cadena se ha cargado correctamente; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 La primera función carga el recurso desde el módulo identificado por el usuario a través de la `hInst` parámetro. La segunda función carga el recurso desde el módulo de recursos asociado con la [CComModule](../../atl/reference/ccommodule-class.md)-deriva el objeto que se usa en este proyecto.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]  
  
##  <a name="m_str"></a>CComBSTR::m_str  
 Contiene el `BSTR` asociados con el `CComBSTR` objeto.  
  
```
BSTR m_str;
```  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]  
  
##  <a name="operator_bstr"></a>CComBSTR::operator BSTR  
 Conversiones de un `CComBSTR` el objeto a un `BSTR`.  
  
```  
operator BSTR() const throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Te permite pasar `CComBSTR` objetos a funciones que tienen **[in] BSTR** parámetros.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CComBSTR::m_str](#m_str).  
  
##  <a name="operator_not"></a>¡CComBSTR::operator!  
 Comprueba si `BSTR` cadena es NULL.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la [m_str](#m_str) miembro es **NULL**; en caso contrario, **false**.  
  
### <a name="remarks"></a>Comentarios  
 Este operador solo busca un valor NULL, no para una cadena vacía.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="operator_neq"></a>CComBSTR::operator! =  
 Devuelve el lógico opuesto [operador ==](#operator_eq_eq).  
  
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
 Devuelve **true** si no es igual que el elemento que se están comparando el `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 `CComBSTR`s se comparan textualmente en el contexto de configuración regional de predeterminada del usuario. El operador de comparación final solo compara la cadena independiente con **NULL**.  
  
##  <a name="operator_amp"></a>CComBSTR::operator&amp;  
 Devuelve la dirección de la `BSTR` almacenado en el [m_str](#m_str) miembro.  
  
```
BSTR* operator&() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 `CComBstr operator &`tiene una aserción especial asociado para ayudar a identificar pérdidas de memoria. El programa producirá una aserción cuando el `m_str` se inicializa un miembro. Esta aserción se creó para identificar las situaciones donde un programador utiliza el `& operator` para asignar un nuevo valor a `m_str` miembro sin liberar la primera asignación de `m_str`. Si `m_str` es igual a NULL, el programa se da por supuesto que m_str no se ha asignado todavía. En este caso, el programa no producirá una aserción.  
  
 Esta aserción no está habilitada de forma predeterminada. Definir `ATL_CCOMBSTR_ADDRESS_OF_ASSERT` para habilitar esta aserción.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities nº 46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities #47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]  
  
##  <a name="operator_add_eq"></a>CComBSTR::operator +=  
 Anexa una cadena para el `CComBSTR` objeto.  
  
```
CComBSTR& operator+= (const CComBSTR& bstrSrc);  
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `bstrSrc`  
 [in] Un `CComBSTR` objeto que se va a anexar.  
  
 `pszSrc`  
 [in] Una cadena terminada en cero que se anexará.  
  
### <a name="remarks"></a>Comentarios  
 `CComBSTR`s se comparan textualmente en el contexto de configuración regional de predeterminada del usuario. El **LPCOLESTR** comparación se realiza utilizando `memcmp` en los datos sin procesar de cada cadena. El `LPCSTR` comparación se realiza en la misma forma una vez que copie de Unicode de un archivo temporal de `pszSrc` se ha creado. El operador de comparación final solo compara la cadena independiente con **NULL**.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]  
  
##  <a name="operator_lt"></a>CComBSTR::operator&lt;  
 Compara una `CComBSTR` con una cadena.  
  
```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el elemento que se va a comparar es menor que el `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación se realiza utilizando la configuración regional de predeterminada del usuario.  
  
##  <a name="operator_eq"></a>CComBSTR::operator =  
 Establece el [m_str](#m_str) miembro a una copia de `pSrc` o a una copia de la `BSTR` miembro de *src*. Mueve el operador de asignación de movimiento `src` sin copiarlo.   
  
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
  
##  <a name="operator_eq_eq"></a>CComBSTR::operator ==  
 Compara una `CComBSTR` con una cadena. `CComBSTR`s se comparan textualmente en el contexto de configuración regional de predeterminada del usuario.  
  
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
 Devuelve **true** si el elemento que se va a comparar es igual que el `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 El operador de comparación final solo compara la cadena independiente con **NULL**.  
  
##  <a name="operator_gt"></a>CComBSTR::operator&gt;  
 Compara una `CComBSTR` con una cadena.  
  
```
bool operator>(const CComBSTR& bstrSrc) const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si es mayor que el elemento que se están comparando el `CComBSTR` objeto; en caso contrario, devuelve **false**.  
  
### <a name="remarks"></a>Comentarios  
 La comparación se realiza utilizando la configuración regional de predeterminada del usuario.  
  
##  <a name="readfromstream"></a>CComBSTR::ReadFromStream  
 Establece el [m_str](#m_str) miembro a la `BSTR` incluidos en la secuencia especificada.  
  
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
 [!code-cpp[NVC_ATL_Utilities #44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]  
  
##  <a name="tolower"></a>CComBSTR::ToLower  
 Convierte la cadena a minúsculas.  
  
```
HRESULT ToLower() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Vea **CharLowerBuff** para obtener más información sobre cómo se realiza la conversión.  
  
##  <a name="toupper"></a>CComBSTR::ToUpper  
 Convierte la cadena a mayúsculas.  
  
```
HRESULT ToUpper() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar.  
  
### <a name="remarks"></a>Comentarios  
 Vea **CharUpperBuff** para obtener más información sobre cómo se realiza la conversión.  
  
##  <a name="writetostream"></a>CComBSTR::WriteToStream  
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
 Puede volver a crear una cadena BSTR con el contenido de la secuencia utilizando el [ReadFromStream](#readfromstream) (función).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities #45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Macros de conversión de cadena MFC y ATL](string-conversion-macros.md)

