---
title: "Error PRJ0009 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0009"
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error PRJ0009 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede abrir el registro de compilación para su escritura.  
  
 **Compruebe que el archivo no está abierto en otro proceso y que no está protegido contra escritura.**  
  
 Después de establecer el valor de la propiedad **Registro de compilación** en **Sí** y compilar o recompilar, Visual C\+\+ no puede abrir el registro de compilación en modo exclusivo.  
  
 Inspeccione el valor de **Registro de compilación**; para ello, abra el cuadro de diálogo **Opciones** \(en el menú **Herramientas**, haga clic en el comando **Opciones**\) y, a continuación, seleccione **Compilación de VC\+\+** en la carpeta **Proyectos**.  El archivo de compilación se denomina BuildLog.htm y se escribe en el directorio intermedio $\(IntDir\).  
  
 Causas posibles de este error:  
  
-   Está ejecutando dos procesos de Visual C\+\+ e intenta compilar simultáneamente la misma configuración del mismo proyecto en los dos procesos.  
  
-   El archivo de registro de compilación se abre en un proceso que bloquea el archivo.  
  
-   El usuario no tiene permiso para crear un archivo.  
  
-   El usuario actual no tiene acceso de escritura al archivo BuildLog.htm.