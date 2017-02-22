---
title: "random_device (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "random_device"
  - "random/std::tr1::random_device"
  - "tr1.random_device"
  - "std::tr1::random_device"
  - "std.tr1.random_device"
  - "tr1::random_device"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "random_device (clase)"
  - "random_device (clase) [TR1]"
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# random_device (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una secuencia aleatoria desde un dispositivo externo.  
  
## Sintaxis  
  
```  
class random_device { public:     typedef unsigned int result_type;     // cosntructor     explicit random_device(const std::string& token = "");     // properties     static result_type min();     static result_type max();     double entropy() const;     // generate     result_type operator()();     // no-copy functions     random_device(const random_device&) = delete;     void operator=(const random_device&) = delete; };  
```  
  
## Miembros  
  
|||  
|-|-|  
|[random\_device::random\_device](../Topic/random_device::random_device.md)|[random\_device::entropy](../Topic/random_device::entropy.md)|  
|[random\_device::operator\(\)](../Topic/random_device::operator\(\).md)||  
  
## Comentarios  
 La clase describe un origen de números aleatorios y puede ser \(aunque no es obligatorio\) no determinista o segura criptográficamente según la norma ISO C\+\+.  En la implementación de Visual Studio, los valores generados son no deterministas y seguros criptográficamente, pero se ejecutan con mayor lentitud que los generadores creados a partir de motores y adaptadores de motor \(como el [motor Mersenne Twister](../standard-library/mersenne-twister-engine-class.md), que constituye la opción de motor más rápida y de mejor calidad la mayoría de las veces\).  
  
 Los resultados de `random_device` se distribuyen uniformemente en el intervalo cerrado \[`0, 2`<sup>32</sup>\].  
  
 No está garantizado que `random_device` resulte en una llamada de no bloqueo.  
  
 `random_device` se suele usar para propagar otros generadores creados con motores o adaptadores de motor.  Para obtener más información, vea [\<random\>](../standard-library/random.md).  
  
## Ejemplo  
 En el siguiente código se muestra la funcionalidad básica de esta clase y resultados de ejemplo.  Dada la índole no determinista de `random_device`, los valores aleatorios que aparecen en la sección **Resultado** no coincidirán con los suyos.  Esto es normal y lo que se espera.  
  
```cpp  
// random_device_engine.cpp   
// cl.exe /W4 /nologo /EHsc /MTd   
#include <random>   
#include <iostream>   
using namespace std;  
  
int main()   
{   
    random_device gen;   
  
    cout << "entropy == " << gen.entropy() << endl;   
    cout << "min == " << gen.min() << endl;   
    cout << "max == " << gen.max() << endl;   
  
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
}  
```  
  
 **Resultado:**  
  
  **entropy \=\= 32**  
**min \=\= 0**  
**max \=\= 4294967295**  
**10 valores aleatorios:**  
**4183829181**  
**1454391608**  
**1176278697**  
**2468830096**  
**3959347222**  
**1803123400**  
**1339590545**  
**1304896877**  
**604088490**  
**2293276253** Este ejemplo es simplista y no representa el caso de uso general de este generador.  Para ver un código de ejemplo más ilustrativo, vea [\<random\>](../standard-library/random.md).  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:**  std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)