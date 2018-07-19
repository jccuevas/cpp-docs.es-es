---
title: CComSafeArray (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
dev_langs:
- C++
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 28be6dffc2f991ad08c83c508af2c401d5eecc37
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959376"
---
# <a name="ccomsafearray-class"></a>CComSafeArray (clase)
Esta clase es un contenedor para el `SAFEARRAY` estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 Tipo de datos que se va a almacenar en la matriz.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeArray::CComSafeArray](#ccomsafearray)|El constructor.|  
|[CComSafeArray:: ~ CComSafeArray](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeArray:: Add](#add)|Agrega uno o más elementos, o un `SAFEARRAY` estructura, un `CComSafeArray`.|  
|[CComSafeArray::Attach](#attach)|Asocia un `SAFEARRAY` estructura a un `CComSafeArray` objeto.|  
|[CComSafeArray:: CopyFrom](#copyfrom)|Copia el contenido de un `SAFEARRAY` estructura en el `CComSafeArray` objeto.|  
|[CComSafeArray::CopyTo](#copyto)|Crea una copia del objeto `CComSafeArray` .|  
|[CComSafeArray::Create](#create)|Crea un objeto `CComSafeArray`.|  
|[CComSafeArray::Destroy](#destroy)|Destruye un objeto `CComSafeArray`.|  
|[CComSafeArray:: Detach](#detach)|Desasocia un `SAFEARRAY` desde un `CComSafeArray` objeto.|  
|[CComSafeArray:: GetAt](#getat)|Recupera un único elemento de una matriz unidimensional.|  
|[CComSafeArray::GetCount](#getcount)|Devuelve el número de elementos de la matriz.|  
|[CComSafeArray::GetDimensions](#getdimensions)|Devuelve el número de dimensiones de la matriz.|  
|[CComSafeArray::GetLowerBound](#getlowerbound)|Devuelve el límite inferior de una determinada dimensión de la matriz.|  
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Devuelve la dirección del miembro de datos `m_psa` .|  
|[CComSafeArray::GetType](#gettype)|Devuelve el tipo de datos almacenado en la matriz.|  
|[CComSafeArray::GetUpperBound](#getupperbound)|Devuelve el límite superior de cualquier dimensión de la matriz.|  
|[CComSafeArray::IsSizable](#issizable)|Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray` .|  
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Recupera un único elemento de una matriz multidimensional.|  
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Establece el valor de un elemento de una matriz multidimensional.|  
|[CComSafeArray::Resize](#resize)|Cambia el tamaño de un objeto `CComSafeArray` .|  
|[SetAt](#setat)|Establece el valor de un elemento de una matriz unidimensional.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Convierte un valor en un `SAFEARRAY` puntero.|  
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Recupera un elemento de la matriz.|  
|[CComSafeArray::operator =](#operator_eq)|Operador de asignación.|  

  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeArray::m_psa](#m_psa)|Este miembro de datos contiene la dirección de la `SAFEARRAY` estructura.|  
  
## <a name="remarks"></a>Comentarios  
 `CComSafeArray` Proporciona un contenedor para el [SAFEARRAY Data Type](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearray) (clase), lo que puede crear y administrar matrices unidimensionales y multidimensionales de casi cualquiera de los tipos compatibles VARIANT fácilmente.  
  
 `CComSafeArray` simplifica el paso de matrices entre procesos y, además, proporciona seguridad adicional al comprobar los valores de índice de matriz con los limites superior e inferior.  
  
 El límite inferior de `CComSafeArray` puede empezar por cualquier valor definido por el usuario, pero las matrices a las que se accede a través de C++ usan un límite inferior de 0. Otros lenguajes como Visual Basic pueden usar otros valores límite (por ejemplo, de -10 a 10).  
  
 Use [CComSafeArray::Create](#create) para crear un objeto `CComSafeArray` y [CComSafeArray::Destroy](#destroy) para eliminarlo.  
  
 Un elemento `CComSafeArray` puede contener el siguiente subconjunto de tipos de datos VARIANT:  
  
|VARTYPE|Descripción|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ulonglong|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|puntero decimal|  
|VT_VARIANT|puntero variant|  
|VT_CY|Currency (tipo de datos)|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsafe.h  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]  
  
##  <a name="add"></a>  CComSafeArray:: Add  
 Agrega uno o más elementos, o un `SAFEARRAY` estructura, un `CComSafeArray`.  
  
```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *psaSrc*  
 Un puntero a un `SAFEARRAY` objeto.  
  
 *ulCount*  
 El número de objetos que se va a agregar a la matriz.  
  
 *pT*  
 Un puntero a uno o más objetos que se agregarán a la matriz.  
  
 *t*  
 Una referencia al objeto que se agregarán a la matriz.  
  
 *bCopy*  
 Indica si se debe crear una copia de los datos. El valor predeterminado es TRUE.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Los nuevos objetos se anexan al final de la existente `SAFEARRAY` objeto. Agregar un objeto a multidimensional `SAFEARRAY` objeto no es compatible. Cuando se agrega una matriz de objetos existente, ambas matrices deben contener elementos del mismo tipo.  
  
 El *bCopy* marca se tiene en cuenta cuando se agregan elementos de tipo BSTR o VARIANT en una matriz. El valor predeterminado es true, se garantiza que se crea una nueva copia de los datos cuando el elemento se agrega a la matriz.  
  
##  <a name="attach"></a>  CComSafeArray::Attach  
 Asocia un `SAFEARRAY` estructura a un `CComSafeArray` objeto.  
  
```
HRESULT Attach(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *psaSrc*  
 Un puntero a la `SAFEARRAY` estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Asocia un `SAFEARRAY` estructura a un `CComSafeArray` objeto, por lo que la existente `CComSafeArray` métodos disponibles.  
  
##  <a name="ccomsafearray"></a>  CComSafeArray::CComSafeArray  
 El constructor.  
  
```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *Enlazado*  
 Un estructura `SAFEARRAYBOUND`.  
  
 *ulCount*  
 Número de elementos de la matriz.  
  
 *lLBound*  
 El valor de límite inferior; es decir, el índice del primer elemento de la matriz.  
  
 *pBound*  
 Un puntero a un `SAFEARRAYBOUND` estructura.  
  
 *uDims*  
 El número de dimensiones de la matriz.  
  
 *saSrc*  
 Una referencia a un `SAFEARRAY` estructura o `CComSafeArray` objeto. En cualquier caso el constructor usa esta referencia para realizar una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.  
  
 *psaSrc*  
 Un puntero a un `SAFEARRAY` estructura. El constructor usa esta dirección para realizar una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.  
  
### <a name="remarks"></a>Comentarios  
 Crea un objeto `CComSafeArray`.  
  
##  <a name="dtor"></a>  CComSafeArray:: ~ CComSafeArray  
 Destructor.  
  
```
~CComSafeArray() throw()
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="copyfrom"></a>  CComSafeArray:: CopyFrom  
 Copia el contenido de un `SAFEARRAY` estructura en el `CComSafeArray` objeto.  
  
```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parámetros  
 *ppArray*  
 Puntero a la `SAFEARRAY` para copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia el contenido de un `SAFEARRAY` en actual `CComSafeArray` objeto. Se reemplazará el contenido existente de la matriz.  
  
##  <a name="copyto"></a>  CComSafeArray::CopyTo  
 Crea una copia del objeto `CComSafeArray` .  
  
```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parámetros  
 *ppArray*  
 Un puntero a una ubicación en la que se va a crear el nuevo `SAFEARRAY`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia el contenido de un `CComSafeArray` objeto en un `SAFEARRAY` estructura.  
  
##  <a name="create"></a>  CComSafeArray::Create  
 Crea una interfaz `CComSafeArray`.  
  
```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *pBound*  
 Un puntero a un `SAFEARRAYBOUND` objeto.  
  
 *uDims*  
 El número de dimensiones de la matriz.  
  
 *ulCount*  
 Número de elementos de la matriz.  
  
 *lLBound*  
 El valor de límite inferior; es decir, el índice del primer elemento de la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Un `CComSafeArray` objeto puede crearse a partir de una máquina `SAFEARRAYBOUND` estructura y el número de dimensiones, o especificando el número de elementos en la matriz y el límite inferior. Si la matriz es necesario acceder desde Visual C++, el límite inferior debe ser 0. Otros lenguajes pueden permitir otros valores para el límite inferior (por ejemplo, Visual Basic admite matrices con elementos con un intervalo de -10 a 10).  
  
##  <a name="destroy"></a>  CComSafeArray::Destroy  
 Destruye un objeto `CComSafeArray`.  
  
```
HRESULT Destroy();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Destruye una existente `CComSafeArray` objeto y todos los datos que contiene.  
  
##  <a name="detach"></a>  CComSafeArray:: Detach  
 Desasocia un `SAFEARRAY` desde un `CComSafeArray` objeto.  
  
```
LPSAFEARRAY Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a un `SAFEARRAY` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método separa el `SAFEARRAY` objeto desde el `CComSafeArray` objeto.  
  
##  <a name="getat"></a>  CComSafeArray:: GetAt  
 Recupera un único elemento de una matriz unidimensional.  
  
```
T& GetAt(LONG lIndex) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *lIndex*  
 El número de índice del valor de la matriz para devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al elemento de matriz requiere.  
  
##  <a name="getcount"></a>  CComSafeArray::GetCount  
 Devuelve el número de elementos de la matriz.  
  
```
ULONG GetCount(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *uDim*  
 La dimensión de matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se usa con una matriz multidimensional, este método devolverá el número de elementos de una dimensión específica solo.  
  
##  <a name="getdimensions"></a>  CComSafeArray::GetDimensions  
 Devuelve el número de dimensiones de la matriz.  
  
```
UINT GetDimensions() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de dimensiones de la matriz.  
  
##  <a name="getlowerbound"></a>  CComSafeArray::GetLowerBound  
 Devuelve el límite inferior de una determinada dimensión de la matriz.  
  
```
LONG GetLowerBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *uDim*  
 La dimensión de matriz para que se va a obtener el límite inferior. Si se omite, el valor predeterminado es 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite inferior.  
  
### <a name="remarks"></a>Comentarios  
 Si el límite inferior es 0, esto indica una matriz de tipo C cuyo primer elemento es el elemento número 0. Si se produce un error, por ejemplo, un argumento no válido de dimensión, este método llama a `AtlThrow` con un valor HRESULT que describe el error.  
  
##  <a name="getsafearrayptr"></a>  CComSafeArray::GetSafeArrayPtr  
 Devuelve la dirección del miembro de datos `m_psa` .  
  
```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la [CComSafeArray::m_psa](#m_psa) miembro de datos.  
  
##  <a name="gettype"></a>  CComSafeArray::GetType  
 Devuelve el tipo de datos almacenado en la matriz.  
  
```
VARTYPE GetType() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tipo de datos almacenados en la matriz, que podría ser cualquiera de los siguientes tipos:  
  
|VARTYPE|Descripción|  
|-------------|-----------------|  
|VT_I1|char|  
|VT_I2|short|  
|VT_I4|int|  
|VT_I4|long|  
|VT_I8|longlong|  
|VT_UI1|byte|  
|VT_UI2|ushort|  
|VT_UI4|uint|  
|VT_UI4|ulong|  
|VT_UI8|ulonglong|  
|VT_R4|float|  
|VT_R8|double|  
|VT_DECIMAL|puntero decimal|  
|VT_VARIANT|puntero variant|  
|VT_CY|Currency (tipo de datos)|  
  
##  <a name="getupperbound"></a>  CComSafeArray::GetUpperBound  
 Devuelve el límite superior de cualquier dimensión de la matriz.  
  
```
LONG GetUpperBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *uDim*  
 La dimensión de matriz para que se va a obtener el límite superior. Si se omite, el valor predeterminado es 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite superior. Este valor es inclusivo, el máximo índice válido para esta dimensión.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error, por ejemplo, un argumento no válido de dimensión, este método llama a `AtlThrow` con un valor HRESULT que describe el error.  
  
##  <a name="issizable"></a>  CComSafeArray::IsSizable  
 Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray` .  
  
```
bool IsSizable() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si el `CComSafeArray` puede cambiarse, FALSE si no es posible.  
  
##  <a name="m_psa"></a>  CComSafeArray::m_psa  
 Contiene la dirección de la `SAFEARRAY` estructura acceder.  
  
```
LPSAFEARRAY m_psa;
```  
  
##  <a name="multidimgetat"></a>  CComSafeArray::MultiDimGetAt  
 Recupera un único elemento de una matriz multidimensional.  
  
```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```  
  
### <a name="parameters"></a>Parámetros  
 *alIndex*  
 Puntero a un vector de índices para cada dimensión de la matriz. La dimensión más a la izquierda (más significativa) es `alIndex[0]`.  
  
 *t*  
 Devuelve una referencia a los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
##  <a name="multidimsetat"></a>  CComSafeArray::MultiDimSetAt  
 Establece el valor de un elemento de una matriz multidimensional.  
  
```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```  
  
### <a name="parameters"></a>Parámetros  
 *alIndex*  
 Puntero a un vector de índices para cada dimensión de la matriz. La dimensión (menos significativa) más a la derecha es `alIndex`[0].  
  
 *T*  
 Especifica el valor del nuevo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una versión de multidimensionales [SetAt](#setat).  
  
##  <a name="operator_at"></a>  CComSafeArray::operator \[\]  
 Recupera un elemento de la matriz.  
  
```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```  
  
### <a name="parameters"></a>Parámetros  
 *lIndex, nIndex*  
 El número de índice del elemento necesario en la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el elemento de matriz correspondiente.  
  
### <a name="remarks"></a>Comentarios  
 Realiza una función similar a [CComSafeArray:: GetAt](#getat); sin embargo, este operador solo funciona con matrices unidimensionales.  
  
##  <a name="operator_eq"></a>  CComSafeArray::operator =  
 Operador de asignación.  
  
```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 *saSrc*  
 Referencia a un objeto `CComSafeArray`.  
  
 *psaSrc*  
 Un puntero a un `SAFEARRAY` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tipo de datos almacenado en la matriz.  
  
##  <a name="operator_lpsafearray"></a>  CComSafeArray::operator LPSAFEARRAY  
 Convierte un valor en un `SAFEARRAY` puntero.  
  
```
operator LPSAFEARRAY() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Convierte un valor en un `SAFEARRAY` puntero.  
  
##  <a name="resize"></a>  CComSafeArray::Resize  
 Cambia el tamaño de un objeto `CComSafeArray` .  
  
```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 *pBound*  
 Un puntero a un `SAFEARRAYBOUND` estructura que contiene información sobre el número de elementos y el límite inferior de la matriz.  
  
 *ulCount*  
 El número solicitado de objetos de la matriz cuyo tamaño ha cambiado.  
  
 *lLBound*  
 El límite inferior.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método solo cambia el tamaño de la dimensión más a la derecha. No cambiará de tamaño las matrices que devuelven `IsResizable` como FALSE.  
  
##  <a name="setat"></a>  SetAt  
 Establece el valor de un elemento de una matriz unidimensional.  
  
```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 *lIndex*  
 El número de índice del elemento de matriz para establecer.  
  
 *t*  
 El nuevo valor del elemento especificado.  
  
 *bCopy*  
 Indica si se debe crear una copia de los datos. El valor predeterminado es TRUE.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El *bCopy* marca se tiene en cuenta cuando se agregan elementos de tipo BSTR o VARIANT en una matriz. El valor predeterminado es true, se garantiza que se crea una nueva copia de los datos cuando el elemento se agrega a la matriz.  
  
## <a name="see-also"></a>Vea también  
 [Tipo de datos SAFEARRAY](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagsafearray)   
 [CComSafeArray:: Create](#create)   
 [CComSafeArray:: Destroy](#destroy)   
 [Información general de clases](../../atl/atl-class-overview.md)
