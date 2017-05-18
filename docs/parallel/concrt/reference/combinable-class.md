---
title: Clase combinable | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- combinable
- PPL/concurrency::combinable
- PPL/concurrency::combinable::combinable
- PPL/concurrency::combinable::clear
- PPL/concurrency::combinable::combine
- PPL/concurrency::combinable::combine_each
- PPL/concurrency::combinable::local
dev_langs:
- C++
helpviewer_keywords:
- combinable class
ms.assetid: fe0bfbf6-6250-47da-b8d0-f75369f0b5be
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: a491f8eef59978808608917531a5237cceacdb21
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="combinable-class"></a>Clase combinable
El objeto `combinable<T>` está diseñado para proporcionar copias de subprocesos privados de datos, para realizar subcálculos de subprocesos locales sin bloqueos durante algoritmos paralelos. Al final de la operación paralela, los subcálculos de subprocesos privados pueden combinarse en un resultado final. Esta clase se puede utilizar en lugar de una variable compartida y puede dar lugar a una mejora en el rendimiento que, de lo contrario, daría lugar a mucha contención en esa variable compartida.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>
class combinable;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos del resultado combinado final. El tipo debe tener un constructor de copias y un constructor predeterminado.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[clase combinable](#ctor)|Sobrecargado. Construye un nuevo objeto `combinable`.|  
|[~ combinable (destructor)](#dtor)|Destruye un objeto `combinable`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[clear](#clear)|Borra cualquier resultado computacional intermedio de un uso anterior.|  
|[combine](#combine)|Calcula un valor final del conjunto de subprocesos locales sin bloqueos llamando al functor de combinación.|  
|[combine_each](#combine_each)|Calcula un valor final del conjunto de subprocesos locales sin bloqueos llamando al functor de combinación una vez por cálculo de subdirectorio local de subproceso. El objeto de función acumula el resultado final.|  
|[local](#local)|Sobrecargado. Devuelve una referencia al cálculo de subdirectorio de subprocesos privados.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operator=](#operator_eq)|Asigna a un `combinable` objeto desde otro `combinable` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información, consulte [objetos y contenedores paralelos](../../../parallel/concrt/parallel-containers-and-objects.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `combinable`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="clear"></a>Borrar 

 Borra cualquier resultado computacional intermedio de un uso anterior.  
  
```
void clear();
```  
  
##  <a name="ctor"></a>clase combinable 

 Construye un nuevo objeto `combinable`.  
  
```
combinable();

template <typename _Function>
explicit combinable(_Function _FnInitialize);

combinable(const combinable& _Copy);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Function`  
 El tipo de objeto functor de inicialización.  
  
 `_FnInitialize`  
 Una función que se llamará para inicializar cada nuevo valor de subprocesos privados del tipo `T`. Debe admitir un operador de llamada de función con la firma `T ()`.  
  
 `_Copy`  
 Existente `combinable` objeto se copia en éste.  
  
### <a name="remarks"></a>Comentarios  
 El primer constructor inicializa nuevos elementos con el constructor predeterminado para el tipo de `T`.  
  
 El segundo constructor inicializa nuevos elementos mediante el functor de inicialización proporcionado como el `_FnInitialize` parámetro.  
  
 El tercer constructor es el constructor de copia.  
  
##  <a name="dtor"></a>~ combinable 

 Destruye un objeto `combinable`.  
  
```
~combinable();
```  
  
##  <a name="combine"></a>combinar 

 Calcula un valor final del conjunto de subprocesos locales sin bloqueos llamando al functor de combinación.  
  
```
template<typename _Function>
T combine(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Function`  
 El tipo de objeto de función que se invocará para combinar dos subprocesos locales sin bloqueos.  
  
 `_FnCombine`  
 El functor que se usa para combinar los cálculos secundarios. Su firma es `T (T, T)` o `T (const T&, const T&)`, y debe ser asociativa y conmutativa.  
  
### <a name="return-value"></a>Valor devuelto  
 El resultado final de combinar todos los subcálculos de subprocesos privados.  
  
##  <a name="combine_each"></a>combine_each 

 Calcula un valor final del conjunto de subprocesos locales sin bloqueos llamando al functor de combinación una vez por cálculo de subdirectorio local de subproceso. El objeto de función acumula el resultado final.  
  
```
template<typename _Function>
void combine_each(_Function _FnCombine) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Function`  
 El tipo de objeto de función que se invocará para combinar un cálculo de subdirectorio local de subproceso único.  
  
 `_FnCombine`  
 El functor que se usa para combinar un subcálculo. Su firma es `void (T)` o `void (const T&)`y debe ser asociativa y conmutativa.  
  
##  <a name="local"></a>local 

 Devuelve una referencia al cálculo de subdirectorio de subprocesos privados.  
  
```
T& local();

T& local(bool& _Exists);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Exists`  
 Una referencia a un valor booleano. El valor booleano al que hace referencia este argumento se establecerá en `true` si el cálculo secundario ya existe en este subproceso y establece en `false` si se trata del primer subcálculo en este subproceso.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al cálculo de subdirectorio de subprocesos privados.  
  
##  <a name="operator_eq"></a>operador = 

 Asigna a un `combinable` objeto desde otro `combinable` objeto.  
  
```
combinable& operator= (const combinable& _Copy);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Copy`  
 Existente `combinable` objeto se copia en éste.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a este `combinable` objeto.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

