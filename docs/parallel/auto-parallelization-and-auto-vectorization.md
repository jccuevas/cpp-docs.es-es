---
title: "Paralelizaci&#243;n y vectorizaci&#243;n autom&#225;ticas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: ec71583a-287b-4599-8767-1d255e080fe3
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# Paralelizaci&#243;n y vectorizaci&#243;n autom&#225;ticas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El paralelizador automático y el vectorizador automático se han diseñado para proporcionar mejoras automáticas de rendimiento de los bucles en el código.  
  
## Paralelizador automático  
 El modificador del compilador [\/Qpar](../build/reference/qpar-auto-parallelizer.md) habilita la *paralelización automática* de bucles en el código.  Cuando se especifica este marcador sin cambiar el código existente, el compilador evalúa el código para buscar los bucles que podrían beneficiarse de la paralelización.  Dado que podría encontrar bucles que no hacen mucho trabajo y, por tanto, no se beneficiarán de la paralelización, y debido a que cada paralelización innecesaria puede acaparar un grupo de subprocesos o producir sincronización adicional u otro procesamiento que tendería a disminuir el rendimiento en lugar de mejorarlo, el compilador es conservador en la selección de los bucles que ejecuta en paralelo.  Por ejemplo, considere el siguiente ejemplo en el que el límite superior del bucle no se conoce en tiempo de compilación:  
  
```cpp  
  
void loop_test(int u) {  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 Dado que `u` puede ser un valor pequeño, el compilador no paralelizará automáticamente este bucle.  Sin embargo, es posible que el usuario todavía desee paralelizarlo porque sabe que `u` siempre será grande.  Para habilitar la paralelización automática, especifique [\#pragma loop\(hint\_parallel\(n\)\)](../preprocessor/loop.md), donde `n` es el número de subprocesos que se van a paralelizar.  En el ejemplo siguiente, el compilador intentará paralelizar el bucle entre 8 subprocesos.  
  
```cpp  
  
void loop_test(int u) {  
#pragma loop(hint_parallel(8))  
   for (int i=0; i<u; ++i)  
      A[i] = B[i] * C[i];  
}  
```  
  
 Al igual que ocurre con todas las [directivas pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), también se admite la sintaxis de directiva pragma alternativa `__pragma(loop(hint_parallel(n)))`.  
  
 Hay algunos bucles que el compilador no puede paralelizar aunque lo desee.  Por ejemplo:  
  
```cpp  
  
#pragma loop(hint_parallel(8))  
for (int i=0; i<upper_bound(); ++i)  
    A[i] = B[i] * C[i];  
```  
  
 La función `upper_bound()` puede cambiar cada vez que se la llama.  Dado que el límite superior no puede conocerse, el compilador puede emitir un mensaje de diagnóstico que explica por qué no se puede paralelizar este bucle.  En el ejemplo siguiente se muestra un bucle que se puede paralelizar, un bucle que no se puede paralelizar, la sintaxis del compilador que se usa en el símbolo del sistema y la salida del compilador para cada opción de línea de comandos:  
  
```cpp  
int A[1000];  
void test() {  
#pragma loop(hint_parallel(0))  
    for (int i=0; i<1000; ++i) {  
        A[i] = A[i] + 1;  
    }  
  
    for (int i=1000; i<2000; ++i) {  
        A[i] = A[i] + 1;  
    }  
}  
  
```  
  
 La compilación con este comando:  
  
 **cl d:\\myproject\\mylooptest.cpp \/O2 \/Qpar \/Qpar\-report:1**  
  
 produce este resultado:  
  
 **\-\-\- Analyzing function: void \_\_cdecl test\(void\)**   
  **d:\\myproject\\mytest.cpp\(4\) : loop parallelized**  
  
 La compilación con este comando:  
  
 **cl d:\\myproject\\mylooptest.cpp \/O2 \/Qpar \/Qpar\-report:2**  
  
 produce este resultado:  
  
 **\-\-\- Analyzing function: void \_\_cdecl test\(void\)**   
  **d:\\myproject\\mytest.cpp\(4\) : loop parallelized**   
  **d:\\myproject\\mytest.cpp\(4\) : loop not parallelized due to reason '1008'**  
  
 Observe la diferencia en la salida de las dos opciones distintas de [\/Qpar\-report \(Nivel de información de paralelizador automático\)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md).  **\/Qpar\-report:1** genera mensajes del paralelizador solo para los bucles que se paralelizan correctamente.  **\/Qpar\-report:2** genera mensajes del paralelizador para las paralelizaciones de bucles correctas e incorrectas.  
  
 Para obtener más información sobre los códigos de motivo y los mensajes, vea [Mensajes del vectorizador y paralelizador](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
## Vectorizador automático  
 El vectorizador automático analiza los bucles del código y usa los registros y las instrucciones de vector en el equipo de destino para ejecutarlos si puede.  Esto puede mejorar el rendimiento del código.  El compilador tiene como destino las instrucciones SSE2, AVX y AVX2 en procesadores Intel o AMD, o las instrucciones NEON en procesadores ARM, según el modificador [\/arch](../build/reference/arch-minimum-cpu-architecture.md).  
  
 El vectorizador automático puede generar instrucciones diferentes de las que especifica el modificador **\/arch**.  Estas instrucciones estarán protegidas por una comprobación en tiempo de ejecución para asegurarse de que código se ejecuta correctamente.  Por ejemplo, cuando se compila **\/arch:SSE2**, se pueden emitir instrucciones SSE4.2.  Una comprobación en tiempo de ejecución comprueba que SSE4.2 está disponible en el procesador de destino y salta a una versión no SSE4.2 del bucle si el procesador no admite las instrucciones.  
  
 De forma predeterminada, se habilita el vectorizador automático.  Si desea comparar el rendimiento del código sometido a la vectorización, puede utilizar [\#pragma loop\(no\_vector\)](../preprocessor/loop.md) para deshabilitar la vectorización de un bucle concreto.  
  
```  
  
#pragma loop(no_vector)  
for (int i = 0; i < 1000; ++i)  
   A[i] = B[i] + C[i];  
  
```  
  
 Al igual que ocurre con todas las [directivas pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md), también se admite la sintaxis de directiva pragma alternativa `__pragma(loop(no_vector))`.  
  
 Al igual que en el paralelizador automático, se puede especificar la opción de línea de comandos [\/Qvec\-report \(Nivel de información de vectorizador automático\)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md) para notificar solo los bucles vectorizados correctamente \(**\/Qvec\-report:1**\) o los bucles vectorizados correcta e incorrectamente \(**\/Qvec\-report:2**\).  
  
 Para obtener más información sobre los códigos de motivo y los mensajes, vea [Mensajes del vectorizador y paralelizador](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md).  
  
 Para obtener un ejemplo que muestra cómo funciona el vectorizador en la práctica, vea [Proyecto Austin, parte 2 de 6: Volver una página](http://blogs.msdn.com/b/vcblog/archive/2012/09/27/10348494.aspx)  
  
## Vea también  
 [loop](../preprocessor/loop.md)   
 [Programación paralela en código nativo](http://go.microsoft.com/fwlink/?LinkId=263662)   
 [\/Qpar \(Paralelizador automático\)](../build/reference/qpar-auto-parallelizer.md)   
 [\/Qpar\-report \(Nivel de información de paralelizador automático\)](../build/reference/qpar-report-auto-parallelizer-reporting-level.md)   
 [\/Qvec\-report \(Nivel de información de vectorizador automático\)](../build/reference/qvec-report-auto-vectorizer-reporting-level.md)   
 [Mensajes del vectorizador y paralelizador](../error-messages/tool-errors/vectorizer-and-parallelizer-messages.md)