---
title: "mersenne_twister_engine (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "random/std::tr1::mersenne_twister_engine"
  - "tr1.mersenne_twister_engine"
  - "std.tr1.mersenne_twister_engine"
  - "std::tr1::mersenne_twister_engine"
  - "tr1::mersenne_twister_engine"
  - "mersenne_twister_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mersenne_twister_engine (clase)"
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
caps.latest.revision: 23
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# mersenne_twister_engine (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genera una secuencia de íntegros aleatoria de alta calidad basada en el algoritmo de Mersenne twister.  
  
## Sintaxis  
  
```  
template<class UIntType,   
    size_t W, size_t N, size_t M, size_t R,  
    UIntType A, size_t U, UIntType D, size_t S,  
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>  
class mersenne_twister_engine;  
```  
  
#### Parámetros  
 `UIntType`  
 El tipo de resultado integral sin signo. Para los tipos posibles, consulte [\<random\>](../standard-library/random.md).  
  
 `W`  
 **Tamaño de palabra**. Tamaño de cada palabra, en bits, de la secuencia de estado.**Condición previa**: `2u < W ≤ numeric_limits<UIntType>::digits`  
  
 `N`  
 **Tamaño de estado**. El número de elementos \(valores\) en la secuencia de estado.  
  
 `M`  
 **Tamaño de cambio**. El número de elementos que omitir durante cada vuelta.**Condición previa**: `0 < M ≤ N`  
  
 `R`  
 **Bits de máscara**.**Condición previa**: `R ≤ W`  
  
 `A`  
 **Máscara XOR**.**Condición previa**: `A ≤ (1u<<W) - 1u`  
  
 `U`, `S`, `T`, `L`  
 **Parámetros de cambio de atenuación**. Utilizados como valores de cambio durante la codificación \(atenuación\). Condición previa: `U,S,T,L ≤ W`  
  
 `D`, `B`, `C`  
 **Parámetros de máscara de bit de atenuación**. Utilizados como valores de máscara de bit durante la codificación \(atenuación\). Condición previa: `D,B,C ≤ (1u<<W) - 1u`  
  
 `F`  
 **Multiplicador de inicialización**. Utilizado para ayudar a la inicialización de la secuencia. Condición previa: `F ≤ (1u<<W) - 1u`  
  
## Miembros  
  
||||  
|-|-|-|  
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|  
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|  
  
 `default_seed` es un miembro constante, definido como `5489u`, utilizado como el valor de parámetro predeterminado para `mersenne_twister_engine::seed` y el constructor de valores simple.  
  
 Para obtener más información acerca de los miembros del motor, consulte [\<random\>](../standard-library/random.md).  
  
## Comentarios  
 Esta clase de plantilla describe un motor de números aleatorios, devolver valores en el intervalo cerrado \[`0`, `2`<sup>W</sup> \- `1`\]. Contiene un valor integral grande con `W * (N - 1) + R` bits. Extrae `W` bits cada vez de este valor grande y, cuando ha utilizado todos los bits, modifica el valor grande cambiando y mezclando los bits para tener un conjunto de bits nuevo del que extraer. El estado del motor es el último `N``W`\-bit de valores que se utilizan si `operator()` se ha llamado al menos `N` el tiempo de espera, en caso contrario el `M``W`\-bit de valores que se han utilizado y el último `N - M` valores de la inicialización.  
  
 El generador modifica el valor grande que contiene utilizando un registro de cambio de informe generalizado modificado, definido por valores de cambio `N` y `M`, un valor de cambio `R` y una máscara XOR condicional `A`. Además, los bits del registro de cambio sin procesar se codifican \(atenúan\) según una matriz de codificación de bits definida por valores `U`, `D`, `S`, `B`, `T`, `C` y `L`.  
  
 El argumento de plantilla `UIntType` debe ser lo suficientemente grande como para contener valores `2`<sup>W</sup> \- `1`. Los valores de los otros argumentos de plantilla deben cumplir los requisitos siguientes: `2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`.  
  
 Aunque puede construir directamente un generador de este motor, se recomienda que utilizar una de estas definiciones de tipos predefinidas:  
  
 `mt19937`: motor de 32 bits Mersenne twister \(Matsumoto y Nishimura, 1998\).  
  
```  
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,   
    31, 0x9908b0df,   
    11, 0xffffffff,   
    7, 0x9d2c5680,   
    15, 0xefc60000,   
    18, 1812433253> mt19937;  
```  
  
 `mt19937_64`: motor de 64 bits Mersenne twister \(Matsumoto y Nishimura, 2000\).  
  
```  
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,   
    31, 0xb5026f5aa96619e9ULL,   
    29, 0x5555555555555555ULL,   
    17, 0x71d67fffeda60000ULL,   
    37, 0xfff7eee000000000ULL,   
    43, 6364136223846793005ULL> mt19937_64;  
```  
  
 Para obtener información detallada sobre el algoritmo de Mersenne twister, vea el artículo de la Wikipedia [Mersenne twister](http://go.microsoft.com/fwlink/?LinkId=402356).  
  
## Ejemplo  
 Para obtener un ejemplo de código, vea [\<random\>](../standard-library/random.md).  
  
## Requisitos  
 **Encabezado:** \<random\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [\<random\>](../standard-library/random.md)