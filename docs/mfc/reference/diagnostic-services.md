---
title: "Servicios de diagn&#243;stico | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "diagnóstico, funciones y variables de diagnóstico"
  - "diagnóstico, servicios de diagnóstico"
  - "diagnóstico, lista de MFC general"
  - "funciones y variables de diagnóstico"
  - "macros de diagnóstico"
  - "macros de diagnóstico, lista de MFC general"
  - "servicios de diagnóstico"
  - "diagnóstico, funciones y variables de diagnóstico"
  - "diagnóstico, servicios de diagnóstico"
  - "diagnóstico, lista de MFC general"
  - "funciones y variables de diagnóstico general"
  - "macros de diagnóstico genera de MFC"
  - "MFC, servicios de diagnóstico"
  - "funciones de diagnóstico de objetos de MFC"
  - "servicios, diagnóstico"
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 21
---
# Servicios de diagn&#243;stico
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La biblioteca MFC \(Microsoft Foundation Class\) ofrece muchos servicios de diagnóstico que facilitan la depuración de los programas con mayor facilidad. Estos servicios de diagnóstico incluyen macros y funciones globales que le permiten realizar un seguimiento de las asignaciones de memoria de su programa, volcar el contenido de los objetos en tiempo de ejecución e imprimir mensajes de depuración en tiempo de ejecución. Las macros y funciones globales para servicios de diagnóstico se agrupan en las siguientes categorías:  
  
-   Macros de diagnóstico generales  
  
-   Funciones y variables de diagnóstico general  
  
-   Funciones de diagnóstico de objetos  
  
 Estas macros y funciones están disponibles para todas las clases derivadas de `CObject` en las versiones de lanzamiento y depuración de MFC. Sin embargo, todas excepto `DEBUG_NEW` y **VERIFY** no hacen nada en la versión de lanzamiento.  
  
 En la biblioteca de depuración, todos los bloques de memoria asignada están encapsulados con una serie de "bytes de protección". Si estos bytes se ven afectados por una escritura de memoria errante, las rutinas de diagnóstico pueden informar de un problema. Si incluye la línea:  
  
 [!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/CPP/diagnostic-services_1.cpp)]  
  
 en el archivo de implementación, todas las llamadas a **nuevo** almacenarán el nombre de archivo y el número de línea en el que se realizó la asignación de memoria. La función [CMemoryState::DumpAllObjectsSince](../Topic/CMemoryState::DumpAllObjectsSince.md) mostrará esta información adicional, lo que le permitirá identificar fugas de memoria. Consulte también la clase [CDumpContext](../../mfc/reference/cdumpcontext-class.md) para información adicional sobre el resultado de diagnóstico.  
  
 Además, la biblioteca de tiempo de ejecución de C también admite un conjunto de funciones de diagnóstico que puede usar para depurar sus aplicaciones. Para más información, vea [Rutinas de depuración](../../c-runtime-library/debug-routines.md) en la Referencia de la biblioteca en tiempo de ejecución.  
  
### Macros de diagnóstico generales de MFC  
  
|||  
|-|-|  
|[ASSERT](../Topic/ASSERT%20\(MFC\).md)|Imprime un mensaje y luego anula el programa si la expresión especificada se evalúa como **FALSE** en la versión de depuración de la biblioteca.|  
|[ASSERT\_KINDOF](../Topic/ASSERT_KINDOF.md)|Prueba que un objeto es un objeto de la clase especificada o de una clase derivada de la clase especificada.|  
|[ASSERT\_VALID](../Topic/ASSERT_VALID.md)|Prueba la validez interna de un objeto llamando a su función de miembro `AssertValid`; normalmente invalidada desde `CObject`.|  
|[DEBUG\_NEW](../Topic/DEBUG_NEW.md)|Ofrece un nombre de archivo y un número de línea para todas las asignaciones de objetos en modo de depuración para ayudar a encontrar fugas de memoria.|  
|[DEBUG\_ONLY](../Topic/DEBUG_ONLY.md)|Similar a **ASSERT** pero no prueba el valor de la expresión; útil para código que se debe ejecutar solo en modo de depuración.|  
|[TRACE](../Topic/TRACE.md)|Ofrece capacidad similar a `printf` en la versión de depuración de la biblioteca.|  
|[VERIFY](../Topic/VERIFY.md)|Similar a **ASSERT** pero evalúa la expresión en la versión de lanzamiento de la biblioteca, así como en la versión de depuración.|  
  
### Funciones y variables de diagnóstico general de MFC  
  
|||  
|-|-|  
|[afxDump](../Topic/afxDump%20\(CDumpContext%20in%20MFC\).md)|Variable global que envía información de [CDumpContext](../../mfc/reference/cdumpcontext-class.md) a la ventana de salida del depurador o al terminal de depuración.|  
|[afxMemDF](../Topic/afxMemDF.md)|Variable global que controla el comportamiento del asignador de memoria de depuración.|  
|[AfxCheckError](../Topic/AfxCheckError.md)|Variable global que se usa para probar el **SCODE** pasado para ver si es un error y, si es así, genera el error correspondiente.|  
|[AfxCheckMemory](../Topic/AfxCheckMemory.md)|Comprueba la integridad de toda la memoria asignada actualmente.|  
|[AfxDump](../Topic/AfxDump%20\(MFC\).md)|Si se llama mientras se encuentra en el depurador, vuelca el estado de un objeto durante la depuración.|  
|[AfxDumpStack](../Topic/AfxDumpStack.md)|Genera una imagen de la pila actual. Esta función siempre está vinculada estáticamente.|  
|[AfxEnableMemoryLeakDump](../Topic/AfxEnableMemoryLeakDump.md)|Habilita el volcado de fuga de memoria.|  
|[AfxEnableMemoryTracking](../Topic/AfxEnableMemoryTracking.md)|Activa y desactiva el seguimiento de la memoria.|  
|[AfxIsMemoryBlock](../Topic/AfxIsMemoryBlock.md)|Comprueba que se ha asignado correctamente un bloque de memoria.|  
|[AfxIsValidAddress](../Topic/AfxIsValidAddress.md)|Comprueba que un intervalo de direcciones de memoria se encuentra dentro de los límites del programa.|  
|[AfxIsValidString](../Topic/AfxIsValidString.md)|Determina si un puntero a una cadena es válido.|  
|[AfxSetAllocHook](../Topic/AfxSetAllocHook.md)|Permite la llamada de una función en cada asignación de memoria.|  
  
### Funciones de diagnóstico de objetos de MFC  
  
|||  
|-|-|  
|[AfxDoForAllClasses](../Topic/AfxDoForAllClasses.md)|Realiza una función especificada en todas las clases derivadas por `CObject` que admiten la comprobación de tipos en tiempo de ejecución.|  
|[AfxDoForAllObjects](../Topic/AfxDoForAllObjects.md)|Realiza una función especificada en todos los objetos derivados por `CObject` asignados con **nuevo**.|  
  
## Vea también  
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)