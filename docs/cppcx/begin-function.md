---
title: "Begin (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d47244e6428979f5319c9ee02f252ef3e559f7ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
 Una colección de Vector\<T > o VectorView\<T > objetos que se tiene acceso mediante un IVector\<T > o IVectorView\<T > interfaz.  
  
 `i`  
 Una colección de objetos en tiempo de ejecución de Windows arbitrarios que se tiene acceso mediante un IIterable\<T > interfaz.  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que apunta al principio de la colección.  
  
### <a name="remarks"></a>Comentarios  
 Las dos primeras funciones de plantilla devuelven iteradores y la tercera función de plantilla devuelve un iterador de entrada.  
  
 El objeto VectorIterator devuelto por begin es un iterador de proxy que almacena elementos de tipo VectorProxy\<T >. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Vea también  
 [Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)