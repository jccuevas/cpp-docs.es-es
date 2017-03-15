---
title: "Cargar todas las importaciones para un archivo DLL de carga retrasada | Microsoft Docs"
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
  - "__HrLoadAllImportsForDll (opción del vinculador)"
ms.assetid: 975fcd97-1a56-4a16-9698-e1a249d2d592
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Cargar todas las importaciones para un archivo DLL de carga retrasada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función **\_\_HrLoadAllImportsForDll**, que se define en delayhlp.cpp, indica al vinculador que cargue todas las importaciones de un archivo DLL especificado con la opción de vinculador [\/delayload](../../build/reference/delayload-delay-load-import.md).  
  
 La carga de todas las importaciones permite colocar el control de errores en el código sin tener que utilizarlo en torno a las llamadas reales a las importaciones.  También evita que la aplicación sufra errores parciales como consecuencia de un proceso en el que el código auxiliar no puede cargar una importación.  
  
 La llamada a **\_\_HrLoadAllImportsForDll** no modifica el comportamiento de los enlaces y del control de errores; vea [Notificación y control de errores](../../build/reference/error-handling-and-notification.md) para obtener más información.  
  
 El nombre de DLL que se pasa a **\_\_HrLoadAllImportsForDll** se compara con el nombre almacenado en la propia DLL y distingue entre mayúsculas y minúsculas.  
  
 El ejemplo siguiente muestra cómo llamar a **\_\_HrLoadAllImportsForDll**:  
  
```  
if (FAILED(__HrLoadAllImportsForDll("delay1.dll"))) {  
   printf ( "failed on snap load, exiting\n" );  
   exit(2);  
}  
```  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)