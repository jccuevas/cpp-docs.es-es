---
title: __cdecl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __cdecl_cpp
dev_langs:
- C++
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d07c34c11037132b9f9695ec889bb681c7f43951
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="cdecl"></a>__cdecl
**Específicos de Microsoft**  
  
 `__cdecl` es la convención de llamada predeterminada de los programas C y C++. Dado que el llamador limpia la pila, puede realizar **vararg** funciones. El `__cdecl` convención de llamada crea archivos ejecutables mayores que [__stdcall](../cpp/stdcall.md), porque requiere que cada llamada a función incluya código de limpieza de la pila. En la lista siguiente se muestra la implementación de esta convención de llamada.  
  
|Elemento|Implementación|  
|-------------|--------------------|  
|Orden de paso de argumento|De derecha a izquierda.|  
|Responsabilidad de mantenimiento de pila|Al llamar a la función, se extraen los argumentos de la pila.|  
|Convención de creación de nombres representativos|Carácter de subrayado (_) precede a los nombres, excepto cuando \__cdecl funciones que utilicen la vinculación de C se exportan.|  
|Convención de traducción de mayúsculas y minúsculas|No se lleva a cabo una traducción de mayúsculas y minúsculas.|  
  
> [!NOTE]
>  Para obtener información relacionada, consulte [nombres representativos](../build/reference/decorated-names.md).  
  
 Coloque el modificador `__cdecl` delante de una variable o nombre de función. Dado que las convenciones de llamada y nomenclatura de C son el valor predeterminado, la única vez debe usar `__cdecl` en x86 código es cuando se haya especificado la **GV** (vectorcall), **/Gz** (stdcall) o  **/ GR** opción del compilador (fastcall). El [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) compilador opción fuerza el `__cdecl` convención de llamada.  
  
 En los procesadores ARM y x64, se acepta el uso de `__cdecl`, pero el compilador lo omite normalmente. Por convención en ARM y x64, los argumentos se pasan en registros siempre que es posible y los argumentos subsiguientes se pasan en la pila. En x64 de código, use `__cdecl` para invalidar la **GV** opción del compilador y usar la convención llamada predeterminada x64.  
  
 En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea. Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración. Dada esta definición de clase:  
  
```cpp  
struct CMyClass {  
   void __cdecl mymethod();  
};  
```  
  
 esto:  
  
```cpp  
void CMyClass::mymethod() { return; }  
```  
  
 equivale a esto:  
  
```cpp  
void __cdecl CMyClass::mymethod() { return; }  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, se le indica al compilador que utilice nombres y convenciones de llamada de C para la función `system`.  
  
```cpp  
// Example of the __cdecl keyword on function  
int __cdecl system(const char *);  
// Example of the __cdecl keyword on function pointer  
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## <a name="see-also"></a>Vea también  
 [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)   
 [Palabras clave](../cpp/keywords-cpp.md)