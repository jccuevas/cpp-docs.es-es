---
title: __cdecl | Microsoft Docs
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
ms.openlocfilehash: c0a9e4db3e1fcbd24358d6dedd2d4ada80672c2a
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406551"
---
# <a name="cdecl"></a>__cdecl
**Específicos de Microsoft**  
  
 **__cdecl** es el valor predeterminado convención de llamada para los programas C y C++. Dado que el llamador limpia la pila, puede realizar `vararg` funciones. El **__cdecl** convención de llamada crea archivos ejecutables mayores que [__stdcall](../cpp/stdcall.md), porque requiere que cada llamada a función incluya código de limpieza de la pila. En la lista siguiente se muestra la implementación de esta convención de llamada.  
  
|Elemento|Implementación|  
|-------------|--------------------|  
|Orden de paso de argumento|De derecha a izquierda.|  
|Responsabilidad de mantenimiento de pila|Al llamar a la función, se extraen los argumentos de la pila.|  
|Convención de creación de nombres representativos|Carácter de subrayado (_) precede a los nombres, excepto cuando \__cdecl funciones que utilice vinculación C se exportan.|  
|Convención de traducción de mayúsculas y minúsculas|No se lleva a cabo una traducción de mayúsculas y minúsculas.|  
  
> [!NOTE]
>  Para obtener información relacionada, consulte [nombres representativos](../build/reference/decorated-names.md).  
  
 Colocar el **__cdecl** modificador antes de una variable o un nombre de función. Dado que los nombres y las convenciones de llamada de C son el valor predeterminado, la única vez que debe usar **__cdecl** en x86 es código cuando haya especificado el `/Gv` (vectorcall), `/Gz` (stdcall) o `/Gr` (fastcall) opción del compilador. El [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) compilador opción fuerza el **__cdecl** convención de llamada.  
  
 En ARM y x64 procesadores, **__cdecl** es aceptado pero el compilador omite normalmente. Por convención en ARM y x64, los argumentos se pasan en registros siempre que es posible y los argumentos subsiguientes se pasan en la pila. En x64 de código, use **__cdecl** para invalidar el **GV** opción del compilador y use la convención de llamada predeterminada x64.  
  
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