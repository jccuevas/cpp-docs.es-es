---
title: Clase Platform | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Box
dev_langs:
- C++
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7def63199666a9dba0a1628031129ce584e0fcec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605964"
---
# <a name="platformbox-class"></a>Platform::Box (Clase)
Habilita un tipo de valor como `Windows::Foundation::DateTime` o un tipo escalar como `int` para almacenarlo en un tipo `Platform::Object` . Normalmente no es necesario usar `Box` explícitamente porque la conversión boxing se produce de manera implícita cuando se convierte un tipo de valor a `Object^`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
ref class Box abstract;  
```  
  ### <a name="remarks"></a>Comentarios  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma
|Miembro|Descripción|  
|------------|-----------------|
|[Box](#ctor)|Crea un `Box` que puede encapsular un valor del tipo especificado.|
|[operador cuadro&lt;const T&gt;^](#box-const-t)|Permite conversiones boxing de una clase de valor `const` `T` o de una clase `enum` `T` en `Box<T>`.|
|[operador cuadro&lt;const volatile T&gt;^](#box-const-volatile-t)|Permite conversiones boxing de una clase de valor `const volatile` `T` o de un tipo `enum` `T` en `Box<T>`. |
|[operador cuadro&lt;T&gt;^](#box-t)|Permite conversiones boxing de una clase de valor `T` en `Box<T>`.|
|[operador cuadro&lt;volatile T&gt;^](#box-volatile-t)|Permite conversiones boxing de una clase de valor `volatile` `T` o de un tipo `enum` `T` en `Box<T>`.|
|[Operador Box:: operator T](#t)|Permite conversiones boxing de una clase de valor `T` o de una clase `enum` `T` en `Box<T>`.| 
## <a name="ctor"></a> Constructor de Box
Crea un `Box` que puede encapsular un valor del tipo especificado. | |[ Propiedad Value](#value)| Devuelve el valor que se encapsula en la `Box` objeto. |  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
Box(T valueArg);  
```  
  
### <a name="parameters"></a>Parámetros  
 `valueArg`  
 El tipo de valor para realizar la conversión boxing, por ejemplo, `int`, `bool`, `float64`, `DateTime`.  
  

## <a name="box-const-t"></a> Box:: operator Box&lt;const T&gt;^ (operador)
Permite conversiones boxing de una clase de valor `const` `T` o de una clase `enum` `T` en `Box<T>`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 Cualquier valor de clase, struct de valor o tipo de enumeración. Incluye los tipos integrados en el [espacio de nombres predeterminado](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Un `Platform::Box<T>^` instancia que representa el valor original en la caja en una clase ref.  
  
## <a name="box-const-volatile-t"></a> Box:: operator Box&lt;const volatile T&gt;^ (operador)
Permite conversiones boxing de una clase de valor `const volatile` `T` o de un tipo `enum` `T` en `Box<T>`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
operator Box<const volatile T>^(const volatile T valueType);  
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el [espacio de nombres predeterminado](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Un `Platform::Box<T>^` instancia que representa el valor original en la caja en una clase ref.  
  
## <a name="box-t"></a> Box:: operator Box&lt;T&gt;^ (operador)
Permite conversiones boxing de una clase de valor `T` en `Box<T>`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el [espacio de nombres predeterminado](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Un `Platform::Box<T>^` instancia que representa el valor original en la caja en una clase ref.  
  
## <a name="box-volatile-t"></a> Box:: operator Box&lt;volatile T&gt;^ (operador)
Permite conversiones boxing de una clase de valor `volatile` `T` o de un tipo `enum` `T` en `Box<T>`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
operator Box<volatile T>^(volatile T valueType);  
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el [espacio de nombres predeterminado](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Un `Platform::Box<T>^` instancia que representa el valor original en la caja en una clase ref.  
  
## <a name="t"></a>  Operador Box:: operator T
Permite conversiones boxing de una clase de valor `T` o de una clase `enum` `T` en `Box<T>`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
operator Box<T>^(T valueType);  
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el [espacio de nombres predeterminado](../cppcx/default-namespace.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Un `Platform::Box<T>^` instancia que representa el valor original en la caja en una clase ref.  
  

## <a name="value"></a> Propiedad de Box
Devuelve el valor encapsulado en el objeto `Box`.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el valor al que se le ha aplicado la conversión boxing con el mismo tipo que tenía originalmente antes de que se le aplicara esa conversión.  
  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)   
 [Conversión boxing](../cppcx/boxing-c-cx.md)