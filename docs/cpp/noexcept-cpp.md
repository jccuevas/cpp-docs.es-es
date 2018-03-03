---
title: noexcept (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 01/12/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- noexcept_cpp
dev_langs:
- C++
ms.assetid: df24edb9-c6a6-4e37-9914-fd5c0c3716a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9b78c19cb156312b6087b75e50c0e0fa28a00246
ms.sourcegitcommit: c2e990450ccd528d85b2783fbc63042612987cfd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2018
---
# <a name="noexcept-c"></a>noexcept (C++)
**C ++ 11:** especifica si una función puede producir excepciones.  
  
## <a name="syntax"></a>Sintaxis  
  
> *noexcept-expression*:  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept**  
> &nbsp;&nbsp;&nbsp;&nbsp;**noexcept(** *constant-expression* **)**  
  
### <a name="parameters"></a>Parámetros  
 *constant-expression*  
 Una expresión constante de tipo `bool` que indica si el conjunto de posibles tipos de excepción está vacío. La versión incondicional es equivalente a `noexcept(true)`.  
  
## <a name="remarks"></a>Comentarios  
 A *noexcept expresión* es un tipo de *una especificación de excepción*, un sufijo a una declaración de función que representa un conjunto de tipos que pueden ser elegidas por un controlador de excepciones para cualquier excepción que se cierra un función. Operador condicional unario `noexcept(` *expresiónConstante* `)` donde *expresiónConstante* yeilds `true`y su sinónimo incondicional `noexcept`, Especifica que el conjunto de posibles tipos de excepciones que puede salir de una función está vacío. Es decir, la función nunca inicia una excepción y no permite nunca una excepción se propague fuera de su ámbito. El operador `noexcept(` *expresiónConstante* `)` donde *expresiónConstante* yeilds `false`, o la ausencia de una especificación de excepción (que no sea para un función destructor o desasignación), indica que el conjunto de posibles excepciones que puede salir de la función es el conjunto de todos los tipos.  
 
 Marque una función como `noexcept` sólo si todas las funciones que llama, directa o indirectamente, también son `noexcept` o `const`. El compilador no comprueba necesariamente cada ruta de acceso de código para las excepciones que podrían ascender hasta una `noexcept` función. Si una excepción salir del ámbito exterior de una función marcada `noexcept`, [std:: Terminate](../standard-library/exception-functions.md#terminate) se invoca inmediatamente, y no hay ninguna garantía de que se invocará los destructores de todos los objetos en el ámbito. Use `noexcept` en lugar del especificador de excepción dinámica `throw()`, que ahora está en desuso en el estándar. Le recomendamos que aplique `noexcept` a cualquier función que nunca se permite una excepción se propague hacia arriba de la pila de llamadas. Cuando se declara una función `noexcept`, permite al compilador que genere un código más eficaz en varios contextos distintos. Para obtener más información, consulte [especificaciones de excepción](exception-specifications-throw-cpp.md).   
  
## <a name="example"></a>Ejemplo  
Una función de plantilla que copia su argumento podría declararse `noexcept` a condición de que el objeto que se está copiando sea un tipo de datos antiguos sin formato (POD). Este tipo de función podría declararse de este modo:  
  
```cpp  
#include <type_traits>  
  
template <typename T>  
T copy_object(const T& obj) noexcept(std::is_pod<T>)  
{  
   // ...   
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones de C++](cpp-exception-handling.md) [especificaciones de excepciones (throw, noexcept)](exception-specifications-throw-cpp.md)