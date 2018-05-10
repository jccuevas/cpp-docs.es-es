---
title: SafeInt::SafeInt | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c7154349105c1953ad314b7928e7be8385179c42
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt
Construye un objeto `SafeInt`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
SafeInt() throw  
  
SafeInt (  
   const T& i  
) throw ()  
  
SafeInt (  
   bool b  
) throw ()  
  
template <typename U>  
SafeInt (  
   const SafeInt <U, E>& u  
)  
  
I template <typename U>  
SafeInt (  
   const U& i  
)  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `i`  
 El valor para el nuevo `SafeInt` objeto. Debe ser un parámetro de tipo T o U, función del constructor.  
  
 [in] `b`  
 El valor booleano de la nueva `SafeInt` objeto.  
  
 [in] `u`  
 Un `SafeInt` de tipo U. El nuevo `SafeInt` objeto tendrá el mismo valor que `u`, pero serán de tipo T.  
  
 U  
 El tipo de datos almacenados en el `SafeInt`. Esto puede ser un valor booleano, un carácter o entero de tipo. Si es un tipo entero, puede ser con o sin signo y tener entre 8 y 64 bits.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información acerca de los tipos de plantilla `T` y `E`, consulte [SafeInt (clase)](../windows/safeint-class.md).  
  
 El parámetro de entrada para el constructor, `i` o `u`, debe ser un tipo entero, un carácter o un valor booleano. Si es otro tipo de parámetro, el `SafeInt` clase llamadas [static_assert](../cpp/static-assert.md) para indicar un parámetro de entrada no válido.  
  
 Los constructores que utilizan el tipo de plantilla `U` convertir automáticamente el parámetro de entrada para el tipo especificado por `T`. La `SafeInt` clase convierte los datos sin pérdida de datos. Indica al controlador de errores `E` si no se puede convertir los datos al tipo `T` sin pérdida de datos.  
  
 Si crea un `SafeInt` de un parámetro booleano, tiene que inicializar el valor inmediatamente. No se puede construir un `SafeInt` con el código `SafeInt<bool> sb;`. Esto generará un error de compilación.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** safeint.h  
  
 **Namespace:** msl::utilities  
  
## <a name="see-also"></a>Vea también  
 [Biblioteca SafeInt](../windows/safeint-library.md)   
 [SafeInt (clase)](../windows/safeint-class.md)   
 [SafeIntException (clase)](../windows/safeintexception-class.md)