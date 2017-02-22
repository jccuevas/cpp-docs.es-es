---
title: "pgosweep | Microsoft Docs"
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
  - "pgosweep (programa)"
  - "optimizaciones guiadas por perfiles, pgosweep"
ms.assetid: f39dd3b7-1cd9-4c3b-8e8b-fb794744b757
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# pgosweep
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se utiliza en la optimización guiada por perfiles para escribir todos los datos del perfil de un programa en ejecución en el archivo .pgc.  
  
## Sintaxis  
  
```  
pgosweep [options] image pgcfile  
```  
  
#### Parámetros  
 `options`  
 Se trata de un parámetro opcional que puede dejarse en blanco.  Éstos son los valores válidos para `options`:  
  
-   **\/?** o **\/help,** muestra el mensaje de ayuda.  
  
-   **\/noreset,**conserva el recuento en las estructuras de datos en tiempo de ejecución.  
  
 `image`  
 Ruta de acceso completa de un archivo .exe o .dll creado con la opción del compilador \/LTCG:PGINSTRUMENT.  
  
 `pgcfile`  
 Archivo .pgc donde este comando escribirá los recuentos de datos.  
  
## Comentarios  
 Este comando funciona en programas generados con la opción del compilador \/LTCG:PGINSTRUMENT.  Interrumpe un programa en ejecución y escribe los datos del perfil en un nuevo archivo .pgc.  De forma predeterminada, el comando restablece los recuentos después de cada operación de escritura.  Si se especifica la opción **\/noreset**, el comando grabará los valores, pero no los restablecerá en el programa en ejecución.  Con esta opción, obtendrá los datos duplicados si más adelante recupera los datos del perfil.  
  
 Un uso alternativo de `pgosweep` consiste en recuperar la información del perfil simplemente para el motor en tiempo de ejecución de la aplicación.  Por ejemplo, podría ejecutar `pgosweep` poco después de iniciar la aplicación y descartar ese archivo.  De este modo, se quitarían los datos del perfil asociados a los costos de inicio.  A continuación, puede ejecutar `pgosweep` antes de finalizar la aplicación.  Ahora, los datos recopilados sólo incluyen la información de perfil del motor en tiempo de ejecución.  
  
 Cuando se llama a un archivo .pgc \(`pgcfile`\) puede utilizar el formato estándar, que es *appname\!n*.pgc.  Si utiliza este formato, el compilador buscará estos datos en la fase \/LTCG:PGO.  Si no utiliza el formato estándar, deberá usar [pgomgr](../../build/reference/pgomgr.md) para combinar los archivos .pgc.  
  
## Ejemplo  
  
```  
pgosweep myapp.exe myapp!1.pgc  
```  
  
 En este ejemplo, `pgosweep` escribe la información del perfil actual para myapp.exe en myapp\!1.pgc.  
  
## Vea también  
 [Herramientas para la optimización basada en perfiles](../../build/reference/tools-for-manual-profile-guided-optimization.md)