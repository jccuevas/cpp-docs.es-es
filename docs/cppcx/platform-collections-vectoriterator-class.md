---
title: Vectoriterator (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: COLLECTION/Platform::Collections::VectorIterator::VectorIterator
dev_langs: C++
helpviewer_keywords: VectorIterator Class
ms.assetid: d531cb42-27e0-48a6-bf5e-c265891a18ff
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 703035c7a5b2b32df95f83b42327b0965c98b4fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="platformcollectionsvectoriterator-class"></a>Platform::Collections::VectorIterator (Clase)
Proporciona un iterador de la biblioteca de plantillas estándar para los objetos que se deriva de la interfaz IVector de Windows en tiempo de ejecución.  
  
 VectorIterator es un iterador de proxy que almacena elementos de tipo VectorProxy\<T >. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename T>  
class VectorIterator;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El typename de la clase de plantilla VectorIterator.  
  
### <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`difference_type`|Una diferencia de puntero (ptrdiff_t).|  
|`iterator_category`|La categoría de un iterador de acceso aleatorio (::std::random_access_iterator_tag).|  
|`pointer`|Un puntero a un tipo interno, Platform::Collections::Details::VectorProxy\<T >, que es necesario para la implementación de VectorIterator.|  
|`reference`|Una referencia a un tipo interno, Platform::Collections::Details::VectorProxy\<T >, que es necesario para la implementación de VectorIterator.|  
|`value_type`|El typename `T` .|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Vectoriterator](#ctor)|Inicializa una nueva instancia de la clase VectorIterator.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[VectorIterator::operator[] (Operador)](#operator-minus)|Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.|  
|[VectorIterator::operator[] (Operador)](#operator-decrement)|Disminuye el objeto VectorIterator actual.|  
|[VectorIterator::operator!= (Operador)](#operator-inequality)|Indica si el objeto VectorIterator actual no es igual que un objeto VectorIterator especificado.|  
|[VectorIterator::operator[] (Operador)](#operator-dereference)|Recupera una referencia al elemento especificado por el objeto VectorIterator actual.|  
|[Vectoriterator:: operator\[\]](#operator-at)|Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorIterator actual.|  
|[VectorIterator::operator+ (Operador)](#operator-plus)|Devuelve un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator especificado.|  
|[VectorIterator::operator++ (Operador)](#operator-increment)|Incrementa el objeto VectorIterator actual.|  
|[VectorIterator::operator+= (Operador)](#operator-plus-assign)|Incrementa el objeto VectorIterator actual en el desplazamiento especificado.|  
|[VectorIterator::operator< (Operador)](#operator-less-than)|Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.|  
|[Vectoriterator:: operator\<= (operador)](#operator-less-than-or-equals)|Indica si el objeto VectorIterator actual es menor o igual que un objeto VectorIterator especificado.|  
|[VectorIterator::operator-= (Operador)](#operator-subtract-assign)|Disminuye el VectorIterator actual según el desplazamiento especificado.|  
|[VectorIterator::operator== (Operador)](#operator-equality)|Indica si el objeto VectorIterator actual es igual que un objeto VectorIterator especificado.|  
|[VectorIterator::operator> (Operador)](#operator-greater-than)|Indica si el objeto VectorIterator actual es mayor que un objeto VectorIterator especificado.|  
|[VectorIterator::operator-> (Operador)](#operator-arrow)|Recupera la dirección del elemento al que hace referencia el objeto VectorIterator actual.|  
|[VectorIterator::operator>= (Operador)](#operator-greater-than-or-equal)|Indica si el objeto VectorIterator actual es mayor o igual que el objeto VectorIterator especificado.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `VectorIterator`  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  

## <a name="operator-arrow"></a>Vectoriterator:: operator -&gt; (operador)
Recupera la dirección del elemento al que hace referencia el objeto VectorIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor del elemento al que hace referencia el objeto VectorIterator actual.  
  
 El tipo del valor devuelto es un tipo interno no especificado que se requiere para la implementación de este operador.  
  


## <a name="operator-decrement"></a>Vectoriterator:: operator--(operador)
Disminuye el objeto VectorIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
VectorIterator& operator--();  
VectorIterator operator--(int);  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La primera sintaxis disminuye y devuelve después el objeto VectorIterator actual. La segunda sintaxis devuelve una copia del objeto VectorIterator actual y disminuye después el objeto VectorIterator actual.  
  
### <a name="remarks"></a>Comentarios  
 La primera sintaxis de VectorIterator disminuye previamente el objeto VectorIterator actual.  
  
 La segunda sintaxis disminuye posteriormente el objeto VectorIterator actual. El `int` tipo en la segunda sintaxis indica una operación de decremento posterior, no un operando entero real.  
  


## <a name="operator-dereference"></a>Operador de vectoriterator:: operator
Recupera la dirección del elemento especificado por el objeto VectorIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
reference operator*() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento especificado por el objeto VectorIterator actual.  
  


## <a name="operator-equality"></a>Vectoriterator:: operator == (operador)
Indica si el objeto VectorIterator actual es igual que un objeto VectorIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator==(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 Es `true` si el objeto VectorIterator actual es igual que `other`; de lo contrario, es `false`.  
  


## <a name="operator-greater-than"></a>Vectoriterator:: operator&gt; (operador)
Indica si el objeto VectorIterator actual es mayor que un objeto VectorIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
bool operator>(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el objeto VectorIterator actual es mayor que `other`; en caso contrario, `false`.  
  


## <a name="operator-greater-than-or-equals"></a>Vectoriterator:: operator&gt;= (operador)
Indica si el objeto VectorIterator actual es mayor o igual que el objeto VectorIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
bool operator>=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si el objeto VectorIterator actual es mayor o igual que `other`; en caso contrario, `false`.    


## <a name="operator-increment"></a>Vectoriterator:: operator ++ (operador)
Incrementa el objeto VectorIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```    
VectorIterator& operator++();  
VectorIterator operator++(int);  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La primera sintaxis incrementa y devuelve después el objeto VectorIterator actual. La segunda sintaxis devuelve una copia del objeto VectorIterator actual e incrementa después el objeto VectorIterator actual.  
  
### <a name="remarks"></a>Comentarios  
 La primera sintaxis de VectorIterator incrementa previamente el objeto VectorIterator actual.  
  
 La segunda sintaxis incrementa posteriormente el objeto VectorIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.  
  


## <a name="operator-inequality"></a>Vectoriterator:: operator! = (operador)
Indica si el objeto VectorIterator actual no es igual que un objeto VectorIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator!=(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el objeto VectorIterator actual no es igual a `other`; en caso contrario, `false`.  
  


## <a name="operator-less-than"></a>Vectoriterator:: operator&lt; (operador)
Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
bool operator<(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 Es `true` si el objeto VectorIterator actual es menor que `other`; de lo contrario, es `false`.  
  


## <a name="operator-less-than-or-equals"></a>Vectoriterator:: operator&lt;= (operador)
Indica si el objeto VectorIterator actual es menor o igual que un objeto VectorIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
  
bool operator<=(const VectorIterator& other) const   
```  
  
### <a name="parameters"></a>Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el objeto VectorIterator actual es menor o igual que `other`; en caso contrario, `false`.  
  


## <a name="operator-minus"></a>Vectoriterator:: operator-(operador)
Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
VectorIterator operator-(difference_type n) const;  
  
difference_type operator-(const VectorIterator& other) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `n`  
 Número de elementos.  
  
 `other`  
 Otro objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 La sintaxis del primer operador devuelve un objeto VectorIterator que tiene `n` elementos menos que el objeto VectorIterator actual. La segunda sintaxis del operador devuelve el número de elementos entre el actual y la `other` VectorIterator.  
  


## <a name="operator-plus-assign"></a>Vectoriterator:: operator += (operador)
Incrementa el objeto VectorIterator actual en el desplazamiento especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
VectorIterator& operator+=(difference_type n);  
```  
  
### <a name="parameters"></a>Parámetros  
 `n`  
 Desplazamiento entero.  
  
### <a name="return-value"></a>Valor devuelto  
 VectorIterator actualizado.  
  


## <a name="operator-plus"></a>ectorIterator::operator + (operador)
Devuelve un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
  
VectorIterator operator+(difference_type n);  
  
template <typename T>  
inline VectorIterator<T> operator+(
  ptrdiff_t n, 
  const VectorIterator<T>& i);  
  
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 En la segunda sintaxis, el typename del objeto VectorIterator.  
  
 `n`  
 Desplazamiento entero.  
  
 `i`  
 En la segunda sintaxis, un objeto VectorIterator.  
  
### <a name="return-value"></a>Valor devuelto  
 En la primera sintaxis, un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator actual.  
  
 En la segunda sintaxis, un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el principio del parámetro `i`.  
  
### <a name="remarks"></a>Comentarios  
 El ejemplo de la primera sintaxis  
  


## <a name="operator-minus-equals"></a>Vectoriterator:: operator-= (operador)
Disminuye el VectorIterator actual según el desplazamiento especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
VectorIterator& operator-=(difference_type n);  
```  
  
### <a name="parameters"></a>Parámetros  
 `n`  
 Desplazamiento entero.  
  
### <a name="return-value"></a>Valor devuelto  
 VectorIterator actualizado.  
  


## <a name="operator-at"></a>Vectoriterator:: operator\[\]
Recupera una referencia al elemento que es un desplazamiento especificado del objeto VectorIterator actual.  
  
### <a name="syntax"></a>Sintaxis  
  
```    
reference operator[](difference_type n) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `n`  
 Desplazamiento entero.  
  
### <a name="return-value"></a>Valor devuelto  
 El elemento que se desplaza `n` elementos del objeto VectorIterator actual.  
  


## <a name="ctor"></a>Constructor de Vectoriterator
Inicializa una nueva instancia de la clase VectorIterator.  
  
### <a name="syntax"></a>Sintaxis  
  
```    
VectorIterator();  
  
explicit VectorIterator(  
   Windows::Foundation::Collections::IVector<T>^ v);  
```  
  
### <a name="parameters"></a>Parámetros  
 `v`  
 Un IVector\<T > objeto.  
  
### <a name="remarks"></a>Comentarios  
 El primer ejemplo de sintaxis es el constructor predeterminado. El segundo ejemplo de sintaxis es un constructor explícito que se usa para construir un VectorIterator desde un IVector\<T > objeto.  
  


  
## <a name="see-also"></a>Vea también  
 [Namespace de plataforma](platform-namespace-c-cx.md)