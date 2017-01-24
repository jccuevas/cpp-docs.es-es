---
title: "Opciones de EDITBIN | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "editbin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EDITBIN (programa), opciones"
ms.assetid: 2da9f88e-cbab-4d64-bb66-ef700535230f
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Opciones de EDITBIN
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede utilizar EDITBIN para modificar archivos objeto, archivos ejecutables y bibliotecas de vínculos dinámicos \(DLLs\).  Las opciones especifican los cambios que EDITBIN realiza.  
  
 Una opción consta de un especificador de opción, que puede ser un guión \(–\) o una barra diagonal \(\/\), seguido por el nombre de la opción.  Los nombres de opción no pueden abreviarse.  Algunas opciones toman argumentos que se especifican al carácter de dos puntos \(: \).  No se permiten espacios ni tabulaciones dentro de una especificación de opción.  Use uno o más espacios o tabulaciones para separar especificaciones de opción en la línea de comandos.  Los nombres de opción y sus argumentos de la palabra clave o los argumentos de nombre de archivo no distinguen entre mayúsculas y minúsculas.  Por ejemplo, \- el enlace y \/BIND significan lo mismo.  
  
 EDITBIN tiene las siguientes opciones:  
  
|Opción|Objetivo|  
|------------|--------------|  
|[\/ALLOWBIND](../../build/reference/allowbind.md)|Especifica si el archivo DLL puede enlazarse.|  
|[\/ALLOWISOLATION](../../build/reference/allowisolation.md)|Especifica la DLL o comportamiento manifiesto de búsqueda del archivo ejecutable.|  
|[\/APPCONTAINER](../../build/reference/appcontainer.md)|Especifica si la aplicación se debe ejecutar dentro de AppContainer\- para el ejemplo, una aplicación de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] .|  
|[\/BIND](../../build/reference/bind.md)|Establece las direcciones para los puntos de entrada en los objetos especificados al tiempo de carga de velocidad.|  
|[\/DYNAMICBASE](../../build/reference/dynamicbase.md)|Especifica si el archivo DLL o la imagen ejecutable puede ser afirmativo aleatoriamente en el carga\- Tiempo mediante la distribución aleatoria \(ASLR\) de diseño del espacio de direcciones.|  
|[\/ERRORREPORT](../../build/reference/errorreport-editbin-exe.md)|Errores internos de los informes a Microsoft.|  
|[\/HEAP](../../build/reference/heap.md)|Establece el tamaño de la pila ejecutable de imagen en bytes.|  
|[\/HIGHENTROPYVA](../../build/reference/highentropyva.md)|Especifica si el archivo DLL o la imagen ejecutable admite la alta distribución aleatoria \(64 bits\) \(ASLR\) de diseño del espacio de direcciones de la entropía.|  
|[\/INTEGRITYCHECK](../../build/reference/integritycheck.md)|Especifica si comprobar la firma digital en tiempo de carga.|  
|[\/LARGEADDRESSAWARE](../../build/reference/largeaddressaware.md)|Especifica si el objeto admite instrucciones que son mayores de dos gigabytes.|  
|[\/NOLOGO](../../build/reference/nologo-editbin.md)|Suprime la pancarta de inicio de EDITBIN.|  
|[\/NXCOMPAT](../../build/reference/nxcompat.md)|Especifica si la imagen ejecutable es compatible con la Prevención de ejecución de datos de Windows.|  
|[\/REBASE](../../build/reference/rebase.md)|Establece las direcciones base para los objetos especificados.|  
|[\/RELEASE](../../build/reference/release.md)|Establece la suma de comprobación en el encabezado.|  
|[\/SECTION](../../build/reference/section-editbin.md)|Reemplaza los atributos de una sección.|  
|[\/STACK](../../build/reference/stack.md)|Establece el tamaño de la pila ejecutable de imagen en bytes.|  
|[\/SUBSYSTEM](../../build/reference/subsystem.md)|Especifica el entorno de ejecución.|  
|[\/SWAPRUN](../../build/reference/swaprun.md)|Especifica que la imagen ejecutable se debe copiar el archivo de intercambio, y después ejecutar desde allí.|  
|[\/TSAWARE](../../build/reference/tsaware.md)|Especifica que la aplicación está diseñada para ejecutarse en un entorno multiusuario.|  
|[\/VERSION](../../build/reference/version.md)|Establece el número de versión en el encabezado.|  
  
## Vea también  
 [Herramientas de compilación de C\/C\+\+](../../build/reference/c-cpp-build-tools.md)   
 [Referencia de EDITBIN](../../build/reference/editbin-reference.md)