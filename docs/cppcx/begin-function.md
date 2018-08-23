---
title: Begin (función) | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4954e98c1e6f1da30e321aad0c0e37cc5c1ab994
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606537"
---
# <a name="begin-function"></a>begin (Función)
Devuelve un iterador que apunta al principio de una colección a la que se tiene acceso con el parámetro de interfaz especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template <typename T>   
    ::Platform::Collections::VectorIterator<T>   
    begin(  
          IVector<T>^ v         );  
  
template <typename T>   
    ::Platform::Collections::VectorViewIterator<T>   
    begin(  
          IVectorView<T>^ v  
         );   
  
template <typename T>   
    ::Platform::Collections::InputIterator<T>   
    begin(  
          IIterable<T>^ i         );  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un parámetro de tipo de plantilla.  
  
 `v`  
 Una colección de Vector\<T > o VectorView\<T > objetos que se accede mediante un IVector\<T > o IVectorView\<T > interfaz.  
  
 `i`  
 Una colección de objetos arbitrarios de Windows en tiempo de ejecución que se accede mediante un IIterable\<T > interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que apunta al principio de la colección.  
  
### <a name="remarks"></a>Comentarios  
 Las dos primeras funciones de plantilla devuelven iteradores y la tercera función de plantilla devuelve un iterador de entrada.  
  
 El objeto VectorIterator objeto devuelto por begin es un iterador de proxy que almacena elementos de tipo VectorProxy\<T >. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Vea también  
 [Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)