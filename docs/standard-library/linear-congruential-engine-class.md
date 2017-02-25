---
title: "linear_congruential_engine (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.tr1.linear_congruential_engine"
  - "random/std::tr1::linear_congruential_engine"
  - "linear_congruential_engine"
  - "std::tr1::linear_congruential_engine"
  - "tr1.linear_congruential_engine"
  - "tr1::linear_congruential_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "linear_congruential_engine (clase)"
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# linear_congruential_engine (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una secuencia aleatoria mediante un algoritmo congruencial lineal.  
  
## Sintaxis  
  
```  
template<class UIntType, UIntType A, UIntType C, UIntType M>  
class linear_congruential_engine{  
public:  
    // types  
    typedef UIntType result_type;  
  
    // engine characteristics  
    static constexpr result_type multiplier = a;  
    static constexpr result_type increment = c;  
    static constexpr result_type modulus = m;  
    static constexpr result_type min() { return c == 0u ? 1u: 0u; }  
    static constexpr result_type max() { return m - 1u; }  
    static constexpr result_type default_seed = 1u;  
  
    // constructors and seeding functions  
    explicit linear_congruential_engine(result_type s = default_seed);  
    template<class Sseq> explicit linear_congruential_engine(Sseq& q);  
    void seed(result_type s = default_seed);  
    template<class Sseq> void seed(Sseq& q);  
  
    // generating functions  
    result_type operator()();  
    void discard(unsigned long long z);  
};  
```  
  
#### Parámetros  
 `UIntType`  
 El tipo de resultado integral sin signo. Para los tipos posibles, consulte [\<random\>](../standard-library/random.md).  
  
 `A`  
 **Multiplicador**.**Condición previa**: sección Vea comentarios.  
  
 `C`  
 **Incremento**.**Condición previa**: sección Vea comentarios.  
  
 `M`  
 **Módulo**.**Condición previa**: vea la sección Comentarios.  
  
## Miembros  
  
||||  
|-|-|-|  
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|  
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|  
  
 `default_seed` es un miembro constante, definido como `1u`, utilizado como el valor de parámetro predeterminado para `linear_congruential_engine::seed` y el constructor de valores simple.  
  
 Para obtener más información acerca de los miembros del motor, consulte [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 La clase de plantilla `linear_congruential_engine` es el motor de generador más sencillo, pero no el más rápido ni de mejor calidad. Una mejora realizada sobre este motor es el [motor de resta llevando](../standard-library/subtract-with-carry-engine-class.md). Ninguno de estos motores logra unos resultados tan rápidos y de una calidad tan enorme como el [motor Mersenne Twister](../standard-library/mersenne-twister-engine-class.md).  
  
 Este motor genera valores de un tipo integral sin signo especificado por el usuario mediante la relación de repetición \(*período*\) `x(i) = (A * x(i-1) + C) mod M`.  
  
 Si `M` es cero, el valor usado en esta operación de módulo es `numeric_limits<result_type>::max() + 1`. El estado del motor es el último valor devuelto, o bien el valor de inicialización si no se ha llamado a `operator()`.  
  
 Si `M` no es cero, los valores de los argumentos de plantilla `A` y `C` deben ser inferiores a `M`.  
  
 Aunque puede construir directamente un generador de este motor, también puede utilizar una de estas definiciones de tipos predefinidos.  
  
 `minstd_rand0`: motor estándar mínimo 1988 \(Lewis, Goodman y Miller, 1969\).  
  
```  
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;  
```  
  
 `minstd_rand`: Actualizada motor estándar mínimo `minstd_rand0` \(Park, Miller y Stockmeyer, 1993\).  
  
```  
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;  
```  
  
 Para obtener información detallada acerca del algoritmo de motor congruencial lineal, vea el artículo de la Wikipedia [generador congruencial lineal](http://go.microsoft.com/fwlink/?LinkId=402446).  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)