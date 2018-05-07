---
title: Vectorview (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::VectorView::VectorView
- COLLECTION/Platform::Collections::VectorView::First
- COLLECTION/Platform::Collections::VectorView::GetAt
- COLLECTION/Platform::Collections::VectorView::GetMany
- COLLECTION/Platform::Collections::VectorView::IndexOf
- COLLECTION/Platform::Collections::VectorView::Size
dev_langs:
- C++
helpviewer_keywords:
- VectorView Class
ms.assetid: 05cd461d-dce7-49d3-b0e7-2e5c78ed8192
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 937342c340b085f2e2bdeef8ed7df21dae826152
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="platformcollectionsvectorview-class"></a>Platform::Collections::VectorView (Clase)
Representa una vista de solo lectura de una colección secuencial de objetos a los que se puede obtener acceso individualmente por índice. El parámetro de plantilla especifica el tipo de cada objeto de la colección.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename T, typename E>  
   ref class VectorView sealed;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de los elementos contenidos en el objeto `VectorView` .  
  
 `E`  
 Especifica un predicado binario para probar la igualdad con valores de tipo `T`. El valor predeterminado es `std::equal_to<T>`.  
  
### <a name="remarks"></a>Comentarios  
 El `VectorView` la clase implementa la [Windows::Foundation::Collections::IVectorView\<T >](http://go.microsoft.com/fwlink/p/?LinkId=262411) interfaz y compatibilidad con los iteradores de biblioteca de plantillas estándar.  
  
### <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Vectorview](#ctor)|Inicializa una nueva instancia de la clase VectorView.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Vectorview:: First](#first)|Devuelve un iterador que especifica el primer elemento del objeto VectorView.|  
|[Vectorview:: GetAt](#getat)|Recupera el elemento del objeto VectorView actual indicado por el índice especificado.|  
|[Vectorview:: Getmany](#getmany)|Recupera una secuencia de elementos del objeto VectorView actual, empezando en el índice especificado.|  
|[Vectorview:: IndexOf](#indexof)|Busca el elemento especificado en el objeto VectorView actual y, si lo encuentra, devuelve el índice del elemento.|  
|[Vectorview:: Size](#size)|Devuelve el número de elementos del objeto VectorView actual.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `VectorView`  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  

## <a name="first"></a>  Vectorview:: First (método)
Devuelve un iterador que especifica el primer elemento del objeto VectorView.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que especifica el primer elemento del objeto VectorView.  
  
### <a name="remarks"></a>Comentarios  
 Una manera cómoda de contener el iterador devuelto por First() es asignar el valor devuelto a una variable que se declara con el **automática** palabra clave de deducción de tipos. Por ejemplo: `auto x = myVectorView->First();`.  
  


## <a name="getat"></a>  Vectorview:: GetAt (método)
Recupera el elemento del objeto VectorView actual indicado por el índice especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `index`  
 Entero sin signo de base cero que especifica un elemento determinado en el objeto VectorView.  
  
### <a name="return-value"></a>Valor devuelto  
 Elemento especificado por el parámetro `index`. El tipo de elemento especificado por el parámetro de plantilla VectorView *T*.  
  


## <a name="getmany"></a>  Vectorview:: Getmany (método)
Recupera una secuencia de elementos del objeto VectorView actual, empezando en el índice especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
virtual unsigned int GetMany(  
   unsigned int startIndex,   
   ::Platform::WriteOnlyArray<T>^ dest  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `startIndex`  
 Índice basado en cero del principio de los elementos que se van a recuperar.  
  
 `dest`  
 Cuando se completa esta operación, una matriz de elementos que comienzan con el elemento especificado por `startIndex` y termina con el último elemento del objeto vectorview.  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos recuperados.  
  


## <a name="indexof"></a>  Vectorview:: IndexOf (método)
Busca el elemento especificado en el objeto VectorView actual y, si lo encuentra, devuelve el índice del elemento.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `value`  
 El elemento que se va a buscar.  
  
 `index`  
 El índice de base cero del elemento si se encuentra el parámetro `value`; en caso contrario, 0.  
  
 El parámetro `index` es 0 si el elemento es el primer elemento del objeto VectorView o no se encuentra el elemento. Si el valor devuelto es `true`, se encontró el elemento y es el primer elemento; de lo contrario, no se encuentra el elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si se encontró el elemento especificado; de lo contrario, `false`.  
  


## <a name="size"></a>  Vectorview:: Size (método)
Devuelve el número de elementos del objeto VectorView actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
virtual property unsigned int Size;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos del objeto VectorView actual.  
  


## <a name="ctor"></a>  Constructor Vectorview
Inicializa una nueva instancia de la clase VectorView.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
VectorView();  
explicit VectorView(  
   UInt32 size  
);  
VectorView(  
   UInt32 size,  
   T value  
);  
explicit VectorView(  
   const ::std::vector<T>& v  
);  
explicit VectorView(  
   ::std::vector<T>&& v  
);  
VectorView(  
   const T * ptr,  
   UInt32 size  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const T (&arr)[N]  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const ::std::array<T,  
   N>& a  
);  
  
explicit VectorView(  
   const ::Platform::Array<T>^ arr  
);  
  
template <  
   typename InIt  
>  
VectorView(  
   InItfirst,  
   InItlast  
);  
  
VectorView(  
   std::initializer_list<T> il  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 `InIt`  
 El tipo de una colección de objetos que se utiliza para inicializar el objeto VectorView actual.  
  
 il  
 A [std:: initializer_list](../standard-library/initializer-list-class.md) cuyos elementos se usarán para inicializar el objeto VectorView.  
  
 `N`  
 El número de elementos en una colección de objetos que se utiliza para inicializar el objeto VectorView actual.  
  
 `size`  
 El número de elementos del objeto VectorView.  
  
 `value`  
 Un valor que se utiliza para inicializar cada elemento en el objeto VectorView actual.  
  
 `v`  
 Un [Lvalues y Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md) a una [std:: vector](../standard-library/vector-class.md) que se usa para inicializar el objeto VectorView actual.  
  
 `ptr`  
 Puntero a un objeto `std::vector` que se usa para inicializar el objeto VectorView actual.  
  
 `arr`  
 A [Platform:: Array](../cppcx/platform-array-class.md) objeto que se utiliza para inicializar el objeto VectorView actual.  
  
 `a`  
 A [std:: Array](../standard-library/array-class-stl.md) objeto que se utiliza para inicializar el objeto VectorView actual.  
  
 `first`  
 El primer elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo de `first` se pasa por medio de *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
 `last`  
 El último elemento de una secuencia de objetos que se utilizan para inicializar el objeto VectorView actual. El tipo de `last` se pasa por medio de *el reenvío directo*. Para más información, vea [Declarador de referencia a un valor R: &&](../cpp/rvalue-reference-declarator-amp-amp.md).  
  


  
## <a name="see-also"></a>Vea también  
 [Namespace de plataforma](platform-namespace-c-cx.md)   
 [Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)