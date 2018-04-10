---
title: Clase de CAtlMap | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- CAtlMap
- ATLCOLL/ATL::CAtlMap
- ATLCOLL/ATL::CAtlMap::KINARGTYPE
- ATLCOLL/ATL::CAtlMap::KOUTARGTYPE
- ATLCOLL/ATL::CAtlMap::VINARGTYPE
- ATLCOLL/ATL::CAtlMap::VOUTARGTYPE
- ATLCOLL/ATL::CPair::m_key
- ATLCOLL/ATL::CPair::m_value
- ATLCOLL/ATL::CAtlMap::CAtlMap
- ATLCOLL/ATL::CAtlMap::AssertValid
- ATLCOLL/ATL::CAtlMap::DisableAutoRehash
- ATLCOLL/ATL::CAtlMap::EnableAutoRehash
- ATLCOLL/ATL::CAtlMap::GetAt
- ATLCOLL/ATL::CAtlMap::GetCount
- ATLCOLL/ATL::CAtlMap::GetHashTableSize
- ATLCOLL/ATL::CAtlMap::GetKeyAt
- ATLCOLL/ATL::CAtlMap::GetNext
- ATLCOLL/ATL::CAtlMap::GetNextAssoc
- ATLCOLL/ATL::CAtlMap::GetNextKey
- ATLCOLL/ATL::CAtlMap::GetNextValue
- ATLCOLL/ATL::CAtlMap::GetStartPosition
- ATLCOLL/ATL::CAtlMap::GetValueAt
- ATLCOLL/ATL::CAtlMap::InitHashTable
- ATLCOLL/ATL::CAtlMap::IsEmpty
- ATLCOLL/ATL::CAtlMap::Lookup
- ATLCOLL/ATL::CAtlMap::Rehash
- ATLCOLL/ATL::CAtlMap::RemoveAll
- ATLCOLL/ATL::CAtlMap::RemoveAtPos
- ATLCOLL/ATL::CAtlMap::RemoveKey
- ATLCOLL/ATL::CAtlMap::SetAt
- ATLCOLL/ATL::CAtlMap::SetOptimalLoad
- ATLCOLL/ATL::CAtlMap::SetValueAt
dev_langs:
- C++
helpviewer_keywords:
- CAtlMap class
ms.assetid: 5e2fe028-8e6d-4686-93df-1433d2080ec3
caps.latest.revision: 21
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9166e8f7804a3138d3e891fbe15b54cb0e270811
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catlmap-class"></a>Clase de CAtlMap
Esta clase proporciona métodos para crear y administrar un objeto de mapa.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename K,
          typename V, 
          class KTraits = CElementTraits<K>, 
          class VTraits = CElementTraits<V>>
class CAtlMap
```  
  
#### <a name="parameters"></a>Parámetros  
 `K`  
 El tipo de elemento de la clave.  
  
 V  
 El tipo de elemento de valor.  
  
 `KTraits`  
 El código utilizado para copiar o mover elementos clave. Vea [CElementTraits clase](../../atl/reference/celementtraits-class.md) para obtener más detalles.  
  
 `VTraits`  
 El código utilizado para copiar o mover elementos de valor.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::KINARGTYPE](#kinargtype)|Tipo que se utiliza cuando una clave se pasa como un argumento de entrada|  
|[CAtlMap::KOUTARGTYPE](#koutargtype)|Tipo que se usa cuando una clave se devuelve como un argumento de salida.|  
|[CAtlMap::VINARGTYPE](#vinargtype)|Tipo que se utiliza cuando un valor se pasa como un argumento de entrada.|  
|[CAtlMap::VOUTARGTYPE](#voutargtype)|Tipo que se utiliza cuando un valor se pasa como un argumento de salida.|  
  
### <a name="public-classes"></a>Clases públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[Clase CAtlMap::CPair](#cpair_class)|Una clase que contiene los elementos clave y valor.|  

  
### <a name="cpair-data-members"></a>Miembros de datos de CPair  
  
|nombre|Descripción|  
|----------|-----------------|  
|[CPair::m_key](#m_key)|El miembro de datos que se almacena el elemento key.|  
|[CPair::m_value](#m_value)|El miembro de datos que se almacena el elemento de valor.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::CAtlMap](#catlmap)|El constructor.|  
|[CAtlMap:: ~ CAtlMap](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::AssertValid](#assertvalid)|Llamar a este método para hacer que una aserción si el `CAtlMap` no es válido.|  
|[CAtlMap::DisableAutoRehash](#disableautorehash)|Llamar a este método para deshabilitar automática vuelve de la `CAtlMap` objeto.|  
|[CAtlMap::EnableAutoRehash](#enableautorehash)|Llamar a este método para habilitar vuelve automática de la `CAtlMap` objeto.|  
|[CAtlMap::GetAt](#getat)|Llame a este método para devolver el elemento en una posición especificada en el mapa.|  
|[CAtlMap::GetCount](#getcount)|Llamar a este método para recuperar el número de elementos en el mapa.|  
|[CAtlMap::GetHashTableSize](#gethashtablesize)|Llamar a este método para determinar el número de ubicaciones en la tabla de hash del mapa.|  
|[CAtlMap::GetKeyAt](#getkeyat)|Llamar a este método para recuperar la clave almacenada en la posición especificada en el `CAtlMap` objeto.|  
|[CAtlMap::GetNext](#getnext)|Llamar a este método para obtener un puntero al elemento siguiente par almacenado en la `CAtlMap` objeto.|  
|[CAtlMap::GetNextAssoc](#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|  
|[CAtlMap::GetNextKey](#getnextkey)|Llamar a este método para recuperar la siguiente clave de la `CAtlMap` objeto.|  
|[CAtlMap::GetNextValue](#getnextvalue)|Llamar a este método para obtener el siguiente valor de la `CAtlMap` objeto.|  
|[CAtlMap::GetStartPosition](#getstartposition)|Llame a este método para iniciar una iteración de mapa.|  
|[CAtlMap::GetValueAt](#getvalueat)|Llamar a este método para recuperar el valor almacenado en una posición determinada en la `CAtlMap` objeto.|  
|[CAtlMap::InitHashTable](#inithashtable)|Llamar a este método para inicializar la tabla hash.|  
|[CAtlMap::IsEmpty](#isempty)|Llamar a este método para comprobar si un objeto de asignación vacía.|  
|[CAtlMap::Lookup](#lookup)|Llamar a este método para buscar las claves o valores en la `CAtlMap` objeto.|  
|[CAtlMap::Rehash](#rehash)|Llame a este método para rehash () la `CAtlMap` objeto.|  
|[CAtlMap::RemoveAll](#removeall)|Llamar a este método para quitar todos los elementos de la `CAtlMap` objeto.|  
|[CAtlMap::RemoveAtPos](#removeatpos)|Llamar a este método para quitar el elemento en la posición especificada en el `CAtlMap` objeto.|  
|[CAtlMap::RemoveKey](#removekey)|Llamar a este método para quitar un elemento de la `CAtlMap` objeto, la clave dada.|  
|[CAtlMap::SetAt](#setat)|Llamar a este método para insertar un par de elementos en el mapa.|  
|[CAtlMap::SetOptimalLoad](#setoptimalload)|Llamar a este método para establecer la carga óptima de la `CAtlMap` objeto.|  
|[CAtlMap::SetValueAt](#setvalueat)|Llamar a este método para cambiar el valor almacenado en una posición determinada en la `CAtlMap` objeto.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlMap::operator\[\]](catlmap-class.md#operator_at)|Reemplaza o agrega un nuevo elemento a la `CAtlMap`.|  

  
## <a name="remarks"></a>Comentarios  
 `CAtlMap`proporciona compatibilidad para una matriz de asignación de un tipo dado, administración de una matriz no ordenada de elementos clave y sus valores asociados. Elementos (que consta de una clave y un valor) se almacenan usando un algoritmo hash, lo que permite una gran cantidad de datos se almacenan y recuperan eficazmente.  
  
 El `KTraits` y `VTraits` parámetros son las clases de rasgos que contienen cualquier código complementario necesario para copiar o mover elementos.  
  
 Una alternativa a `CAtlMap` ofrece la [CRBMap](../../atl/reference/crbmap-class.md) clase. `CRBMap`también almacena pares clave/valor, pero muestra distintas características de rendimiento. El tiempo necesario para insertar un elemento, buscar una clave o eliminar una clave de un `CRBMap` objeto es de orden *log(n)*, donde  *n*  es el número de elementos. Para `CAtlMap`, todas estas operaciones suelen tardan un tiempo constante, aunque pueden ser peores escenarios de pedido  *n* . Por lo tanto, en un caso típico, `CAtlMap` es más rápido.  
  
 Otra diferencia entre `CRBMap` y `CAtlMap` queda patente cuando recorrer en iteración los elementos almacenados. En un `CRBMap`, los elementos se visitan de forma ordenada. En un `CAtlMap`, no se ordenan los elementos y no se puede inferir ningún orden.  
  
 Cuando un número pequeño de elementos debe estar almacenados, considere el uso de la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase en su lugar.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="assertvalid"></a>CAtlMap::AssertValid  
 Llamar a este método para hacer que una aserción si el `CAtlMap` objeto no es válido.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, este método producirá una aserción si el `CAtlMap` objeto no es válido.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="catlmap"></a>CAtlMap::CAtlMap  
 El constructor.  
  
```
CAtlMap(
    UINT nBins = 17,
    float fOptimalLoad = 0.75f,
    float fLoThreshold = 0.25f,
    float fHiThreshold = 2.25f,
    UINT nBlockSize = 10) throw ();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBins`  
 El número de ubicaciones proporciona punteros a los elementos almacenados. Vea la sección Comentarios más adelante en este tema para obtener una explicación de las ubicaciones.  
  
 `fOptimalLoad`  
 La proporción de carga óptima.  
  
 `fLoThreshold`  
 Umbral inferior para la proporción de carga.  
  
 `fHiThreshold`  
 Umbral superior para la proporción de carga.  
  
 `nBlockSize`  
 El tamaño del bloque.  
  
### <a name="remarks"></a>Comentarios  
 `CAtlMap`hace referencia a todos sus elementos almacenados creando primero un índice usando un algoritmo hash en la clave. Este índice hace referencia a un "bin", que contiene un puntero a los elementos almacenados. Si la Papelera ya está en uso, se crea una lista vinculada para obtener acceso a los elementos siguientes. Recorrer una lista es más lenta que tengan acceso directo al elemento correcto y, por tanto, la estructura del mapa debe equilibrar los requisitos de almacenamiento con respecto al rendimiento. Los parámetros predeterminados se han elegido para dar buenos resultados en la mayoría de los casos.  
  
 La proporción de carga es la proporción del número de cubos para el número de elementos almacenados en el objeto de mapa. Cuando se vuelve a calcular la estructura del mapa, el *fOptimalLoad* el valor del parámetro que se usará para calcular el número de ubicaciones necesarias. Este valor se puede cambiar mediante la [CAtlMap::SetOptimalLoad](#setoptimalload) método.  
  
 El `fLoThreshold` parámetro es el valor más bajo que la proporción de carga puede alcanzar antes `CAtlMap` se volverá a calcular el tamaño óptimo de la asignación.  
  
 El `fHiThreshold` parámetro es el valor más alto que puede alcanzar la proporción de carga antes de la `CAtlMap` objeto se volverá a calcular el tamaño óptimo de la asignación.  
  
 Este proceso de recálculo (conocido como vuelve) está habilitado de forma predeterminada. Si desea deshabilitar este proceso, quizás al escribir una gran cantidad de datos al mismo tiempo, llamada la [CAtlMap::DisableAutoRehash](#disableautorehash) método. Reactivar con el [CAtlMap::EnableAutoRehash](#enableautorehash) método.  
  
 El `nBlockSize` parámetro es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Bloques más grandes, reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.  
  
 Antes de que se pueden almacenar los datos, es necesario inicializar la tabla hash con una llamada a [CAtlMap::InitHashTable](#inithashtable).  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#72](../../atl/codesnippet/cpp/catlmap-class_1.cpp)]  
  
##  <a name="dtor"></a>CAtlMap:: ~ CAtlMap  
 Destructor.  
  
```
~CAtlMap() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos asignados.  
  
##  <a name="cpair_class"></a>Clase CAtlMap::CPair  
 Una clase que contiene los elementos clave y valor.  
  
```
class CPair : public __POSITION
```  
  
### <a name="remarks"></a>Comentarios  
 Esta clase se utiliza con los métodos [CAtlMap::GetNext](#getnext) y [CAtlMap::Lookup](#lookup) para tener acceso a los elementos clave y el valor almacenados en la estructura de asignación.  
  
##  <a name="disableautorehash"></a>CAtlMap::DisableAutoRehash  
 Llamar a este método para deshabilitar automática vuelve de la `CAtlMap` objeto.  
  
```
void DisableAutoRehash() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando vuelve automática está habilitada (lo que sucede de forma predeterminada), el número de ubicaciones en la tabla hash, automáticamente se volverán a recalcular si el valor de carga (la proporción del número de cubos para el número de elementos almacenados en la matriz) supera los valores máximo o mínimos Si se especifica en el momento en que se creó la asignación.  
  
 `DisableAutoRehash`es muy útil cuando un gran número de elementos se agregará a la asignación a la vez. En lugar de desactivar el proceso de rehashing cada vez que se superan los límites, es más eficaz llamar a `DisableAutoRehash`, agregue los elementos y, por último, llame a [CAtlMap::EnableAutoRehash](#enableautorehash).  
  
##  <a name="enableautorehash"></a>CAtlMap::EnableAutoRehash  
 Llamar a este método para habilitar vuelve automática de la `CAtlMap` objeto.  
  
```
void EnableAutoRehash() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Cuando vuelve automática está habilitada (lo que sucede de forma predeterminada), el número de ubicaciones en la tabla hash, automáticamente se volverán a recalcular si el valor de carga (la proporción del número de cubos para el número de elementos almacenados en la matriz) supera los valores máximo o mínimos Si se especifica en el momento en que se crea la asignación.  
  
 **EnableAutoRefresh** más a menudo se usa después de llamar a [CAtlMap::DisableAutoRehash](#disableautorehash).  
  
##  <a name="getat"></a>CAtlMap::GetAt  
 Llame a este método para devolver el elemento en una posición especificada en el mapa.  
  
```
void GetAt(
    POSITION pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;

CPair* GetAt(POSITION& pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
 `key`  
 Parámetro de plantilla que especifica el tipo de clave del mapa.  
  
 *valor*  
 Especifica el tipo del valor de la asignación de un parámetro de plantilla.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la par actual de elementos de clave/valor almacenados en el mapa.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se producirá un error de aserción si `pos` es igual a NULL.  
  
##  <a name="getcount"></a>CAtlMap::GetCount  
 Llamar a este método para recuperar el número de elementos en el mapa.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos del objeto map. Un único elemento es un par de clave/valor.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="gethashtablesize"></a>CAtlMap::GetHashTableSize  
 Llamar a este método para determinar el número de ubicaciones en la tabla de hash del mapa.  
  
```
UINT GetHashTableSize() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de ubicaciones en la tabla hash. Vea [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.  
  
##  <a name="getkeyat"></a>CAtlMap::GetKeyAt  
 Llamar a este método para recuperar la clave almacenada en la posición especificada en el `CAtlMap` objeto.  
  
```
const K& GetKeyAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la clave almacenada en la posición especificada en el `CAtlMap` objeto.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getnext"></a>CAtlMap::GetNext  
 Llamar a este método para obtener un puntero al elemento siguiente par almacenado en la `CAtlMap` objeto.  
  
```
CPair* GetNext(POSITION& pos) throw();
const CPair* GetNext(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la siguiente par de elementos de clave/valor almacenados en el mapa. La `pos` posición contador se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, `pos` se establece en NULL.  
  
##  <a name="getnextassoc"></a>CAtlMap::GetNextAssoc  
 Obtiene el elemento siguiente para efectuar una iteración.  
  
```
void GetNextAssoc(
    POSITION& pos,
    KOUTARGTYPE key,
    VOUTARGTYPE value) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
 `key`  
 Parámetro de plantilla que especifica el tipo de clave del mapa.  
  
 *valor*  
 Especifica el tipo del valor de la asignación de un parámetro de plantilla.  
  
### <a name="remarks"></a>Comentarios  
 La `pos` posición contador se actualiza después de cada llamada. Si el elemento recuperado es el último en el mapa, `pos` se establece en NULL.  
  
##  <a name="getnextkey"></a>CAtlMap::GetNextKey  
 Llamar a este método para recuperar la siguiente clave de la `CAtlMap` objeto.  
  
```
const K& GetNextKey(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia a la clave siguiente del mapa.  
  
### <a name="remarks"></a>Comentarios  
 Actualiza el contador de posición actual, `pos`. Si no hay más entradas en el mapa, el contador de posición se establece en NULL.  
  
##  <a name="getnextvalue"></a>CAtlMap::GetNextValue  
 Llamar a este método para obtener el siguiente valor de la `CAtlMap` objeto.  
  
```
V& GetNextValue(POSITION& pos) throw();
const V& GetNextValue(POSITION& pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia en el siguiente valor en el mapa.  
  
### <a name="remarks"></a>Comentarios  
 Actualiza el contador de posición actual, `pos`. Si no hay más entradas en el mapa, el contador de posición se establece en NULL.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getstartposition"></a>CAtlMap::GetStartPosition  
 Llame a este método para iniciar una iteración de mapa.  
  
```
POSITION GetStartPosition() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve que la posición de inicio, o NULL se devuelve si el mapa está vacío.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para iniciar una iteración de mapa devolviendo un **posición** valor que puede pasarse a la `GetNextAssoc` método.  
  
> [!NOTE]
>  La secuencia de la iteración no es de predicción  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="getvalueat"></a>CAtlMap::GetValueAt  
 Llamar a este método para recuperar el valor almacenado en una posición determinada en la `CAtlMap` objeto.  
  
```
V& GetValueAt(POSITION pos) throw();
const V& GetValueAt(POSITION pos) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia para el valor almacenado en la posición especificada en el `CAtlMap` objeto.  
  
##  <a name="inithashtable"></a>CAtlMap::InitHashTable  
 Llamar a este método para inicializar la tabla hash.  
  
```
bool InitHashTable(
    UINT nBins,
    bool bAllocNow = true);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBins`  
 El número de ubicaciones utilizada por la tabla hash. Vea [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.  
  
 `bAllocNow`  
 Una indicación de marca cuando se debe asignar memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** en la inicialización correcta, **false** en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `InitHashTable`se debe llamar antes de que todos los elementos se almacenan en la tabla hash.  Si no se llama explícitamente a este método, se le llamará automáticamente la primera vez que se agrega un elemento utilizando el recuento de la ubicación especificado por el **CAtlMap** constructor.  En caso contrario, la asignación se inicializará mediante el nuevo número de bin especificado por el `nBins` parámetro.  
  
 Si el `bAllocNow` del parámetro es false, no se le asignará la memoria necesaria para la tabla hash hasta que el primero es necesario. Esto puede ser útil si está seguro de que se usará la asignación.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="isempty"></a>CAtlMap::IsEmpty  
 Llamar a este método para comprobar si un objeto de asignación vacía.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el mapa está vacío, **false** en caso contrario.  
  
##  <a name="kinargtype"></a>CAtlMap::KINARGTYPE  
 Tipo que se usa cuando una clave se pasa como un argumento de entrada.  
  
```
typedef KTraits::INARGTYPE KINARGTYPE;
```  
  
##  <a name="koutargtype"></a>CAtlMap::KOUTARGTYPE  
 Tipo que se usa cuando una clave se devuelve como un argumento de salida.  
  
```
typedef KTraits::OUTARGTYPE KOUTARGTYPE;
```  
  
##  <a name="lookup"></a>CAtlMap::Lookup  
 Llamar a este método para buscar las claves o valores en la `CAtlMap` objeto.  
  
```
bool Lookup(KINARGTYPE key, VOUTARGTYPE value) const;
const CPair* Lookup(KINARGTYPE key) const throw();
CPair* Lookup(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 Especifica la clave que identifica el elemento que se va a buscar.  
  
 *valor*  
 Variable que recibe el valor buscado.  
  
### <a name="return-value"></a>Valor devuelto  
 El primer formulario del método devuelve true si se encuentra la clave, en caso contrario, false. Los formularios de la segundo y terceros devuelven un puntero a un [CPair](#cpair_class) que puede utilizarse como una posición para las llamadas a [CAtlMap::GetNext](#getnext) y así sucesivamente.  
  
### <a name="remarks"></a>Comentarios  
 `Lookup`aplica un algoritmo hash para encontrar rápidamente el elemento de mapa que contiene una clave que coincida exactamente con el parámetro de clave especificado.  
  
##  <a name="operator_at"></a>CAtlMap::operator\[\]  
 Reemplaza o agrega un nuevo elemento a la `CAtlMap`.  
  
```
V& operator[](kinargtype key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave del elemento para agregar o reemplazar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia para el valor asociado a la clave dada.  
  
### <a name="example"></a>Ejemplo  
 Si la clave ya existe, se reemplaza el elemento. Si la clave no existe, se agrega un nuevo elemento. Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="rehash"></a>CAtlMap::Rehash  
 Llame a este método para rehash () la `CAtlMap` objeto.  
  
```
void Rehash(UINT nBins = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `nBins`  
 El nuevo número de cubos para usar en la tabla hash. Vea [CAtlMap::CAtlMap](#catlmap) para obtener una explicación.  
  
### <a name="remarks"></a>Comentarios  
 Si `nBins` es 0, `CAtlMap` calcula un número razonable en función del número de elementos de la asignación y la configuración óptima de carga. Normalmente el proceso rehashing es automático, pero si [CAtlMap::DisableAutoRehash](#disableautorehash) ha sido llama, este método llevará a cabo el cambio de tamaño es necesario.  
  
##  <a name="removeall"></a>CAtlMap::RemoveAll  
 Llamar a este método para quitar todos los elementos de la `CAtlMap` objeto.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Borra la `CAtlMap` objeto, liberar la memoria utilizada para almacenar los elementos.  
  
##  <a name="removeatpos"></a>CAtlMap::RemoveAtPos  
 Llamar a este método para quitar el elemento en la posición especificada en el `CAtlMap` objeto.  
  
```
void RemoveAtPos(POSITION pos) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
### <a name="remarks"></a>Comentarios  
 Quita el par clave/valor almacenado en la posición especificada. Se libera la memoria utilizada para almacenar el elemento. Hace referencia la posición `pos` deja de ser válido y, mientras que la posición de los demás elementos en el mapa sigue siendo válida, lo hacen no necesariamente siguen el mismo orden.  
  
##  <a name="removekey"></a>CAtlMap::RemoveKey  
 Llamar a este método para quitar un elemento de la `CAtlMap` objeto, la clave dada.  
  
```
bool RemoveKey(KINARGTYPE key) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 La clave correspondiente para el par de elementos que desea quitar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si la clave se encuentra y quita, **false** en caso de error.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlMap::CAtlMap](#catlmap).  
  
##  <a name="setat"></a>CAtlMap::SetAt  
 Llamar a este método para insertar un par de elementos en el mapa.  
  
```
POSITION SetAt(
    KINARGTYPE key,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parámetros  
 `key`  
 El valor de clave para agregar a la `CAtlMap` objeto.  
  
 *valor*  
 El valor para agregar a la `CAtlMap` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la posición del par clave/valor elemento en el `CAtlMap` objeto.  
  
### <a name="remarks"></a>Comentarios  
 `SetAt`reemplaza un elemento existente si se encuentra una clave coincidente. Si no se encuentra la clave, se crea un nuevo par clave/valor.  
  
##  <a name="setoptimalload"></a>CAtlMap::SetOptimalLoad  
 Llamar a este método para establecer la carga óptima de la `CAtlMap` objeto.  
  
```
void SetOptimalLoad(
    float fOptimalLoad,
    float fLoThreshold,
    float fHiThreshold,
    bool bRehashNow = false);
```  
  
### <a name="parameters"></a>Parámetros  
 `fOptimalLoad`  
 La proporción de carga óptima.  
  
 `fLoThreshold`  
 Umbral inferior para la proporción de carga.  
  
 `fHiThreshold`  
 Umbral superior para la proporción de carga.  
  
 `bRehashNow`  
 Marca que indica si se debe volver a calcular la tabla hash.  
  
### <a name="remarks"></a>Comentarios  
 Este método vuelve a definir el valor óptimo de carga para el `CAtlMap` objeto. Vea [CAtlMap::CAtlMap](#catlmap) para obtener una explicación de los distintos parámetros. Si `bRehashNow` es true y el número de elementos está fuera de los valores mínimo y máximos, se vuelve a calcular la tabla hash.  
  
##  <a name="setvalueat"></a>CAtlMap::SetValueAt  
 Llamar a este método para cambiar el valor almacenado en una posición determinada en la `CAtlMap` objeto.  
  
```
void SetValueAt(
    POSITION pos,
    VINARGTYPE value);
```  
  
### <a name="parameters"></a>Parámetros  
 `pos`  
 El contador de posición, devuelto por una llamada anterior a [CAtlMap::GetNextAssoc](#getnextassoc) o [CAtlMap::GetStartPosition](#getstartposition).  
  
 *valor*  
 El valor para agregar a la `CAtlMap` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Cambia el elemento de valor almacenado en la posición especificada en el `CAtlMap` objeto.  
  
##  <a name="vinargtype"></a>CAtlMap::VINARGTYPE  
 Tipo que se utiliza cuando un valor se pasa como un argumento de entrada.  
  
```
typedef VTraits::INARGTYPE VINARGTYPE;
```  
  
##  <a name="voutargtype"></a>CAtlMap::VOUTARGTYPE  
 Tipo que se utiliza cuando un valor se pasa como un argumento de salida.  
  
```
typedef VTraits::OUTARGTYPE VOUTARGTYPE;
```  
  
##  <a name="m_key"></a>CAtlMap::CPair::m_key  
 El miembro de datos que se almacena el elemento key.  
  
```
const K m_key;
```    
  
### <a name="parameters"></a>Parámetros  
 `K`  
 El tipo de elemento de la clave.  
  
##  <a name="m_value"></a>CAtlMap::CPair::m_value  
 El miembro de datos que se almacena el elemento de valor.  
  
```
V  m_value;
```    
  
### <a name="parameters"></a>Parámetros  
 *V*  
 El tipo de elemento de valor.  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo de marquesina](../../visual-cpp-samples.md)   
 [Ejemplo UpdatePV](../../visual-cpp-samples.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
