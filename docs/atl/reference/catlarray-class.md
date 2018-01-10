---
title: Clase CAtlArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
dev_langs: C++
helpviewer_keywords: CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ffebf8289b7c1eb5ccaae5a6b6a5f2a3f939cbb9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catlarray-class"></a>Clase CAtlArray
Esta clase implementa un objeto de matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```  
  
#### <a name="parameters"></a>Parámetros  
 *E*  
 Tipo de datos que se va a almacenar en la matriz.  
  
 *ETraits*  
 El código utilizado para copiar o mover elementos.  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Add](#add)|Llame a este método para agregar un elemento al objeto de matriz.|  
|[Anexar](#append)|Llamar a este método para agregar el contenido de una matriz al final de la otra.|  
|[AssertValid](#assertvalid)|Llamar a este método para confirmar que el objeto de matriz es válido.|  
|[CAtlArray](#catlarray)|El constructor.|  
|[~ CAtlArray](#dtor)|Destructor.|  
|[Copiar](#copy)|Llamar a este método para copiar los elementos de una matriz a otra.|  
|[FreeExtra](#freeextra)|Llame a este método para quitar los elementos vacíos de la matriz.|  
|[GetAt](#getat)|Llamar a este método para recuperar un único elemento del objeto de matriz.|  
|[GetCount](#getcount)|Llamar a este método para devolver el número de elementos almacenados en la matriz.|  
|[GetData](#getdata)|Llame a este método para devolver un puntero al primer elemento de la matriz.|  
|[InsertArrayAt](#insertarrayat)|Llamar a este método para insertar una matriz en otra.|  
|[InsertAt](#insertat)|Llamar a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.|  
|[IsEmpty](#isempty)|Llamar a este método para comprobar si la matriz está vacía.|  
|[RemoveAll](#removeall)|Llame a este método para quitar todos los elementos del objeto de matriz.|  
|[RemoveAt](#removeat)|Llame a este método para quitar uno o más elementos de la matriz.|  
|[SetAt](#setat)|Llamar a este método para establecer el valor de un elemento en el objeto de matriz.|  
|[SetAtGrow](#setatgrow)|Llamar a este método para establecer el valor de un elemento en el objeto de matriz, expandiendo la matriz según sea necesario.|  
|[SetCount](#setcount)|Llamar a este método para establecer el tamaño del objeto de matriz.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador &#91; &#93;](#operator_at)|Llame a este operador para devolver una referencia a un elemento de la matriz.|  

  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos a la matriz.|  
|[OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de la matriz.|  
  
## <a name="remarks"></a>Comentarios  
 **CAtlArray** proporciona métodos para crear y administrar una matriz de elementos de un tipo definido por el usuario. Aunque es similar a las matrices de C estándares, el **CAtlArray** objeto dinámicamente puede reducir y crecer según sea necesario. El índice de matriz siempre se inicia en la posición 0, y el límite superior puede ser fijo o pueden ampliar a medida que se agregan nuevos elementos.  
  
 Para las matrices con un número pequeño de elementos, la clase ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) puede utilizarse.  
  
 **CAtlArray** está estrechamente relacionado con el de MFC **CArray** clase y funcionará en un proyecto MFC, pero sin compatibilidad con la serialización.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="add"></a>CAtlArray::Add  
 Llame a este método para agregar un elemento al objeto de matriz.  
  
```
size_t Add(INARGTYPE element);
size_t Add();
```  
  
### <a name="parameters"></a>Parámetros  
 `element`  
 El elemento que se va a agregar a la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el índice del elemento agregado.  
  
### <a name="remarks"></a>Comentarios  
 El nuevo elemento se agrega al final de la matriz. Si ningún elemento se proporciona, se agrega un elemento vacío; es decir, la matriz aumenta de tamaño como si se ha agregado un elemento real. Si se produce un error en la operación, [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) se llama con el argumento E_OUTOFMEMORY.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]  
  
##  <a name="append"></a>CAtlArray::Append  
 Llamar a este método para agregar el contenido de una matriz al final de la otra.  
  
```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `aSrc`  
 La matriz que se anexará.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el índice del primer elemento anexado.  
  
### <a name="remarks"></a>Comentarios  
 Los elementos de la matriz proporcionada se agregan al final de la matriz existente. Si es necesario, se puede asignar memoria para dar cabida a los nuevos elementos.  
  
 Las matrices deben ser del mismo tipo y no es posible anexar una matriz a sí mismo.  
  
 En las compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` argumento no es una matriz válida o si `aSrc` hace referencia al mismo objeto. En versiones de lanzamiento, argumentos no válidos pueden provocar un comportamiento imprevisible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]  
  
##  <a name="assertvalid"></a>CAtlArray::AssertValid  
 Llamar a este método para confirmar que el objeto de matriz es válido.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Si el objeto de matriz no es válido, `ATLASSERT` producirá una aserción. Este método está disponible sólo si se define _DEBUG.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]  
  
##  <a name="catlarray"></a>CAtlArray::CAtlArray  
 El constructor.  
  
```
CAtlArray() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el objeto de matriz.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]  
  
##  <a name="dtor"></a>CAtlArray:: ~ CAtlArray  
 Destructor.  
  
```
~CAtlArray() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos utilizados por el objeto de matriz.  
  
##  <a name="copy"></a>CAtlArray::Copy  
 Llamar a este método para copiar los elementos de una matriz a otra.  
  
```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `aSrc`  
 El origen de los elementos que se va a copiar en una matriz.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para sobrescribir los elementos de una matriz con los elementos de otra matriz. Si es necesario, se puede asignar memoria para dar cabida a los nuevos elementos. No es posible copiar los elementos de una matriz a sí mismo.  
  
 Si el contenido existente de la matriz se conservarán, utilice [CAtlArray::Append](#append) en su lugar.  
  
 En las compilaciones de depuración, se generará una ATLASSERT si existente `CAtlArray` objeto no es válido, o si `aSrc` hace referencia al mismo objeto. En versiones de lanzamiento, argumentos no válidos pueden provocar un comportamiento imprevisible.  
  
> [!NOTE]
> `CAtlArray::Copy`no admite matrices que consta de los elementos creados con la [CAutoPtr](../../atl/reference/cautoptr-class.md) clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]  
  
##  <a name="freeextra"></a>CAtlArray::FreeExtra  
 Llame a este método para quitar los elementos vacíos de la matriz.  
  
```
void FreeExtra() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Se quitan los elementos vacíos, pero el tamaño y el límite superior de la matriz se mantienen intactas.  
  
 En las compilaciones de depuración, se generará una ATLASSERT si el objeto CAtlArray no es válido, o si la matriz, superará el tamaño máximo.  
  
##  <a name="getat"></a>CAtlArray::GetAt  
 Llamada a que este método recupera un único elemento del objeto de matriz.  
  
```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El valor de índice del elemento de matriz para devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al elemento de matriz necesarios.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se generará una ATLASSERT si `iElement` supera el número de elementos de la matriz. En versiones de lanzamiento, un argumento no válido puede provocar un comportamiento imprevisible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]  
  
##  <a name="getcount"></a>CAtlArray::GetCount  
 Llamar a este método para devolver el número de elementos almacenados en la matriz.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos almacenados en la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Como el primer elemento de la matriz es en la posición 0, el valor devuelto por `GetCount` siempre es mayor que el índice más grande de 1.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::GetAt](#getat).  
  
##  <a name="getdata"></a>CAtlArray::GetData  
 Llame a este método para devolver un puntero al primer elemento de la matriz.  
  
```
E* GetData() throw();
const E* GetData() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la ubicación de memoria que almacena el primer elemento de la matriz. Si no hay elementos disponibles, se devuelve NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]  
  
##  <a name="inargtype"></a>CAtlArray::INARGTYPE  
 El tipo de datos que se usará para agregar elementos a la matriz.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="insertarrayat"></a>CAtlArray::InsertArrayAt  
 Llamar a este método para insertar una matriz en otra.  
  
```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `iStart`  
 Índice en el que la matriz se va a insertar.  
  
 `paNew`  
 La matriz que se va a insertar.  
  
### <a name="remarks"></a>Comentarios  
 Elementos de la matriz `paNew` se copian en el objeto de matriz, empezando por el elemento `iStart`. Los elementos de la matriz existente se mueven para evitar que se sobrescriba.  
  
 En las compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido, o si el `paNew` puntero es NULL o no es válido.  
  
> [!NOTE]
> `CAtlArray::InsertArrayAt`no admite matrices que consta de los elementos creados con la [CAutoPtr](../../atl/reference/cautoptr-class.md) clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]  
  
##  <a name="insertat"></a>CAtlArray::InsertAt  
 Llamar a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.  
  
```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El índice donde el elemento o elementos son va a insertar.  
  
 `element`  
 El valor del elemento o elementos que se va a insertar.  
  
 `nCount`  
 El número de elementos que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Inserta uno o más elementos en la matriz, empezando por el índice `iElement`. Se mueven los elementos existentes para evitar que se sobrescriba.  
  
 En las compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido, el número de elementos que se va a agregar es cero o es demasiado grande para la matriz para que contenga el número combinado de elementos. En las compilaciones comerciales, pasar parámetros no válidos puede provocar resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]  
  
##  <a name="isempty"></a>CAtlArray::IsEmpty  
 Llamar a este método para comprobar si la matriz está vacía.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la matriz en caso contrario, está vacía, false.  
  
### <a name="remarks"></a>Comentarios  
 Se dice que la matriz vacía si no contiene ningún elemento. Por lo tanto, incluso si la matriz contiene elementos vacíos, no está vacío.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]  
  
##  <a name="operator_at"></a>[] CAtlArray::operator  
 Llame a este operador para devolver una referencia a un elemento de la matriz.  
  
```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El valor de índice del elemento de matriz para devolver.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve una referencia al elemento de matriz necesarios.  
  
### <a name="remarks"></a>Comentarios  
 Realiza una función similar a [CAtlArray::GetAt](#getat). A diferencia de la clase MFC [CArray](../../mfc/reference/carray-class.md), este operador no se puede usar como un sustituto de [CAtlArray::SetAt](#setat).  
  
 En las compilaciones de depuración, se generará una ATLASSERT si `iElement` supera el número total de elementos de la matriz. En las compilaciones comerciales, un parámetro incorrecto puede provocar resultados imprevisibles.  
  
##  <a name="outargtype"></a>CAtlArray::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de la matriz.  
  
```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```  
  
##  <a name="removeall"></a>CAtlArray::RemoveAll  
 Llame a este método para quitar todos los elementos del objeto de matriz.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita todos los elementos del objeto de matriz.  
  
 Este método llama a [CAtlArray::SetCount](#setcount) para cambiar el tamaño de la matriz y después libera la memoria asignada.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::IsEmpty](#isempty).  
  
##  <a name="removeat"></a>CAtlArray::RemoveAt  
 Llame a este método para quitar uno o más elementos de la matriz.  
  
```
void RemoveAt(size_t iElement, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El índice del primer elemento para quitar.  
  
 `nCount`  
 Número de elementos que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Quita uno o más elementos de la matriz. Los elementos restantes se desplazan hacia abajo. El límite superior es reducido, pero no se libera memoria hasta que una llamada a [CAtlArray::FreeExtra](#freeextra) se realiza.  
  
 En las compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido, o si el total combinado de `iElement` y `nCount` supera el número total de elementos de la matriz. En las compilaciones comerciales, los parámetros no válidos pueden provocar resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]  
  
##  <a name="setat"></a>CAtlArray::SetAt  
 Llamar a este método para establecer el valor de un elemento en el objeto de matriz.  
  
```
void SetAt(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El índice que apunta al elemento de matriz para establecer.  
  
 `element`  
 El nuevo valor del elemento especificado.  
  
### <a name="remarks"></a>Comentarios  
 En las compilaciones de depuración, se generará una ATLASSERT si `iElement` supera el número de elementos de la matriz. En las compilaciones comerciales, un parámetro no válido puede tener resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::GetAt](#getat).  
  
##  <a name="setcount"></a>CAtlArray::SetCount  
 Llamar a este método para establecer el tamaño del objeto de matriz.  
  
```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNewSize`  
 El tamaño necesario de la matriz.  
  
 `nGrowBy`  
 Un valor que se utiliza para determinar el tamaño que tendrá el búfer. Un valor de -1 hace que un valor calculado internamente para usarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la matriz está correctamente cuyo tamaño ha cambiado.  
  
### <a name="remarks"></a>Comentarios  
 La matriz se puede incrementar o disminuir de tamaño. Si aumenta, se agregan elementos vacíos adicionales a la matriz. Si ha disminuido, se eliminarán los elementos con los índices más grandes y liberar memoria.  
  
 Utilice este método para establecer el tamaño de la matriz antes de usarlo. Si `SetCount` no se utiliza, el proceso de agregar elementos, y lleva a cabo la asignación de memoria posterior, se reduce el rendimiento y fragmentar la memoria.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::GetData](#getdata).  
  
##  <a name="setatgrow"></a>CAtlArray::SetAtGrow  
 Llamar a este método para establecer el valor de un elemento en el objeto de matriz, expandiendo la matriz según sea necesario.  
  
```
void SetAtGrow(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El índice que apunta al elemento de matriz para establecer.  
  
 `element`  
 El nuevo valor del elemento especificado.  
  
### <a name="remarks"></a>Comentarios  
 Reemplaza el valor del elemento que señala el índice. Si `iElement` es mayor que el tamaño actual de la matriz, la matriz se incrementa automáticamente mediante una llamada a [CAtlArray::SetCount](#setcount). En las compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido. En las compilaciones comerciales, los parámetros no válidos pueden provocar resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MMXSwarm](../../visual-cpp-samples.md)   
 [Ejemplo DynamicConsumer](../../visual-cpp-samples.md)   
 [Ejemplo UpdatePV](../../visual-cpp-samples.md)   
 [Ejemplo de marquesina](../../visual-cpp-samples.md)   
 [CArray (clase)](../../mfc/reference/carray-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
