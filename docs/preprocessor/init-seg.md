---
title: "init_seg | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc-pragma.init_seg"
  - "init_seg_CPP"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "inicialización de segmentos de datos [C++]"
  - "init_seg (pragma)"
  - "pragma (directivas), init_seg"
ms.assetid: 40a5898a-5c85-4aa9-8d73-3d967eb13610
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# init_seg
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de C\+\+**  
  
 Especifica una palabra clave o una sección de código que afecta al orden en que se ejecuta el código de inicio.  
  
## Sintaxis  
  
```  
  
#pragma init_seg({ compiler | lib | user | "section-name" [, func-name]} )  
```  
  
## Comentarios  
 Los términos *segmento* y *sección* son sinónimos en este tema.  
  
 Dado que la inicialización de objetos estáticos globales puede implicar la ejecución de código, debe especificar una palabra clave que defina cuándo deben crearse los objetos.  Es especialmente importante usar la instrucción pragma **init\_seg** en las bibliotecas de vínculos dinámicos \(DLL\) o en las bibliotecas que requieran inicialización.  
  
 Las opciones de la instrucción pragma **init\_seg** son las siguientes:  
  
 **compiler**  
 Reservada para la inicialización de la biblioteca en tiempo de ejecución de C de Microsoft.  Los objetos de este grupo se construyen en primer lugar.  
  
 **lib**  
 Disponible para las inicializaciones de los proveedores de bibliotecas de clases de terceros.  Los objetos de este grupo se construyen después de los marcados como **compiler** pero antes de los demás.  
  
 **user**  
 Disponible para cualquier usuario.  Los objetos de este grupo se construyen en último lugar.  
  
 *section\-name*  
 Permite la especificación explícita de la sección de inicialización.  Los objetos en un elemento *section\-name* definido por el usuario no se construyen implícitamente; por el contrario, sus direcciones se colocan en la sección designada por el elemento *section\-name*.  
  
 El nombre de sección que asigne contendrá punteros a funciones auxiliares que construirán los objetos globales declarados en ese módulo después de la instrucción pragma.  
  
 Para obtener una lista de los nombres que no debe utilizar cuando cree una sección, vea [\/SECTION](../build/reference/section-specify-section-attributes.md).  
  
 *func\-name*  
 Especifica la función que se va a llamar en lugar de `atexit` cuando termine el programa.  Esta función auxiliar también llama a [atexit](../c-runtime-library/reference/atexit.md) con un puntero al destructor del objeto global.  Si especifica un identificador de función en la instrucción pragma con el formato,  
  
```  
int __cdecl myexit (void (__cdecl *pf)(void))  
```  
  
 se llamará a su función en lugar de a `atexit` de la biblioteca en tiempo de ejecución de C.  Esto permite crear una lista de los destructores que deberá llamar cuando esté preparado para destruir los objetos.  
  
 Si necesita diferir la inicialización \(por ejemplo, en una DLL\), puede elegir especificar el nombre de sección explícitamente.  En tal caso, deberá llamar a los constructores de cada objeto estático.  
  
 No se incluyen comillas alrededor del identificador del sustituto de `atexit`.  
  
 Sus objetos se incluirán igualmente en las secciones definidas por las otras instrucciones pragma XXX\_seg.  
  
 El motor de tiempo de ejecución de C no inicializará automáticamente los objetos que se declaren en el módulo.  Tendrá que inicializarlos usted mismo.  
  
 De forma predeterminada, las secciones `init_seg` son de solo lectura.  Si el nombre de sección es .CRT, el compilador cambiará silenciosamente el atributo a de solo lectura, aunque esté marcado como de lectura o escritura.  
  
 No puede especificar **init\_seg** más de una vez en una unidad de traducción.  
  
 Aunque el objeto no tenga un constructor definido por el usuario, un constructor no definido explícitamente en el código, el compilador puede generar uno \(por ejemplo, para enlazar punteros de tabla v\).  Por consiguiente, el código tendrá que llamar al constructor generado por el compilador.  
  
## Ejemplo  
  
```  
// pragma_directive_init_seg.cpp  
#include <stdio.h>  
#pragma warning(disable : 4075)  
  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors we need to call  
PF pfx[200];    // pointers to destructors.  
  
int myexit (PF pf) {  
   pfx[cxpf++] = pf;  
   return 0;  
}  
  
struct A {  
   A() { puts("A()"); }  
   ~A() { puts("~A()"); }  
};  
  
// ctor & dtor called by CRT startup code   
// because this is before the pragma init_seg  
A aaaa;   
  
// The order here is important.  
// Section names must be 8 characters or less.  
// The sections with the same name before the $  
// are merged into one section. The order that  
// they are merged is determined by sorting  
// the characters after the $.  
// InitSegStart and InitSegEnd are used to set  
// boundaries so we can find the real functions  
// that we need to call for initialization.  
  
#pragma section(".mine$a", read)  
__declspec(allocate(".mine$a")) const PF InitSegStart = (PF)1;  
  
#pragma section(".mine$z",read)  
__declspec(allocate(".mine$z")) const PF InitSegEnd = (PF)1;  
  
// The comparison for 0 is important.  
// For now, each section is 256 bytes. When they  
// are merged, they are padded with zeros. You  
// can't depend on the section being 256 bytes, but  
// you can depend on it being padded with zeros.  
  
void InitializeObjects () {  
   const PF *x = &InitSegStart;  
   for (++x ; x < &InitSegEnd ; ++x)  
      if (*x) (*x)();  
}  
  
void DestroyObjects () {  
   while (cxpf>0) {  
      --cxpf;  
      (pfx[cxpf])();  
   }  
}  
  
// by default, goes into a read only section  
#pragma init_seg(".mine$m", myexit)  
  
A bbbb;   
A cccc;  
  
int main () {  
   InitializeObjects();  
   DestroyObjects();  
}  
```  
  
  **A\(\)**  
**A\(\)**  
**A\(\)**  
**~A\(\)**  
**~A\(\)**  
**~A\(\)**   
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)