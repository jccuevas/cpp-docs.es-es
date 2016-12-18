---
title: "C&#243;mo: Calcular las referencias a estructuras mediante PInvoke | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cálculo de referencias de datos [C++], estructuras"
  - "interoperabilidad [C++], estructuras"
  - "calcular las referencias [C++], estructuras"
  - "invocación de plataforma [C++], estructuras"
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
caps.latest.revision: 30
caps.handback.revision: 28
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Calcular las referencias a estructuras mediante PInvoke
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este documento se explica cómo se puede llamar a funciones nativas que aceptan cadenas de lenguaje C desde funciones administradas que proporcionan una instancia de <xref:System.String> utilizando P\/Invoke.  Aunque recomendamos el uso de características de interoperabilidad de C\+\+ en lugar de P\/Invoke porque P\/Invoke proporciona pocos informes de errores en tiempo de compilación, no tiene seguridad de tipos y puede ser tedioso de implementar, si la API no administrada se empaqueta como archivo DLL y el código fuente no está disponible, P\/Invoke es la única opción.  De lo contrario, vea los siguientes documentos:  
  
-   [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [How to: Marshal Structures Using PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
 De forma predeterminada, las estructuras nativas y las administradas se distribuyen de manera diferente en la memoria, por lo que, para pasar correctamente estructuras por el límite entre administrado y no administrado, se requieren pasos adicionales para preservar la integridad de los datos.  
  
 En este documento se explican los pasos necesarios para definir equivalentes administrados de estructuras nativas y cómo se pueden pasar las estructuras resultantes a funciones no administradas.  En este documento se supone que se utilizan estructuras simples \(las que no contienen cadenas o punteros\).  Para obtener información sobre interoperabilidad que no puede transferirse en bloque de bits, vea [Utilizar la interoperabilidad de C\+\+ \(PInvoke implícito\)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  P\/Invoke no puede contener tipos que no pueden transferirse en bloque de bits como valor devuelto.  Los tipos que pueden transferirse en bloque de bits tienen la misma representación en código administrado y no administrado.  Para obtener más información, vea [Blittable and Non\-Blittable Types](../Topic/Blittable%20and%20Non-Blittable%20Types.md).  
  
 El cálculo de referencias en estructuras simples que pueden transferirse en bloque de bits entre el límite entre administrado y no administrado requiere en primer lugar que se definan versiones administradas de cada estructura nativa.  Estas estructuras pueden tener cualquier nombre válido; no existe ninguna relación entre la versión nativa y la administrada de las dos estructuras, salvo su distribución de datos.  Por consiguiente, es vital que la versión administrada contenga campos que tengan el mismo tamaño y que estén en el mismo orden que en la versión nativa. \(No existe un mecanismo para garantizar que las versiones administrada y nativa de la estructura sean equivalentes, por lo que las incompatibilidades no se pondrán de manifiesto hasta el tiempo de ejecución.  Es responsabilidad del programador asegurarse de que las dos estructuras tienen la misma distribución de datos.\)  
  
 Dado que, en ocasiones, los miembros de estructuras administradas se reorganizan por motivos de rendimiento, es necesario utilizar el atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> para indicar que la estructura tiene una distribución secuencial.  También es buena idea establecer explícitamente la configuración de empaquetado de la estructura para que sea igual a la que utiliza la estructura nativa \(aunque, de manera predeterminada, Visual C\+\+ utiliza un empaquetado de la estructura de 8 bytes para ambos códigos administrados\).  
  
1.  A continuación, utilice <xref:System.Runtime.InteropServices.DllImportAttribute> para declarar puntos de entrada que correspondan a cualquier función no administrada que acepte la estructura, pero use la versión administrada de la estructura en las firmas de la función, lo que es un punto discutible si se usa el mismo nombre para ambas versiones de la estructura.  
  
2.  Así, el código administrado ya puede pasar la versión administrada de la estructura a las funciones no administradas como si realmente se tratase de funciones administradas.  Estas estructuras se pueden pasar por valor o por referencia, como se muestra en el ejemplo siguiente.  
  
## Ejemplo  
 El código siguiente está compuesto por módulo administrado y en uno no administrado.  El módulo no administrado es un archivo DLL que define una estructura llamada Location y una función llamada GetDistance, que acepta dos instancias de la estructura Location.  El segundo módulo es una aplicación de línea de comandos administrada, que importa la función GetDistance, pero la define en cuanto a un equivalente administrado de la estructura Location: MLocation.  En la práctica, es probable que ambas versiones de la estructura utilizasen el mismo nombre; sin embargo, aquí se usa un nombre distinto para mostrar que el prototipo DllImport se define en cuanto a la versión administrada.  
  
 El módulo administrado se compila con \/clr, pero \/clr:pure también funciona.  
  
 Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional directiva \#include.  De hecho, sólo se puede obtener acceso al archivo DLL en tiempo de ejecución, por lo que no se detectarán problemas con funciones importadas con DllImport en tiempo de compilación.  
  
```  
// TraditionalDll3.cpp  
// compile with: /LD /EHsc  
#include <iostream>  
#include <stdio.h>  
#include <math.h>  
  
#define TRADITIONALDLL_EXPORTS  
#ifdef TRADITIONALDLL_EXPORTS  
   #define TRADITIONALDLL_API __declspec(dllexport)  
#else  
   #define TRADITIONALDLL_API __declspec(dllimport)  
#endif  
  
#pragma pack(push, 8)  
struct Location {  
   int x;  
   int y;  
};  
#pragma pack(pop)  
  
extern "C" {  
   TRADITIONALDLL_API double GetDistance(Location, Location);  
   TRADITIONALDLL_API void InitLocation(Location*);  
}  
  
double GetDistance(Location loc1, Location loc2) {  
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);  
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);  
  
   double h = loc1.x - loc2.x;  
   double v = loc1.y = loc2.y;  
   double dist = sqrt( pow(h,2) + pow(v,2) );  
  
   return dist;  
}  
  
void InitLocation(Location* lp) {  
   printf_s("[unmanaged] Initializing location...\n");  
   lp->x = 50;  
   lp->y = 50;  
}  
```  
  
## Ejemplo  
  
```  
// MarshalStruct_pi.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, Pack=8)]  
value struct MLocation {  
   int x;  
   int y;  
};  
  
value struct TraditionalDLL {  
   [DllImport("TraditionalDLL3.dll")]  
   static public double GetDistance(MLocation, MLocation);  
   [DllImport("TraditionalDLL3.dll")]  
   static public double InitLocation(MLocation*);  
};  
  
int main() {  
   MLocation loc1;  
   loc1.x = 0;  
   loc1.y = 0;  
  
   MLocation loc2;  
   loc2.x = 100;  
   loc2.y = 100;  
  
   double dist = TraditionalDLL::GetDistance(loc1, loc2);  
   Console::WriteLine("[managed] distance = {0}", dist);  
  
   MLocation loc3;  
   TraditionalDLL::InitLocation(&loc3);  
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);  
}  
```  
  
  **\[no administrado\] loc1\(0,0\) loc2\(100,100\)**  
**\[administrado\] distancia \= 141.42135623731**  
**\[no administrado\] Inicializar ubicación...**  
**\[administrado\] x\=50 y\=50**   
## Vea también  
 [Utilizar un elemento PInvoke explícito en C\+\+ \(Atributo DllImport\)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)