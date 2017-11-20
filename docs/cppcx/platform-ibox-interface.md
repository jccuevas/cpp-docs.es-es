---
title: Ibox (interfaz) | Documentos de Microsoft
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Namespace not found::Platform
- VCCORLIB/Namespace not found::Platform::Value
dev_langs: C++
ms.assetid: 774df45d-f8a7-45a3-ae24-eecc3c681040
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: e3cbeed5893e6a757ca5ac3c17e596d3a1526e46
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="platformibox-interface"></a>Platform::IBox (Interfaz)
La interfaz [Platform::IBox](../cppcx/platform-ibox-interface.md) es el nombre de C++ para la interfaz `Windows::Foundation::IReference` .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
template <typename T>  
interface class IBox  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo del valor al que se le ha aplicado la conversión boxing.  
  
### <a name="remarks"></a>Comentarios  
 La interfaz `IBox<T>` se usa principalmente para representar tipos de valor que aceptan valores NULL, tal y como se describe en [Clases y structs de valor (C++/CX)](../cppcx/value-classes-and-structs-c-cx.md). La interfaz también se usa internamente para aplicar la conversión boxing a tipos de valor que se pasan a métodos de C++ que toman parámetros de tipo `Object^`. Puedes declarar explícitamente un parámetro de entrada como `IBox<SomeValueType>`. Para obtener un ejemplo, vea [conversión Boxing](../cppcx/boxing-c-cx.md).  
  
### <a name="requirements"></a>Requisitos  
  
### <a name="members"></a>Miembros  
 La interfaz `Platform::IBox` hereda de la interfaz [Platform::IValueType](../cppcx/platform-ivaluetype-interface.md) . `IBox` tiene estos miembros:  
  
 **Propiedades**  
  
|Método|Descripción|  
|------------|-----------------|  
|[Valor](#value)|Devuelve el valor al que se le ha aplicado la conversión unboxing y que se almacenó previamente en esta instancia de `IBox` .|  

## <a name="value"></a>Propiedad Ibox
Devuelve el valor que se almacenó originalmente en este objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
property T Value {T get();}  
```  
  
### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo del valor al que se le ha aplicado la conversión boxing.  
  
### <a name="property-valuereturn-value"></a>Valor de propiedad y valor devuelto  
 Devuelve el valor que se almacenó originalmente en este objeto.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo, vea [conversión Boxing](../cppcx/boxing-c-cx.md).  
  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)