---
title: Writeonlyarray (clase) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WriteOnlyArray::begin
- VCCORLIB/Platform::WriteOnlyArray::Data
- VCCORLIB/Platform::WriteOnlyArray::end
- VCCORLIB/Platform::WriteOnlyArray::FastPass
- VCCORLIB/Platform::WriteOnlyArray::Length
- VCCORLIB/Platform::WriteOnlyArray::set
dev_langs:
- C++
helpviewer_keywords:
- Platform::WriteOnlyArray Class
ms.assetid: 92d7dd56-ec58-4b8c-88ba-9c903668b687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44beeca9b860e2010b092739d8c39044ad0bb5b1
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680930"
---
# <a name="platformwriteonlyarray-class"></a>Platform::WriteOnlyArray (Clase)
Representa una matriz unidimensional que se utiliza como parámetro de entrada cuando el llamador pasa una matriz para el método que se va a rellenar.  
  
 Esta clase ref se declara como privada en vccorlib.h; por consiguiente, no se emite en los metadatos y solo se puede usar desde C++. Esta clase está diseñada únicamente para su uso como un parámetro de entrada que recibe una matriz que el llamador ha asignado. No se puede crear desde el código de usuario. Permite a un método de C++ escribir directamente en dicha matriz, patrón que se conoce como *FillArray* . Para obtener más información, consulte [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
private ref class WriteOnlyArray<T, 1>  
```  
  
### <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
 Estos métodos tienen accesibilidad interna, es decir, solo están accesibles desde la aplicación o componente de C++.  
  
|nombre|Descripción|  
|----------|-----------------|  

|[Writeonlyarray](#begin)| Un iterador que apunta al primer elemento de la matriz. |  
|[Writeonlyarray](#data)| Un puntero al búfer de datos. |  
|[Writeonlyarray](#end)| Un iterador que apunta a uno más allá del último elemento de la matriz. |  
|[Fastpass](#fastpass)| Indica si la matriz puede usar el mecanismo FastPass, que es una optimización realizada de forma transparente por el sistema. No utilices esto en el código |  
|[Writeonlyarray](#length)| Devuelve el número de elementos de la matriz. |  
|[Writeonlyarray](#set)| Establece el elemento especificado en el valor especificado. |  

  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `WriteOnlyArray`  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
 **Metadatos:** Platform.winmd  
  
 **Espacio de nombres:** Plataforma  

## <a name="begin"></a>  WriteOnlyArray::begin (Método)
Devuelve un puntero al primer elemento de la matriz.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
T* begin() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero al primer elemento de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Este iterador se puede usar con los algoritmos de STL como `std::sort` para operar en elementos de la matriz.  
  


## <a name="data"></a>  WriteOnlyArray::Data (Propiedad)
Puntero al búfer de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
property T* Data{  
   T* get() const;  
}  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Puntero a los bytes sin formato de la matriz.  
  


## <a name="end"></a>  WriteOnlyArray::end (Método)
Devuelve un puntero a uno más allá del último elemento de la matriz.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
T* end() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador de puntero a uno más allá del último elemento de la matriz.  
  
### <a name="remarks"></a>Comentarios  
 Este iterador se puede usar con los algoritmos de STL para realizar operaciones como `std::sort` en elementos de la matriz.  
  


## <a name="fastpass"></a>  WriteOnlyArray::FastPass (Propiedad)
Indica si se puede realizar la optimización interna de FastPass. No se ha diseñado para el uso en el código del usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
property bool FastPass{  
   bool get() const;  
}  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Valor booleano que indica si la matriz es FastPass.  
  


## <a name="get"></a>  Writeonlyarray (método)
Devuelve el elemento que se encuentra en el índice especificado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
T& get(  
   unsigned int indexArg) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `indexArg`  
  
### <a name="return-value"></a>Valor devuelto  
  


## <a name="length"></a>  WriteOnlyArray::Length (Propiedad)
Devuelve el número de elementos de la matriz asignada por el llamador.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
property unsigned int Length{  
   unsigned int get() const;  
}  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Número de elementos de la matriz.  
  


## <a name="set"></a>  WriteOnlyArray::set (Función)
Establece el valor especificado en el índice especificado de la matriz.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
T& set(  
   unsigned int indexArg,  
   T valueArg);  
```  
  
### <a name="parameters"></a>Parámetros  
 `indexArg`  
 Índice del elemento que se va a establecer.  
  
 `valueArg`  
 El valor que se va a establecer en `indexArg`.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia al elemento que se acaba de establecer.  
  

  
### <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de cómo interpretar el valor HRESULT, vea [estructura de códigos de Error COM](/windows/desktop/com/structure-of-com-error-codes).  
  
  
## <a name="see-also"></a>Vea también  
 [Plataforma Namespace](platform-namespace-c-cx.md)   
 [Crear componentes de Windows en tiempo de ejecución en C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)