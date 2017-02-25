---
title: "selectany | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "selectany_cpp"
  - "selectany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], selectany"
  - "selectany __declspec (palabra clave)"
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# selectany
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Indica al compilador que el elemento de datos globales declarado \(variable u objeto\) es un COMDAT de selección \(una función empaquetada\).  
  
## Sintaxis  
  
```  
  
__declspec( selectany ) declarator  
```  
  
## Comentarios  
 En tiempo de vinculación, si se ven varias definiciones de un COMDAT, el vinculador selecciona una y descarta el resto.  Si se selecciona la opción de vinculador [\/OPT:REF](../build/reference/opt-optimizations.md) \(Optimizaciones\), se producirá la eliminación de COMDAT para quitar todos los elementos de datos no referenciados de la salida del vinculador.  
  
 Los constructores y la asignación mediante una función global o métodos estáticos en la declaración no crean una referencia y no impedirán la eliminación de \/OPT:REF.  No se debe depender de los efectos secundarios de ese código si no existen otras referencias a los datos.  
  
 Para los objetos globales inicializados dinámicamente, `selectany` también descartará un código de inicialización de objeto no referenciado.  
  
 Un elemento de datos globales se puede inicializar normalmente solo una vez en un proyecto EXE o DLL.  `selectany` se puede utilizar en la inicialización de datos globales definidos por los encabezados cuando el mismo encabezado aparece en más de un archivo de código fuente.  `selectany` está disponible en los compiladores de C y C\+\+.  
  
> [!NOTE]
>  `selectany` solo se puede aplicar a la inicialización real de elementos de datos globales externamente visibles.  
  
## Ejemplo  
 En este código se muestra cómo usar el atributo `selectany`.  
  
```  
//Correct - x1 is initialized and externally visible   
__declspec(selectany) int x1=1;  
  
//Incorrect - const is by default static in C++, so   
//x2 is not visible externally (This is OK in C, since  
//const is not by default static in C)  
const __declspec(selectany) int x2 =2;  
  
//Correct - x3 is extern const, so externally visible  
extern const __declspec(selectany) int x3=3;  
  
//Correct - x4 is extern const, so it is externally visible  
extern const int x4;  
const __declspec(selectany) int x4=4;  
  
//Incorrect - __declspec(selectany) is applied to the uninitialized  
//declaration of x5  
extern __declspec(selectany) int x5;  
  
// OK: dynamic initialization of global object  
class X {  
public:  
X(int i){i++;};  
int i;  
};  
  
__declspec(selectany) X x(1);  
```  
  
## Ejemplo  
 En este código se muestra cómo utilizar el atributo `selectany` para garantizar el plegamiento de COMDAT de datos cuando también se utiliza la opción del vinculador [\/OPT: ICF](../build/reference/opt-optimizations.md).  Observe que los datos se deben marcar con `selectany` y colocar en una sección **const** \(de solo lectura\).  Debe especificar explícitamente la sección de solo lectura.  
  
```  
// selectany2.cpp  
// in the following lines, const marks the variables as read only  
__declspec(selectany) extern const int ix = 5;  
__declspec(selectany) extern const int jx = 5;  
int main() {  
   int ij;  
   ij = ix + jx;  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)