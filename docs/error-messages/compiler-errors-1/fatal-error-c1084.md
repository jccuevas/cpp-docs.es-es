---
title: "Error irrecuperable C1084 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1084"
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se puede leer el archivo filetype: 'file': message  
  
 Este error suele deberse a un error en una llamada API del sistema interno realizada por el compilador.  El mensaje que se muestra cuando aparece este error suelen generarlo [\_wcserror\_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) o [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351.aspx).  
  
 Con los siguientes pasos, puede que resulte más fácil resolver C1084:  
  
-   Compruebe que el archivo especificado existe.  
  
-   Compruebe que están establecidos los permisos adecuados para acceder al archivo especificado.  
  
-   Compruebe que la sintaxis de línea de comandos cumple las reglas de [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md).  
  
-   Compruebe que las variables de entorno **TMP** y **TEMP**, y los permisos correspondientes para acceder a los directorios a los que hacen referencia estas variables de entorno, están establecidos correctamente.  Compruebe, también, que las unidades a las que hacen referencia las variables de entorno **TMP** y **TEMP** tienen una cantidad de espacio libre adecuada.  
  
-   Si en el mensaje se indica “número de archivo incorrecto”, puede que el archivo especificado se estuviera cerrando en primer plano mientras se compilaba en segundo plano.  
  
 Después de llevar a cabo los diagnósticos anteriores, realice una compilación limpia.