---
title: "const y volatile (Punteros) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const (palabra clave) [C++], punteros volátiles"
  - "punteros, y const"
  - "punteros, y volatile"
  - "volatile (palabra clave) [C++], y punteros"
ms.assetid: 0c92dc6c-400e-4342-b345-63ddfe649d7e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# const y volatile (Punteros)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las palabras clave de [const](../cpp/const-cpp.md) y [volatile](../cpp/volatile-cpp.md) cambian el modo en que se tratan los punteros.  La palabra clave **const** especifica que el puntero no se puede modificar después de la inicialización; desde ese momento, el puntero se protege de cualquier modificación.  
  
 La palabra clave `volatile` especifica que el valor asociado al nombre que va a continuación se puede modificar con acciones que no sean las de la aplicación del usuario.  Por consiguiente, la palabra clave `volatile` es útil para declarar objetos en memoria compartida a los que puedan obtener acceso varios procesos o áreas de datos globales utilizados para la comunicación con rutinas de servicio de interrupción.  
  
 Si un nombre se declara como `volatile`, el compilador recarga el valor de la memoria cada vez que el programa tiene acceso al mismo.  Esto reduce considerablemente las posibles optimizaciones.  Sin embargo, cuando el estado de un objeto puede cambiar de forma inesperada, es la única forma garantizar un rendimiento predecible del programa.  
  
 Para declarar el objeto al que señala el puntero como **const** o `volatile`, utilice una declaración con el formato:  
  
```  
const char *cpch;  
volatile char *vpch;  
```  
  
 Para declarar el valor del puntero \(es decir, la dirección real almacenada en el puntero\) como **const** o `volatile`, utilice una declaración con el formato:  
  
```  
char * const pchc;  
char * volatile pchv;  
```  
  
 El lenguaje C\+\+ evita asignaciones que pudieran permitir la modificación de un objeto o un puntero declarado como **const**.  Estas asignaciones quitarían la información con la que se declaró el objeto o puntero, infringiendo así la intención de la declaración original.  Considere las siguientes declaraciones:  
  
```  
const char cch = 'A';  
char ch = 'B';  
```  
  
 Dadas las declaraciones anteriores de dos objetos \(`cch`, de tipo **const char** y `ch`, de tipo **char\)**, la declaración o las inicializaciones siguientes son válidas:  
  
```  
const char *pch1 = &cch;  
const char *const pch4 = &cch;  
const char *pch5 = &ch;  
char *pch6 = &ch;  
char *const pch7 = &ch;  
const char *const pch8 = &ch;  
```  
  
 La declaración o inicializaciones siguientes son erróneas.  
  
```  
char *pch2 = &cch;   // Error  
char *const pch3 = &cch;   // Error  
```  
  
 La declaración de `pch2` declara un puntero a través del cual podría modificarse un objeto constante y, por consiguiente, no se permite.  La declaración de `pch3` especifica que `pointer` es constante, no el objeto; la declaración no se permite por la misma razón que la declaración de `pch2`.  
  
 Las ocho asignaciones siguientes muestran la asignación a través de un puntero y cómo se cambia el valor del puntero para las declaraciones anteriores; por ahora, supongamos que la inicialización era correcta para las declaraciones de `pch1` a `pch8`.  
  
```  
*pch1 = 'A';  // Error: object declared const  
pch1 = &ch;   // OK: pointer not declared const  
*pch2 = 'A';  // OK: normal pointer  
pch2 = &ch;   // OK: normal pointer  
*pch3 = 'A';  // OK: object not declared const  
pch3 = &ch;   // Error: pointer declared const  
*pch4 = 'A';  // Error: object declared const  
pch4 = &ch;   // Error: pointer declared const  
```  
  
 Los punteros declarados como `volatile`, o como una combinación de **const** y `volatile`, siguen las mismas reglas.  
  
 Los punteros a objetos **const** suelen utilizarse en declaraciones de función como esta:  
  
```  
errno_t strcpy_s( char *strDestination, size_t numberOfElements, const char *strSource );  
```  
  
 La instrucción anterior declara una función, [strcpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md), donde dos de los tres argumentos son de tipo puntero a `char`.  Dado que los argumentos se pasan por referencia y no por valor, la función podría modificar libremente `strDestination` y `strSource` si `strSource` no se declaró como **const**.  La declaración de `strSource` como **const** garantiza al llamador que la función llamada no puede cambiar `strSource`.  
  
> [!NOTE]
>  Dado que hay una conversión estándar de *typename* **\*** a **const** *typename* **\***, se permite pasar un argumento de tipo **char \*** a [strcpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md).  Sin embargo, no sucede lo mismo a la inversa; no existe ninguna conversión implícita para quitar el atributo **const** de un objeto o puntero.  
  
 Un puntero **const** de un tipo determinado se puede asignar a un puntero del mismo tipo.  Sin embargo, un puntero que no es **const** no se puede asignar a un puntero **const**.  El código siguiente muestra las asignaciones correctas e incorrectas:  
  
```  
// const_pointer.cpp  
int *const cpObject = 0;  
int *pObject;  
  
int main() {  
pObject = cpObject;  
cpObject = pObject;   // C3892  
}  
```  
  
 En el ejemplo siguiente se muestra cómo declarar un objeto como const si tiene un puntero a un puntero a un objeto.  
  
```  
// const_pointer2.cpp  
struct X {  
   X(int i) : m_i(i) { }  
   int m_i;  
};  
  
int main() {  
   // correct  
   const X cx(10);  
   const X * pcx = &cx;  
   const X ** ppcx = &pcx;  
  
   // also correct  
   X const cx2(20);  
   X const * pcx2 = &cx2;  
   X const ** ppcx2 = &pcx2;  
}  
```  
  
## Vea también  
 [Punteros](../cpp/pointers-cpp.md)