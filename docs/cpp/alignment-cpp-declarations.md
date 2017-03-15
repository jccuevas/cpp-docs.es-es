---
title: "Alineaci&#243;n (declaraciones de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Alineaci&#243;n (declaraciones de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una de las características de bajo nivel de C\+\+ es la capacidad para especificar la alineación precisa de los objetos en la memoria para sacar el máximo partido de una arquitectura de hardware específica.  De forma predeterminada el compilador alinea los miembros de clases y struct en su valor de tamaño: bool y char se alinean en límites de un byte, short en dos bytes, int en cuatro bytes y long long, double y long double en ocho bytes.  En la mayoría de los escenarios no tendrá que preocuparse jamás por la alineación, puesto que la alineación predeterminada ya es óptima.  No obstante, en algunos casos se pueden conseguir importantes mejoras de rendimiento o ahorros de memoria al especificar una alineación personalizada para sus estructuras de datos.  Antes de Visual Studio 2015 podía usar las palabras clave \_\_alignof y declspec\(alignas\) específicas de Microsoft para especificar una alineación mayor que el valor predeterminado.  Desde Visual Studio 2015 se deben usar las palabras clave estándar de C\+\+11 [alignof y alignas](../cpp/alignof-and-alignas-cpp.md) para aumentar al máximo la portabilidad de su código.  A efectos prácticos, las nuevas palabras clave se comportan de la misma manera que las extensiones específicas de Microsoft. Además, la documentación de esas extensiones también se aplica a las nuevas palabras clave.  Vea el [\_\_alignof \(Operador\)](../cpp/alignof-operator.md) y [align](../cpp/align-cpp.md) para obtener más información.  El estándar de C\+\+ no especifica el comportamiento de empaquetado para alinear en límites inferiores al valor predeterminado del compilador para la plataforma de destino, por lo que seguirá teniendo que usar el [pack](../preprocessor/pack.md) \#pragma de Microsoft en ese caso.  
  
 La biblioteca estándar de C\+\+ proporciona la [aligned\_storage \(Clase\)](../standard-library/aligned-storage-class.md) para asignar memoria a estructuras de datos con alineaciones personalizadas y la [Clase aligned\_union](../standard-library/aligned-union-class.md) para especificar la alineación de uniones con constructores o destructores no triviales.  
  
## Acerca de la alineación  
 La alineación es una propiedad de una dirección de memoria, expresada como el módulo de la dirección numérica a una potencia de 2.  Por ejemplo, la dirección 0x0001103F módulo 4 es 3; se dice que esa dirección está alineada con 4n\+3, donde 4 indica la potencia de 2 elegida.  La alineación de una dirección depende de la potencia de dos elegida.  El mismo módulo de dirección 8 es 7.  Se dice que una dirección está alineada con X si su alineación es Xn\+0.  
  
 Las CPU ejecutan instrucciones que operan en los datos almacenados en la memoria y los datos se identifican por sus direcciones en la memoria.  Además de su dirección, un dato individual también tiene un tamaño.  Se dice que un dato está alineado naturalmente si su dirección está alineada a su tamaño y desalineado si no lo está.  Por ejemplo, un dato de punto flotante de 8 bytes se encuentra alineado naturalmente si la dirección que se utiliza para identificarlo está alineada a 8.  
  
 Control de alineación de datos de los compiladores Los compiladores del dispositivo intentan asignar los datos de forma que se impida su desalineación.  
  
 Para los tipos de datos simples, el compilador asigna direcciones que son múltiplos del tamaño en bytes del tipo de datos.  De este modo, el compilador asigna direcciones a variables de tipo long que son múltiplos de cuatro, estableciendo los dos bits de la parte inferior de la dirección en cero.  
  
 Además, el compilador rellena las estructuras de tal manera que alinea naturalmente cada elemento de la estructura.  Considere la estructura struct x\_ en el siguiente ejemplo de código:  
  
```  
struct x_  
{  
   char a;     // 1 byte  
   int b;      // 4 bytes  
   short c;    // 2 bytes  
   char d;     // 1 byte  
} MyStruct;  
  
```  
  
 El compilador rellena esta estructura para aplicar la alineación de forma natural.  
  
 En el siguiente ejemplo de código se muestra cómo el compilador coloca la estructura rellenada en memoria:  
  
```  
// Shows the actual memory layout  
struct x_  
{  
   char a;            // 1 byte  
   char _pad0[3];     // padding to put 'b' on 4-byte boundary  
   int b;            // 4 bytes  
   short c;          // 2 bytes  
   char d;           // 1 byte  
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4  
}  
  
```  
  
1.  Ambas declaraciones devuelven sizeof\(struct x\_\) como 12 bytes.  
  
2.  La segunda declaración incluye dos elementos de relleno:  
  
3.  char \_pad0\[3\] para alinear el miembro int b en un límite de cuatro bytes y  
  
4.  char \_pad1\[1\] para alinear los elementos de la matriz de la estructura \_x struct bar\[3\].  
  
5.  El relleno alinea los elementos de bar\[3\] de tal forma que permite el acceso natural.  
  
 En el código de ejemplo siguiente se muestra el diseño de matriz bar\[3\]:  
  
```  
adr offset   element  
------   -------  
0x0000   char a;         // bar[0]  
0x0001   char pad0[3];  
0x0004   int b;  
0x0008   short c;  
0x000a   char d;  
0x000b   char _pad1[1];  
  
0x000c   char a;         // bar[1]  
0x000d   char _pad0[3];  
0x0010   int b;  
0x0014   short c;  
0x0016   char d;  
0x0017   char _pad1[1];  
  
0x0018   char a;         // bar[2]  
0x0019   char _pad0[3];  
0x001c   int b;  
0x0020   short c;  
0x0022   char d;  
0x0023   char _pad1[1];  
  
```  
  
## Vea también  
 [Alineación de estructuras de datos](http://en.wikipedia.org/wiki/Data_structure_alignment)