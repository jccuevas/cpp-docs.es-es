---
title: "Error irrecuperable C1092 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1092"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1092"
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error irrecuperable C1092
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La función Editar y continuar no admite cambios en los tipos de datos; se requiere compilación  
  
 Se ha agregado o cambiado un tipo de datos desde la última compilación correcta.  
  
-   Editar y continuar no admite cambios en los tipos de datos existentes, incluidas las definiciones de clases, structs o enumeraciones.  Interrumpa la depuración y compile la aplicación.  
  
-   Editar y continuar no admitirá la adición de nuevos tipos de datos en caso de que haya una base de datos de programa, como vc*x*0.pdb \(donde *x* es la versión principal de Visual C\+\+ utilizada\), de sólo lectura.  Para agregar tipos de datos, el compilador deberá abrir el archivo .pdb en modo de escritura.  
  
### Para quitar este error sin terminar la sesión de depuración actual  
  
1.  Cambie el tipo de datos a su estado anterior al error.  
  
2.  En el menú **Depurar**, elija **Aplicar cambios en el código**.  
  
### Para quitar el error sin cambiar el código fuente  
  
1.  En el menú **Depurar**, elija **Detener depuración**.  
  
2.  En el menú **Compilar**, elija **Compilar**.  
  
 Para obtener información adicional, vea [Cambios admitidos en el código](../Topic/Supported%20Code%20Changes%20\(C++\).md).