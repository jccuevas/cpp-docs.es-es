---
title: pin_ptr (C++ / CLI) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
dev_langs:
- C++
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce63996cc2d93f4890f54c5edda318fca55f98aa
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/22/2018
---
# <a name="pinptr-ccli"></a>pin_ptr (C++/CLI)
Declara un *puntero anclado*, que se utiliza únicamente con common language runtime.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 (No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 (Esta característica de lenguaje no se admite en el tiempo de ejecución de Windows).  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 A *puntero anclado* es un puntero interior que impide que el objeto que señala al mover en el montón de recolección. Es decir, no se cambia el valor de un puntero anclado por common language runtime. Esto es necesario cuando se pasa la dirección de una clase administrada a una función no administrada para que la dirección no cambiará de forma inesperada durante la resolución de la llamada de función no administrada.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp  
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;  
```  
  
### <a name="parameters"></a>Parámetros  
 *cv_qualifier*  
 `const` o `volatile` calificadores. De forma predeterminada, es un puntero anclado `volatile`. Es redundante pero no es un error declarar un puntero anclado `volatile`.  
  
 *type*  
 Tipo de `initializer`.  
  
 *var*  
 El nombre de la `pin_ptr` variable.  
  
 *initializer*  
 Un miembro de un tipo de referencia, el elemento de una matriz administrada o cualquier otro objeto que se puede asignar a un puntero nativo.  
  
### <a name="remarks"></a>Comentarios  
 Un `pin_ptr` representa un supraconjunto de la funcionalidad de un puntero nativo. Por lo tanto, todo lo que puede asignarse a un puntero nativo también pueden asignarse a un `pin_ptr`. Se permite un puntero interior a realizar el mismo conjunto de operaciones como punteros nativos, incluida la comparación y la aritmética con punteros.  
  
 Puede anclar un objeto o subobjeto de una clase administrada, en cuyo caso el common language runtime no la moverá durante la recolección de elementos no utilizados. El uso principal de esto consiste en pasar un puntero a datos administrados como un parámetro real de una llamada de función no administrada. Durante un ciclo de recopilación, el tiempo de ejecución inspeccionará los metadatos creados para el puntero anclado y no la moverá el elemento al que apunta.  
  
 Al anclar un objeto ancla también sus campos de valor; es decir, los campos de tipo primitivo o valor type. Sin embargo, se declaran los campos por identificador de seguimiento (`%`) no se han fijado.  
  
 Anclar un subobjeto definido en un objeto administrado tiene el efecto de todo el objeto de anclaje.  
  
 Si el puntero anclado se reasigna para que apunte a un nuevo valor, la instancia anterior que señala no se considerará anclado.  
  
 Un objeto está fijo sólo mientras un `pin_ptr` hace referencia a ella. El objeto ya no está anclado cuando el puntero anclado sale del ámbito o se establece en [nullptr](../windows/nullptr-cpp-component-extensions.md). Después de la `pin_ptr` sale del ámbito, el objeto que se ancló se puede mover en el montón del recolector de elementos no utilizados. No se actualizará ningún puntero nativo que seguir señalando al objeto y anular que hacen referencia a uno de ellos podría provocar una excepción irrecuperable.  
  
 Si no hay punteros anclados apuntan al objeto (todos los punteros anclados fue fuera del ámbito, se vuelve a asignar para que señale a otros objetos o se asignaron [nullptr](../windows/nullptr-cpp-component-extensions.md)), se garantiza que el objeto no se pueden anclar.  
  
 Un puntero anclado puede apuntar a un identificador de referencia tipo de valor o el identificador del tipo de conversión boxing, miembro de un tipo administrado o un elemento de una matriz administrada. No puede apuntar a un tipo de referencia.  
  
 Tomar la dirección de un `pin_ptr` que apunta a un objeto nativo provoca un comportamiento indefinido.  
  
 Punteros anclados solo pueden declararse como variables locales no estáticas en la pila.  
  
 Punteros anclados no se puede usar como:  
  
-   parámetros de la función  
  
-   el tipo de valor devuelto de una función  
  
-   un miembro de una clase  
  
-   el tipo de destino de una conversión.  
  
 `pin_ptr` en el `cli` espacio de nombres. Para obtener más información, consulte [plataforma, predeterminado y cli espacios de nombres](../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).  
  
 Para obtener más información acerca de los punteros interiores, consulte [interior_ptr (C++ / CLI)](../windows/interior-ptr-cpp-cli.md).  
  
 Para obtener más información acerca de fijar punteros, vea [Cómo: anclar punteros y matrices](../windows/how-to-pin-pointers-and-arrays.md) y [Cómo: declarar punteros anclados y tipos de valor](../windows/how-to-declare-pinning-pointers-and-value-types.md).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
 **Ejemplo**  
  
 En el ejemplo siguiente se utiliza `pin_ptr` para restringir la posición del primer elemento de una matriz.  
  
```  
// pin_ptr_1.cpp  
// compile with: /clr   
using namespace System;  
#define SIZE 10  
  
#pragma unmanaged  
// native function that initializes an array  
void native_function(int* p) {  
   for(int i = 0 ; i < 10 ; i++)  
    p[i] = i;  
}  
#pragma managed  
  
public ref class A {  
private:  
   array<int>^ arr;   // CLR integer array  
  
public:  
   A() {  
      arr = gcnew array<int>(SIZE);  
   }  
  
   void load() {  
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr  
   int* np = p;   // pointer to the first element in arr  
   native_function(np);   // pass pointer to native function  
   }  
  
   int sum() {  
      int total = 0;  
      for (int i = 0 ; i < SIZE ; i++)  
         total += arr[i];  
      return total;  
   }  
};  
  
int main() {  
   A^ a = gcnew A;  
   a->load();   // initialize managed array using the native function  
   Console::WriteLine(a->sum());  
}  
```  
  
 **Salida**  
  
```Output  
45  
```  
  
 **Ejemplo**  
  
 En el ejemplo siguiente se muestra que se puede convertir un puntero interior a un puntero anclado y que el tipo de devolución de la dirección del operador (`&`) es un puntero interior si el operando está en el montón administrado.  
  
```  
// pin_ptr_2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct G {  
   G() : i(1) {}  
   int i;  
};  
  
ref struct H {  
   H() : j(2) {}  
   int j;  
};  
  
int main() {  
   G ^ g = gcnew G;   // g is a whole reference object pointer  
   H ^ h = gcnew H;  
  
   interior_ptr<int> l = &(g->i);   // l is interior pointer  
  
   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer  
  
   k = l;   // ok  
   Console::WriteLine(*k);  
};  
```  
  
 **Salida**  
  
```Output  
1  
```  
  
 **Ejemplo**  
  
 En el ejemplo siguiente se muestra que se puede convertir un puntero anclado a otro tipo.  
  
```  
// pin_ptr_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref class ManagedType {  
public:  
   int i;  
};  
  
int main() {  
   ManagedType ^mt = gcnew ManagedType;  
   pin_ptr<int> pt = &mt->i;  
   *pt = 8;  
   Console::WriteLine(mt->i);  
  
   char *pc = ( char* ) pt;  
   *pc = 255;  
   Console::WriteLine(mt->i);  
}  
```  
  
 **Salida**  
  
```Output  
8  
255  
```