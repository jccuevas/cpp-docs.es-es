---
title: Clase CAtlArray | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlArray
- ATL.CAtlArray
- CAtlArray
dev_langs:
- C++
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5fe987e428fc0dcf3e40bfb16aa26bcb90339aff
ms.lasthandoff: 02/24/2017

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
|[Add](#add)|Llame a este método para agregar un elemento al objeto array.|  
|[Anexar](#append)|Llame a este método para agregar el contenido de una matriz al final de la otra.|  
|[AssertValid](#assertvalid)|Llamar a este método para confirmar que el objeto de matriz es válido.|  
|[CAtlArray](#catlarray)|El constructor.|  
|[~ CAtlArray](#dtor)|Destructor.|  
|[Copia](#copy)|Llame a este método para copiar los elementos de una matriz a otra.|  
|[FreeExtra](#freeextra)|Llame a este método para quitar los elementos vacíos de la matriz.|  
|[GetAt](#getat)|Llame a este método para recuperar un único elemento del objeto de matriz.|  
|[GetCount](#getcount)|Llame a este método para devolver el número de elementos almacenados en la matriz.|  
|[GetData](#getdata)|Llame a este método para devolver un puntero al primer elemento de la matriz.|  
|[InsertArrayAt](#insertarrayat)|Llamar a este método para insertar una matriz a otra.|  
|[InsertAt](#insertat)|Llamar a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.|  
|[IsEmpty](#isempty)|Llamar a este método para comprobar si la matriz está vacía.|  
|[RemoveAll](#removeall)|Llame a este método para quitar todos los elementos del objeto de matriz.|  
|[RemoveAt](#removeat)|Llame a este método para quitar uno o más elementos de la matriz.|  
|[SetAt](#setat)|Llamar a este método para establecer el valor de un elemento en el objeto de matriz.|  
|[SetAtGrow](#setatgrow)|Llamar a este método para establecer el valor de un elemento en el objeto de matriz, expandir la matriz según sea necesario.|  
|[SetCount](#setcount)|Llamar a este método para establecer el tamaño del objeto de matriz.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operator&#91;&#93;](#operator_at)|Llame a este operador para devolver una referencia a un elemento de la matriz.|  

  
### <a name="typedefs"></a>Definiciones de tipo  
  
|||  
|-|-|  
|[INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos a la matriz.|  
|[OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de la matriz.|  
  
## <a name="remarks"></a>Comentarios  
 **CAtlArray** proporciona métodos para crear y administrar una matriz de elementos de un tipo definido por el usuario. Aunque es similar a las matrices de C estándares, el **CAtlArray** objeto dinámicamente puede reducir y crecer según sea necesario. El índice de matriz siempre se inicia en la posición 0 y el límite superior puede fijo o se puede ampliar a medida que se agregan nuevos elementos.  
  
 Para matrices con un número pequeño de elementos, la clase ATL [CSimpleArray](../../atl/reference/csimplearray-class.md) se puede usar.  
  
 **CAtlArray** está estrechamente relacionado con el de MFC **CArray** clase y funcionará en un proyecto MFC, aunque sin compatibilidad con la serialización.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="a-nameadda--catlarrayadd"></a><a name="add"></a>CAtlArray::Add  
 Llame a este método para agregar un elemento al objeto array.  
  
```
size_t Add(INARGTYPE element);
size_t Add();
```  
  
### <a name="parameters"></a>Parámetros  
 `element`  
 El elemento que se agrega a la matriz.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el índice del elemento agregado.  
  
### <a name="remarks"></a>Comentarios  
 El nuevo elemento se agrega al final de la matriz. Si ningún elemento se proporciona, se agrega un elemento vacío; es decir, la matriz aumenta de tamaño como si se ha agregado un elemento real. Si se produce un error en la operación, [AtlThrow](http://msdn.microsoft.com/library/2bd111da-8170-488d-914a-c9bf6b6765f7) se llama con el argumento E_OUTOFMEMORY.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[1 NVC_ATL_Utilities](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]  
  
##  <a name="a-nameappenda--catlarrayappend"></a><a name="append"></a>CAtlArray::Append  
 Llame a este método para agregar el contenido de una matriz al final de la otra.  
  
```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `aSrc`  
 La matriz para anexar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el índice del primer elemento anexado.  
  
### <a name="remarks"></a>Comentarios  
 Los elementos de la matriz proporcionada se agregan al final de la matriz existente. Si es necesario, se asignará memoria para dar cabida a los nuevos elementos.  
  
 Las matrices deben ser del mismo tipo y no es posible anexar una matriz a sí mismo.  
  
 En compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` argumento no es una matriz válida o si `aSrc` hace referencia al mismo objeto. En versiones de lanzamiento, argumentos no válidos pueden provocar un comportamiento impredecible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#2;](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]  
  
##  <a name="a-nameassertvalida--catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid  
 Llamar a este método para confirmar que el objeto de matriz es válido.  
  
```
void AssertValid() const;
```  
  
### <a name="remarks"></a>Comentarios  
 Si no es válido, el objeto array `ATLASSERT` producirá una aserción. Este método está disponible sólo si está definido _DEBUG.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&3;](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]  
  
##  <a name="a-namecatlarraya--catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray  
 El constructor.  
  
```
CAtlArray() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el objeto de matriz.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&4;](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]  
  
##  <a name="a-namedtora--catlarraycatlarray"></a><a name="dtor"></a>CAtlArray:: ~ CAtlArray  
 Destructor.  
  
```
~CAtlArray() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera los recursos utilizados por el objeto de matriz.  
  
##  <a name="a-namecopya--catlarraycopy"></a><a name="copy"></a>CAtlArray::Copy  
 Llame a este método para copiar los elementos de una matriz a otra.  
  
```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```  
  
### <a name="parameters"></a>Parámetros  
 `aSrc`  
 El origen de los elementos que se van a copiar en una matriz.  
  
### <a name="remarks"></a>Comentarios  
 Llamar a este método para sobrescribir los elementos de una matriz con los elementos de otra matriz. Si es necesario, se asignará memoria para dar cabida a los nuevos elementos. No es posible copiar los elementos de una matriz a sí mismo.  
  
 Si el contenido de la matriz se conservarán, utilice [CAtlArray::Append](#append) en su lugar.  
  
 En compilaciones de depuración, se generará una ATLASSERT si existente `CAtlArray` objeto no es válido, o si `aSrc` hace referencia al mismo objeto. En versiones de lanzamiento, argumentos no válidos pueden provocar un comportamiento impredecible.  
  
> [!NOTE]
> `CAtlArray::Copy`no admite matrices que consta de los elementos creados con la [CAutoPtr](../../atl/reference/cautoptr-class.md) clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#5;](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]  
  
##  <a name="a-namefreeextraa--catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra  
 Llame a este método para quitar los elementos vacíos de la matriz.  
  
```
void FreeExtra() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Se quitan los elementos vacíos, pero el tamaño y el límite superior de la matriz no cambian.  
  
 En compilaciones de depuración, se generará una ATLASSERT si el objeto CAtlArray no es válido o si la matriz es mayor que su tamaño máximo.  
  
##  <a name="a-namegetata--catlarraygetat"></a><a name="getat"></a>CAtlArray::GetAt  
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
 En compilaciones de depuración, se generará una ATLASSERT si `iElement` supera el número de elementos de la matriz. En versiones de lanzamiento, un argumento no válido puede provocar un comportamiento impredecible.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&6;](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]  
  
##  <a name="a-namegetcounta--catlarraygetcount"></a><a name="getcount"></a>CAtlArray::GetCount  
 Llame a este método para devolver el número de elementos almacenados en la matriz.  
  
```
size_t GetCount() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el número de elementos almacenados en la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Como el primer elemento de la matriz en la posición 0, el valor devuelto por `GetCount` siempre es mayor que el índice más grande de 1.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::GetAt](#getat).  
  
##  <a name="a-namegetdataa--catlarraygetdata"></a><a name="getdata"></a>CAtlArray::GetData  
 Llame a este método para devolver un puntero al primer elemento de la matriz.  
  
```
E* GetData() throw();
const E* GetData() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la ubicación de memoria que almacena el primer elemento de la matriz. Si no hay elementos disponibles, se devuelve NULL.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#7;](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]  
  
##  <a name="a-nameinargtypea--catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE  
 El tipo de datos que se usará para agregar elementos a la matriz.  
  
```
typedef ETraits::INARGTYPE INARGTYPE;
```  
  
##  <a name="a-nameinsertarrayata--catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt  
 Llamar a este método para insertar una matriz a otra.  
  
```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```  
  
### <a name="parameters"></a>Parámetros  
 `iStart`  
 Índice en el que la matriz se va a insertar.  
  
 `paNew`  
 Matriz que se va a insertar.  
  
### <a name="remarks"></a>Comentarios  
 Elementos de la matriz `paNew` se copian en el objeto de matriz, empezando por el elemento `iStart`. Los elementos de matriz existente se mueven para evitar que se sobrescriban.  
  
 En compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido, o si el `paNew` puntero es NULL o no es válido.  
  
> [!NOTE]
> `CAtlArray::InsertArrayAt`no admite matrices que consta de los elementos creados con la [CAutoPtr](../../atl/reference/cautoptr-class.md) clase.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities Nº&8;](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]  
  
##  <a name="a-nameinsertata--catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::InsertAt  
 Llamar a este método para insertar un nuevo elemento (o varias copias de un elemento) en el objeto de matriz.  
  
```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El índice donde son el elemento o elementos que se va a insertar.  
  
 `element`  
 El valor del elemento o elementos que se va a insertar.  
  
 `nCount`  
 El número de elementos que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 Inserta uno o más elementos en la matriz, comenzando en el índice `iElement`. Se mueven los elementos existentes para evitar que se sobrescriban.  
  
 En compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido, el número de elementos que se va a agregar es cero o es demasiado grande para la matriz que contendrá el número total de elementos. En las compilaciones comerciales, pasar parámetros no válidos puede producir resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#9;](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]  
  
##  <a name="a-nameisemptya--catlarrayisempty"></a><a name="isempty"></a>CAtlArray::IsEmpty  
 Llamar a este método para comprobar si la matriz está vacía.  
  
```
bool IsEmpty() const throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la matriz es vacía, lo contrario false.  
  
### <a name="remarks"></a>Comentarios  
 Se dice que vacío si no contiene ningún elemento de la matriz. Por lo tanto, incluso si la matriz contiene elementos vacíos, no está vacío.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#10;](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]  
  
##  <a name="a-nameoperatorata--catlarrayoperator-"></a><a name="operator_at"></a>[] CAtlArray::operator  
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
 Realiza una función similar a [CAtlArray::GetAt](#getat). A diferencia de la clase MFC [CArray](../../mfc/reference/carray-class.md), este operador no se puede utilizar como sustituto de [CAtlArray::SetAt](#setat).  
  
 En compilaciones de depuración, se generará una ATLASSERT si `iElement` supera el número total de elementos de la matriz. En las compilaciones comerciales, un parámetro incorrecto puede provocar resultados imprevisibles.  
  
##  <a name="a-nameoutargtypea--catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de la matriz.  
  
```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```  
  
##  <a name="a-nameremovealla--catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::RemoveAll  
 Llame a este método para quitar todos los elementos del objeto de matriz.  
  
```
void RemoveAll() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Quita todos los elementos del objeto de matriz.  
  
 Este método llama a [CAtlArray::SetCount](#setcount) para cambiar el tamaño de la matriz y después libera la memoria asignada.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::IsEmpty](#isempty).  
  
##  <a name="a-nameremoveata--catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::RemoveAt  
 Llame a este método para quitar uno o más elementos de la matriz.  
  
```
void RemoveAt(size_t iElement, size_t nCount = 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 Índice del primer elemento que se quita.  
  
 `nCount`  
 Número de elementos que se va a quitar.  
  
### <a name="remarks"></a>Comentarios  
 Quita uno o más elementos de la matriz. Los elementos restantes se desplazan hacia abajo. El límite superior es reducido, pero no se libera memoria hasta que una llamada a [CAtlArray::FreeExtra](#freeextra) se realiza.  
  
 En compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido, o si el total combinado de `iElement` y `nCount` supera el número total de elementos de la matriz. En las compilaciones comerciales, los parámetros no válidos pueden producir resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#11;](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]  
  
##  <a name="a-namesetata--catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt  
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
 En compilaciones de depuración, se generará una ATLASSERT si `iElement` supera el número de elementos de la matriz. En las compilaciones comerciales, un parámetro no válido puede producir resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::GetAt](#getat).  
  
##  <a name="a-namesetcounta--catlarraysetcount"></a><a name="setcount"></a>CAtlArray::SetCount  
 Llamar a este método para establecer el tamaño del objeto de matriz.  
  
```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```  
  
### <a name="parameters"></a>Parámetros  
 `nNewSize`  
 El tamaño necesario de la matriz.  
  
 `nGrowBy`  
 Un valor que se utiliza para determinar el tamaño del búfer. El valor -1 hace que un valor calculado internamente para usarse.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si la matriz está correctamente cuyo tamaño ha cambiado.  
  
### <a name="remarks"></a>Comentarios  
 La matriz se puede incrementar o disminuir de tamaño. Si aumenta, se agregan elementos vacíos adicionales a la matriz. Si se reduce, se eliminarán los elementos con los índices más grandes y liberar memoria.  
  
 Utilice este método para establecer el tamaño de la matriz antes de usarlo. Si `SetCount` no se utiliza, el proceso de agregar elementos, y realice la asignación de memoria posterior, reducirá el rendimiento y fragmentar la memoria.  
  
### <a name="example"></a>Ejemplo  
 Vea el ejemplo de [CAtlArray::GetData](#getdata).  
  
##  <a name="a-namesetatgrowa--catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow  
 Llamar a este método para establecer el valor de un elemento en el objeto de matriz, expandir la matriz según sea necesario.  
  
```
void SetAtGrow(size_t iElement, INARGTYPE element);
```  
  
### <a name="parameters"></a>Parámetros  
 `iElement`  
 El índice que apunta al elemento de matriz para establecer.  
  
 `element`  
 El nuevo valor del elemento especificado.  
  
### <a name="remarks"></a>Comentarios  
 Sustituye el valor del elemento señalado por el índice. Si `iElement` es mayor que el tamaño actual de la matriz, la matriz aumenta automáticamente mediante una llamada a [CAtlArray::SetCount](#setcount). En compilaciones de depuración, se generará una ATLASSERT si la `CAtlArray` objeto no es válido. En las compilaciones comerciales, los parámetros no válidos pueden producir resultados imprevisibles.  
  
### <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_Utilities&#12;](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo MMXSwarm](../../visual-cpp-samples.md)   
 [Ejemplo DynamicConsumer](../../visual-cpp-samples.md)   
 [Ejemplo UpdatePV](../../visual-cpp-samples.md)   
 [Ejemplo de marquesina](../../visual-cpp-samples.md)   
 [CArray (clase)](../../mfc/reference/carray-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

