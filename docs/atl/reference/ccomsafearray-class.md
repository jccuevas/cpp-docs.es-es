---
title: CComSafeArray (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7bed846015090ef9c4da841adff4968c91d8719d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomsafearray-class"></a>CComSafeArray (clase)
Esta clase es un contenedor de la estructura **SAFEARRAY** .  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
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
|[CComSafeArray::Add](#add)|Agrega uno o más elementos, o una estructura **SAFEARRAY** , a `CComSafeArray`.|  
|[CComSafeArray::Attach](#attach)|Asocia una estructura **SAFEARRAY** a un objeto `CComSafeArray` .|  
|[CComSafeArray::CopyFrom](#copyfrom)|Copia el contenido de una estructura **SAFEARRAY** en el objeto `CComSafeArray` .|  
|[CComSafeArray::CopyTo](#copyto)|Crea una copia del objeto `CComSafeArray` .|  
|[CComSafeArray::Create](#create)|Crea un objeto `CComSafeArray`.|  
|[CComSafeArray::Destroy](#destroy)|Destruye un objeto `CComSafeArray`.|  
|[CComSafeArray::Detach](#detach)|Desasocia un elemento **SAFEARRAY** de un objeto `CComSafeArray` .|  
|[CComSafeArray::GetAt](#getat)|Recupera un único elemento de una matriz unidimensional.|  
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
|[CComSafeArray::SetAt](#setat)|Establece el valor de un elemento de una matriz unidimensional.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Transmite un valor a un puntero **SAFEARRAY** .|  
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Recupera un elemento de la matriz.|  
|[CComSafeArray::operator =](#operator_eq)|Operador de asignación.|  

  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSafeArray::m_psa](#m_psa)|Este miembro de datos contiene la dirección de la estructura **SAFEARRAY** .|  
  
## <a name="remarks"></a>Comentarios  
 `CComSafeArray` proporciona un contenedor para la clase [SAFEARRAY Data Type](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e) , lo que facilita la creación y administración de matrices unidimensionales y multidimensionales de casi cualquiera de los tipos compatibles VARIANT.  
  
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
  
##  <a name="add"></a>CComSafeArray::Add  
 Agrega uno o más elementos, o una estructura **SAFEARRAY** , a `CComSafeArray`.  
  
```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `psaSrc`  
 Un puntero a un **SAFEARRAY** objeto.  
  
 `ulCount`  
 El número de objetos que se va a agregar a la matriz.  
  
 *pT*  
 Un puntero a uno o más objetos que va a agregar a la matriz.  
  
 *t*  
 Una referencia al objeto que se va a agregar a la matriz.  
  
 `bCopy`  
 Indica si se debe crear una copia de los datos. El valor predeterminado es **TRUE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Los objetos nuevos se anexan al final de la existente **SAFEARRAY** objeto. Agregar un objeto a un multidimensionales **SAFEARRAY** no admite el objeto. Cuando se agrega una matriz de objetos existente, ambas matrices deben contener elementos del mismo tipo.  
  
 El `bCopy` marca se tiene en cuenta cuando los elementos de tipo `BSTR` o **VARIANT** se agregan a una matriz. El valor predeterminado de **TRUE** garantiza que se crea una nueva copia de los datos cuando el elemento se agrega a la matriz.  
  
##  <a name="attach"></a>CComSafeArray::Attach  
 Asocia una estructura **SAFEARRAY** a un objeto `CComSafeArray` .  
  
```
HRESULT Attach(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `psaSrc`  
 Un puntero a la **SAFEARRAY** estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Asocia un **SAFEARRAY** estructura a un `CComSafeArray` objeto, por lo que el existente `CComSafeArray` métodos disponibles.  
  
##  <a name="ccomsafearray"></a>CComSafeArray::CComSafeArray  
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
 `bound`  
 A **SAFEARRAYBOUND** estructura.  
  
 `ulCount`  
 Número de elementos de la matriz.  
  
 `lLBound`  
 El valor de límite inferior; es decir, el índice del primer elemento de la matriz.  
  
 `pBound`  
 Un puntero a un **SAFEARRAYBOUND** estructura.  
  
 `uDims`  
 El número de dimensiones de la matriz.  
  
 `saSrc`  
 Una referencia a un **SAFEARRAY** estructura o `CComSafeArray` objeto. En cualquier caso el constructor usa esta referencia para realizar una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.  
  
 `psaSrc`  
 Un puntero a un **SAFEARRAY** estructura. El constructor utiliza esta dirección para realizar una copia de la matriz, por lo que no se hace referencia a la matriz después de la construcción.  
  
### <a name="remarks"></a>Comentarios  
 Crea un objeto `CComSafeArray`.  
  
##  <a name="dtor"></a>CComSafeArray:: ~ CComSafeArray  
 Destructor.  
  
```
~CComSafeArray() throw()
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="copyfrom"></a>CComSafeArray::CopyFrom  
 Copia el contenido de una estructura **SAFEARRAY** en el objeto `CComSafeArray` .  
  
```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppArray`  
 Puntero a la **SAFEARRAY** para copiar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia el contenido de un **SAFEARRAY** en actual `CComSafeArray` objeto. Se reemplazará el contenido existente de la matriz.  
  
##  <a name="copyto"></a>CComSafeArray::CopyTo  
 Crea una copia del objeto `CComSafeArray` .  
  
```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```  
  
### <a name="parameters"></a>Parámetros  
 `ppArray`  
 Un puntero a una ubicación en la que se va a crear el nuevo **SAFEARRAY**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método copia el contenido de un `CComSafeArray` objeto en un **SAFEARRAY** estructura.  
  
##  <a name="create"></a>  CComSafeArray::Create  
 Crea una interfaz `CComSafeArray`.  
  
```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBound`  
 Un puntero a un **SAFEARRAYBOUND** objeto.  
  
 `uDims`  
 El número de dimensiones de la matriz.  
  
 `ulCount`  
 Número de elementos de la matriz.  
  
 `lLBound`  
 El valor de límite inferior; es decir, el índice del primer elemento de la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 A `CComSafeArray` objeto puede crearse a partir de una **SAFEARRAYBOUND** estructura y el número de dimensiones, o especificando el número de elementos de la matriz y el límite inferior. Si la matriz es estar accesibles desde Visual C++, el límite inferior debe ser 0. Otros lenguajes pueden permitir otros valores para el límite inferior (por ejemplo, Visual Basic permite matrices con elementos con un intervalo como -10 a 10).  
  
##  <a name="destroy"></a>  CComSafeArray::Destroy  
 Destruye un objeto `CComSafeArray`.  
  
```
HRESULT Destroy();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Destruye una existente `CComSafeArray` objeto y todos los datos que contiene.  
  
##  <a name="detach"></a>CComSafeArray::Detach  
 Desasocia un elemento **SAFEARRAY** de un objeto `CComSafeArray` .  
  
```
LPSAFEARRAY Detach();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a un **SAFEARRAY** objeto.  
  
### <a name="remarks"></a>Comentarios  
 Este método separa el **SAFEARRAY** objeto desde el `CComSafeArray` objeto.  
  
##  <a name="getat"></a>CComSafeArray::GetAt  
 Recupera un único elemento de una matriz unidimensional.  
  
```
T& GetAt(LONG lIndex) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `lIndex`  
 El número de índice del valor de la matriz para devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al elemento de matriz necesarios.  
  
##  <a name="getcount"></a>CComSafeArray::GetCount  
 Devuelve el número de elementos de la matriz.  
  
```
ULONG GetCount(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `uDim`  
 La dimensión de la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Cuando se utiliza con una matriz multidimensional, este método devolverá el número de elementos en una dimensión concreta solo.  
  
##  <a name="getdimensions"></a>CComSafeArray::GetDimensions  
 Devuelve el número de dimensiones de la matriz.  
  
```
UINT GetDimensions() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de dimensiones de la matriz.  
  
##  <a name="getlowerbound"></a>CComSafeArray::GetLowerBound  
 Devuelve el límite inferior de una determinada dimensión de la matriz.  
  
```
LONG GetLowerBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `uDim`  
 La dimensión de matriz para el que se va a obtener el límite inferior. Si se omite, el valor predeterminado es 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite inferior.  
  
### <a name="remarks"></a>Comentarios  
 Si el límite inferior es 0, esto indica una matriz de tipo C cuyo primer elemento es el número 0 del elemento. Si se produce un error, por ejemplo, un argumento no válido de dimensión, este método llama a `AtlThrow` con un valor HRESULT que describe el error.  
  
##  <a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr  
 Devuelve la dirección del miembro de datos `m_psa` .  
  
```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la [CComSafeArray::m_psa](#m_psa) miembro de datos.  
  
##  <a name="gettype"></a>CComSafeArray::GetType  
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
  
##  <a name="getupperbound"></a>CComSafeArray::GetUpperBound  
 Devuelve el límite superior de cualquier dimensión de la matriz.  
  
```
LONG GetUpperBound(UINT uDim = 0) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `uDim`  
 La dimensión de matriz para el que se va a obtener el límite superior. Si se omite, el valor predeterminado es 0.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el límite superior. Este valor es inclusivo, el índice válido máximo para esta dimensión.  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error, por ejemplo, un argumento no válido de dimensión, este método llama a `AtlThrow` con un valor HRESULT que describe el error.  
  
##  <a name="issizable"></a>CComSafeArray::IsSizable  
 Comprueba si se puede cambiar el tamaño de un objeto `CComSafeArray` .  
  
```
bool IsSizable() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la `CComSafeArray` puede cambiarse, **false** si no es posible.  
  
##  <a name="m_psa"></a>CComSafeArray::m_psa  
 Contiene la dirección de la **SAFEARRAY** estructura tiene acceso.  
  
```
LPSAFEARRAY m_psa;
```  
  
##  <a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt  
 Recupera un único elemento de una matriz multidimensional.  
  
```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```  
  
### <a name="parameters"></a>Parámetros  
 `alIndex`  
 Puntero a un vector de índices para cada dimensión de la matriz. La dimensión más a la izquierda (más significativa) es `alIndex[0]`.  
  
 *t*  
 Devuelve una referencia a los datos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt  
 Establece el valor de un elemento de una matriz multidimensional.  
  
```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```  
  
### <a name="parameters"></a>Parámetros  
 `alIndex`  
 Puntero a un vector de índices para cada dimensión de la matriz. La dimensión más a la derecha (menos significativa) es `alIndex`[0].  
  
 *T*  
 Especifica el valor del nuevo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se trata de una versión multidimensional de [CComSafeArray::SetAt](#setat).  
  
##  <a name="operator_at"></a>CComSafeArray::operator\[\]  
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
 Realiza una función similar a [CComSafeArray::GetAt](#getat); sin embargo, este operador solo funciona con matrices unidimensionales.  
  
##  <a name="operator_eq"></a>CComSafeArray::operator =  
 Operador de asignación.  
  
```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `saSrc`  
 Referencia a un objeto `CComSafeArray`.  
  
 `psaSrc`  
 Un puntero a un **SAFEARRAY** objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tipo de datos almacenado en la matriz.  
  
##  <a name="operator_lpsafearray"></a>CComSafeArray::operator LPSAFEARRAY  
 Transmite un valor a un puntero **SAFEARRAY** .  
  
```
operator LPSAFEARRAY() const;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Transmite un valor a un puntero **SAFEARRAY** .  
  
##  <a name="resize"></a>CComSafeArray::Resize  
 Cambia el tamaño de un objeto `CComSafeArray` .  
  
```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `pBound`  
 Un puntero a un **SAFEARRAYBOUND** estructura que contiene información sobre el número de elementos y el límite inferior de una matriz.  
  
 `ulCount`  
 El número solicitado de objetos de la matriz cuyo tamaño ha cambiado.  
  
 `lLBound`  
 El límite inferior.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método solo cambia el tamaño de la dimensión más a la derecha. No cambiará de tamaño matrices que devuelven **IsResizable** como **false**.  
  
##  <a name="setat"></a>CComSafeArray::SetAt  
 Establece el valor de un elemento de una matriz unidimensional.  
  
```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```  
  
### <a name="parameters"></a>Parámetros  
 `lIndex`  
 El número de índice del elemento de matriz para establecer.  
  
 *t*  
 El nuevo valor del elemento especificado.  
  
 `bCopy`  
 Indica si se debe crear una copia de los datos. El valor predeterminado es **TRUE**.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 El `bCopy` marca se tiene en cuenta cuando los elementos de tipo `BSTR` o **VARIANT** se agregan a una matriz. El valor predeterminado de **TRUE** garantiza que se crea una nueva copia de los datos cuando el elemento se agrega a la matriz.  
  
## <a name="see-also"></a>Vea también  
 [SAFEARRAY Data Type](http://msdn.microsoft.com/en-us/9ec8025b-4763-4526-ab45-390c5d8b3b1e)   
 [CComSafeArray:: Create](#create)   
 [CComSafeArray:: Destroy](#destroy)   
 [Información general de clases](../../atl/atl-class-overview.md)
