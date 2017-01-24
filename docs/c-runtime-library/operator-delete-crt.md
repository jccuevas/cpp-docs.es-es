---
title: "operator delete (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "delete"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator delete"
  - "eliminación escalar"
ms.assetid: bcd0066a-0022-45f5-af4c-9007c64a6b89
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator delete (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Frees asignada el bloque.  
  
## Sintaxis  
  
```  
  
      void __cdecl operator delete(  
   void * object  
);  
void __cdecl operator delete(  
   void * object,   
   void * memory  
) throw();  
void __cdecl operator delete(  
   void * object,   
   const std::nothrow_t&  
) throw();  
```  
  
#### Parámetros  
 *memory*  
 La ubicación de memoria que se libera.  
  
 *objeto*  
 Un puntero al objeto que se va a eliminar.  
  
## Comentarios  
 Este formulario de **operator borrar** se conoce como eliminar escalar, en contraposición al formulario de cancelación vectorial \([operador delete &#91;&#93;](../c-runtime-library/delete-operator-crt.md)\).  
  
 **operator borrar** libera memoria asignada por [operador nuevo](../c-runtime-library/operator-new-crt.md).  
  
 El primer formulario de este operador se conoce como el formulario de nonplacement.  El segundo y tercer formularios de este operador no se llamará normalmente de código pero existir para proporcionar al compilador una cancelación coincidente para llamar a una posición nuevos errores.  
  
 El primer formulario de operador está definido por el compilador y no requiere new.h estar incluido en el programa.  
  
 A excepción de comportamiento que produce o ninguno\- que produce, CRT **operator borrar** se comporta como [operador delete](../Topic/operator%20delete%20\(%3Cnew%3E\).md) en la biblioteca estándar de C\+\+.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**delete**|\<new.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 Vea [operador nuevo](../c-runtime-library/operator-new-crt.md) ejemplos del uso del operador **borrar**.  
  
## Vea también  
 [Asignación de memoria](../c-runtime-library/memory-allocation.md)