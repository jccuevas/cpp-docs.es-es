---
title: "fpos (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.fpos"
  - "std::fpos"
  - "iosfwd/std::fpos"
  - "fpos"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fpos (clase)"
  - "fpos (clase), about fpos (clase)"
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# fpos (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de plantilla describe un objeto que puede almacenar toda la información necesaria para restaurar un indicador de posición de archivo arbitraria en cualquier flujo.  Un objeto de clase fpos\<**St**\> almacena efectivamente objetos de al menos dos miembros:  
  
-   Desplazamiento de bytes del tipo [streamoff](../Topic/streamoff.md).  
  
-   Estado de conversión, para su uso por un objeto de clase basic\_filebuf, del tipo **St**, normalmente `mbstate_t`.  
  
 También puede almacenar una posición de archivo arbitraria, para su uso por un objeto de clase [basic\_filebuf](../standard-library/basic-filebuf-class.md), del tipo `fpos_t`.  Sin embargo, en un entorno con limitación de tamaño del archivo, puede que `streamoff` y `fpos_t` se usen a veces indistintamente.  Para un entorno sin flujos que tengan una codificación dependiente del estado, `mbstate_t` puede en realidad estar sin usar.  Por lo tanto, el número de objetos miembro almacenados puede variar.  
  
## Sintaxis  
  
```  
  
     template <class   
     Statetype  
     >  
class fpos  
```  
  
#### Parámetros  
 *Statetype*  
 Información de estado.  
  
### Constructores  
  
|||  
|-|-|  
|[fpos](../Topic/fpos::fpos.md)|Crea un objeto que contiene información sobre una posición \(desplazamiento\) en un flujo.|  
  
### Funciones miembro  
  
|||  
|-|-|  
|[seekpos](../Topic/fpos::seekpos.md)|Se usa internamente en la biblioteca estándar de C\+\+.  No llame este método desde el código.|  
|[state](../Topic/fpos::state.md)|Establece o devuelve el estado de la conversión.|  
  
### Operadores  
  
|||  
|-|-|  
|[operator\!\=](../Topic/fpos::operator!=.md)|Indicadores de posición de archivo de las pruebas para desigualdad.|  
|[operator\+](../Topic/fpos::operator+.md)|Incrementa un indicador de posición de archivo.|  
|[operator\+\=](../Topic/fpos::operator+=.md)|Incrementa un indicador de posición de archivo.|  
|[operator\-](../Topic/fpos::operator-.md)|Disminuye un indicador de posición de archivo.|  
|[operator\-\=](../Topic/fpos::operator-=.md)|Disminuye un indicador de posición de archivo.|  
|[operator\=\=](../Topic/fpos::operator==.md)|Indicadores de posición de archivo de las pruebas para igualdad.|  
|[operador streamoff](../Topic/fpos::operator%20streamoff.md)|Convierte objetos de tipo `fpos` a objetos de tipo `streamoff`.|  
  
## Requisitos  
 **Encabezado:** \<ios\>  
  
 **Espacio de nombres:** std  
  
## Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C\+\+](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Programación con iostream](../standard-library/iostream-programming.md)   
 [Convenciones de iostreams](../standard-library/iostreams-conventions.md)