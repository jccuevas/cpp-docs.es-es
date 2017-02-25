---
title: "Inicializaci&#243;n de CRT | Microsoft Docs"
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
helpviewer_keywords: 
  - "CRT (inicialización) [C++]"
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Inicializaci&#243;n de CRT
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema describe cómo inicializa CRT estados globales en código nativo.  
  
 De forma predeterminada, el vinculador incluye la biblioteca CRT, que proporciona su propio código de inicio.  Este código de inicio inicializa la biblioteca CRT, llama a inicializadores globales, y después los llama usuario\- proporcionado a la función de `main` para aplicaciones de consola.  
  
## Inicializar un objeto global  
 Observe el código siguiente:  
  
```  
int func(void)  
{  
    return 3;  
}  
  
int gi = func();  
  
int main()  
{  
    return gi;  
}  
```  
  
 Según el estándar de C\/C\+\+, `func()` debe llamar antes de que se ejecute `main()` .  ¿Pero que se denomina?  
  
 Una manera de determinar esto es establecer un punto de interrupción en `func()`, depurar la aplicación, y examinar la pila.  Esto es posible porque el código fuente de CRT se incluye con Visual Studio.  
  
 Cuando examine las funciones de la pila, descubrirá que CRT está recorriendo mediante una lista de los punteros a función y llama a cada cuando los encuentra.  Estas funciones son similares a `func()` o los constructores de las instancias de clase.  
  
 CRT obtiene la lista de punteros a función del compilador de Visual C\+\+.  Cuando el compilador consulta un inicializador global, genera un inicializador dinámico en la sección de `.CRT$XCU` \(donde es el nombre de sección `CRT` y `XCU` es el nombre de grupo\).  Para obtener una lista de los inicializadores dinámicos ejecute el comando **dumpbin \/all main.obj**, y después busque en la sección de `.CRT$XCU` \(cuando se compila main.cpp como archivo de c\+\+., no archivo c\+\+.\).  Será similar al siguiente:  
  
```  
SECTION HEADER #6  
.CRT$XCU name  
       0 physical address  
       0 virtual address  
       4 size of raw data  
     1F2 file pointer to raw data (000001F2 to 000001F5)  
     1F6 file pointer to relocation table  
       0 file pointer to line numbers  
       1 number of relocations  
       0 number of line numbers  
40300040 flags  
         Initialized Data  
         4 byte align  
         Read Only  
  
RAW DATA #6  
  00000000: 00 00 00 00                                      ....  
  
RELOCATIONS #6  
                                                Symbol    Symbol  
 Offset    Type              Applied To         Index     Name  
 --------  ----------------  -----------------  --------  ------  
 00000000  DIR32                      00000000         C  ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))  
```  
  
 CRT define dos punteros:  
  
-   `__xc_a` en `.CRT$XCA`  
  
-   `__xc_z` en `.CRT$XCZ`  
  
 Ambos grupos no tienen ninguna otra símbolos definida excepto `__xc_a` y `__xc_z`.  
  
 Ahora, cuando el vinculador lee a varios grupos de `.CRT` , los combina en una sección y los ordena alfabéticamente.  Esto significa que los inicializadores globales definido por el usuario \(que el compilador de Visual C\+\+ coloca en `.CRT$XCU`\) procederán siempre después de `.CRT$XCA` y antes de `.CRT$XCZ`.  
  
 La sección se parecerá a la siguiente:  
  
```  
.CRT$XCA  
            __xc_a  
.CRT$XCU  
            Pointer to Global Initializer 1  
            Pointer to Global Initializer 2  
.CRT$XCZ  
            __xc_z  
```  
  
 Así, la biblioteca CRT utiliza `__xc_a` y `__xc_z` para determinar el inicio y el final de los inicializadores globales muestra debido a la manera en que se muestran en memoria después de que la imagen se carga.  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)