---
title: '&lt;exception&gt; (Typedefs) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: f55867484f781f91dfb447d384223fbdeb370592
ms.lasthandoff: 02/24/2017

---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt; (Typedefs)
||||  
|-|-|-|  
|[exception_ptr](#exception_ptr)|[terminate_handler](#terminate_handler)|[unexpected_handler](#unexpected_handler)|  
  
##  <a name="exception_ptr"></a>  exception_ptr  
 Tipo que describe un puntero a una excepción.  
  
```cpp  
typedef unspecified exception_ptr;
```  
  
### <a name="remarks"></a>Comentarios  
 Clase interna sin especificar que se utiliza para implementar el tipo `exception_ptr`.  
  
 Utilice un objeto `exception_ptr` para hacer referencia a la excepción actual o a una instancia de una excepción especificada por el usuario. En la implementación de Microsoft, una excepción se representa mediante una estructura [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082). Cada objeto `exception_ptr` incluye un campo de referencia de excepción que apunta a una copia de la estructura `EXCEPTION_RECORD` que representa la excepción.  
  
 Cuando se declara una variable `exception_ptr`, la variable no está asociada a ninguna excepción. Es decir, su campo de referencia de excepción es NULL. Este tipo de objeto `exception_ptr` se denomina *exception_ptr null*.  
  
 Utilice la función `current_exception` o `make_exception_ptr` para asignar una excepción a un objeto `exception_ptr`. Cuando se asigna una excepción a una variable `exception_ptr`, el campo de referencia de excepción de la variable apunta a una copia de la excepción. Si no hay memoria suficiente para copiar la excepción, el campo de referencia de excepción apunta a una copia de una excepción [std::bad_alloc](../standard-library/bad-alloc-class.md). Si la función `current_exception` o `make_exception_ptr` no puede copiar la excepción por cualquier otro motivo, llama a la función de CRT **terminate** para salir del proceso actual.  
  
 A pesar de su nombre, un objeto `exception_ptr` no es en sí mismo un puntero. No obedece a la semántica de los punteros y no se puede usar con los operadores de acceso (`->`) o de direccionamiento indirecto (*) de miembro de puntero. El objeto `exception_ptr` no tiene ningún miembro de datos ni ninguna función miembro de tipo público.  
  
 **Comparaciones:**  
  
 Se pueden usar los operadores de igualdad (`==`) y desigualdad (`!=`) para comparar dos objetos `exception_ptr`. Los operadores no comparan el valor binario (patrón de bits) de las estructuras `EXCEPTION_RECORD` que representan las excepciones. En su lugar, los operadores comparan las indicaciones del campo de referencia de excepción de los objetos `exception_ptr`. Por tanto, un `exception_ptr` NULL y el valor NULL se consideran iguales.  
  
##  <a name="terminate_handler"></a>  terminate_handler  
 El tipo describe un puntero a una función que se puede usar como `terminate_handler`.  
  
```
typedef void (*terminate_handler)();
```  
  
### <a name="remarks"></a>Comentarios  
 El tipo describe un puntero a una función que se puede usar como controlador de finalización.  
  
### <a name="example"></a>Ejemplo  
  Vea [set_terminate](../standard-library/exception-functions.md#set_terminate) para obtener un ejemplo de uso de `terminate_handler`.  
  
##  <a name="unexpected_handler"></a>  unexpected_handler  
 El tipo describe un puntero a una función que se puede usar como un `unexpected_handler`.  
  
```
typedef void (*unexpected_handler)();
```  
  
### <a name="example"></a>Ejemplo  
  Vea [set_unexpected](../standard-library/exception-functions.md#set_unexpected) para obtener un ejemplo de uso de `unexpected_handler`.  
  
## <a name="see-also"></a>Vea también  
 [\<exception>](../standard-library/exception.md)




