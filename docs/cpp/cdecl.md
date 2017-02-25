---
title: "__cdecl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__cdecl"
  - "__cdecl_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__cdecl (palabra clave) [C++]"
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
caps.latest.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# __cdecl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 `__cdecl` es la convención de llamada predeterminada de los programas C y C\+\+.  Como el llamador limpia la pila, puede realizar funciones **vararg**.  La convención de llamada `__cdecl` crea archivos ejecutables mayores que [\_\_stdcall](../cpp/stdcall.md), porque requiere que cada llamada a función incluya código de limpieza de la pila.  En la lista siguiente se muestra la implementación de esta convención de llamada.  
  
|Elemento|Implementación|  
|--------------|--------------------|  
|Orden de paso de argumento|De derecha a izquierda.|  
|Responsabilidad de mantenimiento de pila|Al llamar a la función, se extraen los argumentos de la pila.|  
|Convención de creación de nombres representativos|El carácter de subrayado \(\_\) precede a los nombres, excepto al exportar funciones \_\_cdecl que usan la vinculación de C.|  
|Convención de traducción de mayúsculas y minúsculas|No se lleva a cabo una traducción de mayúsculas y minúsculas.|  
  
> [!NOTE]
>  Para obtener información relacionada, vea [Nombres representativos](../build/reference/decorated-names.md).  
  
 Coloque el modificador `__cdecl` delante de una variable o nombre de función.  Como las convenciones de llamada y nomenclatura de C son el valor predeterminado, la única vez que se debe usar `__cdecl` en código para x86 es cuando se haya especificado la opción del compilador **\/Gv** \(vectorcall\), **\/Gz** \(stdcall\) o **\/Gr** \(fastcall\).  La opción del compilador [\/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) fuerza la convención de llamada `__cdecl`.  
  
 En los procesadores ARM y x64, se acepta el uso de `__cdecl`, pero el compilador lo omite normalmente.  Por convención en ARM y x64, los argumentos se pasan en registros siempre que es posible y los argumentos subsiguientes se pasan en la pila.  En código x64, use `__cdecl` para invalidar la opción del compilador **\/Gv** y usar la convención de llamada predeterminada de x64.  
  
 En el caso de funciones de clase no estáticas, si la función se define fuera de línea, no es necesario especificar el modificador de convención de llamada en la definición fuera de línea.  Es decir, para los métodos miembro no estáticos de clase, en el momento de la definición se supone la convención de llamada especificada durante la declaración.  Dada esta definición de clase:  
  
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
  
## Ejemplo  
 En el ejemplo siguiente, se le indica al compilador que utilice nombres y convenciones de llamada de C para la función `system`.  
  
```cpp  
// Example of the __cdecl keyword on function  
int __cdecl system(const char *);  
// Example of the __cdecl keyword on function pointer  
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);  
```  
  
## Vea también  
 [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)